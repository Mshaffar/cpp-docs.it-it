---
title: Hosting di un controllo utente Windows Form come finestra di dialogo MFC
ms.date: 11/04/2016
helpviewer_keywords:
- MFC [C++], Windows Forms support
- Windows Forms [C++], hosting as MFC Dialog
- hosting Windows Forms control [C++]
ms.assetid: 0434a9d7-8b14-48e6-ad69-9ba9a684677a
ms.openlocfilehash: 7fc2aad1e0a550fb8f22b311518ae9fb16c076a5
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/12/2019
ms.locfileid: "73964945"
---
# <a name="hosting-a-windows-form-user-control-as-an-mfc-dialog-box"></a>Hosting di un controllo utente Windows Form come finestra di dialogo MFC

MFC fornisce la classe modello [CWinFormsDialog](../mfc/reference/cwinformsdialog-class.md) in modo che sia possibile ospitare un controllo utente Windows Forms (<xref:System.Windows.Forms.UserControl>) in una finestra di dialogo MFC modale o non modale. `CWinFormsDialog` deriva dalla classe MFC [CDialog](../mfc/reference/cdialog-class.md), quindi la finestra di dialogo può essere avviata come modale o non modale.

Il processo che `CWinFormsDialog` utilizza per ospitare il controllo utente è simile a quello descritto in [hosting di un controllo utente Windows Form in una finestra di dialogo MFC](../dotnet/hosting-a-windows-form-user-control-in-an-mfc-dialog-box.md). Tuttavia, `CWinFormsDialog` gestisce l'inizializzazione e l'hosting del controllo utente in modo che non debba essere programmato manualmente.

Per un'applicazione di esempio che Mostra Windows Forms utilizzata con MFC, vedere [MFC and Windows Forms Integration](https://www.microsoft.com/download/details.aspx?id=2113).

### <a name="to-create-the-mfc-host-application"></a>Per creare l'applicazione host MFC

1. Creare un progetto di applicazione MFC.

   Scegliere **nuovo**dal menu **file** , quindi fare clic su **progetto**. Nella cartella **visuale C++**  Selezionare **applicazione MFC**.

   Nella casella **nome** immettere `MFC03` e modificare l'impostazione della soluzione in **Aggiungi a soluzione**. Fare clic su **OK**.

   Nella **creazione guidata applicazione MFC**accettare tutte le impostazioni predefinite, quindi fare clic su **fine**. In questo modo viene creata un'applicazione MFC con un'interfaccia a documenti multipli.

1. Configurare il progetto.

   In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto **MFC03** e scegliere **proprietà**. Verrà visualizzata la finestra di dialogo **pagine delle proprietà** .

   Nel controllo albero **proprietà di configurazione** della finestra di dialogo **pagine delle proprietà** selezionare **generale**, quindi nella sezione **impostazioni predefinite progetto** impostare **supporto Common Language Runtime** su **supporto Common Language Runtime (/CLR)** . fare clic su **OK**.

1. Aggiungere un riferimento al controllo .NET.

   In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto **MFC03** e scegliere **Aggiungi**, **riferimenti**. Nella **pagina delle proprietà**fare clic su **Aggiungi nuovo riferimento**, selezionare WindowsControlLibrary1 (nella scheda **progetti** ) e fare clic su **OK**. Viene aggiunto un riferimento sotto forma di opzione del compilatore [/fu](../build/reference/fu-name-forced-hash-using-file.md) in modo che il programma venga compilato. copia inoltre WindowsControlLibrary1. dll nella directory del progetto `MFC03` in modo che il programma venga eseguito.

1. Aggiungere `#include <afxwinforms.h>` a *PCH. h* (*stdafx. h* in Visual Studio 2017 e versioni precedenti), alla fine delle istruzioni di `#include` esistenti.

1. Aggiungere una nuova classe che sottoclassi `CDialog`.

   Fare clic con il pulsante destro del mouse sul nome del progetto e aggiungere una classe MFC (denominata CHostForWinForm) che sottoclassi `CDialog`. Poiché la risorsa della finestra di dialogo non è necessaria, è possibile eliminare l'ID risorsa (selezionare **visualizzazione risorse**, espandere la cartella della **finestra di dialogo** ed eliminare `IDD_HOSTFORWINFORM` risorsa.  Rimuovere quindi tutti i riferimenti all'ID nel codice.

1. Sostituire `CDialog` nei file CHostForWinForm. h e CHostForWinForm. cpp con `CWinFormsDialog<WindowsControlLibrary1::UserControl1>`.

1. Chiamare DoModal sulla classe CHostForWinForm.

   In MFC03. cpp aggiungere `#include "HostForWinForm.h"`.

   Prima dell'istruzione return nella definizione di CMFC03App:: InitInstance, aggiungere:

    ```cpp
    CHostForWinForm m_HostForWinForm;
    m_HostForWinForm.DoModal();
    ```

1. Compilare ed eseguire il progetto.

   Scegliere **Compila soluzione** dal menu **Compila**.

   Scegliere **Avvia senza eseguire debug**dal menu **debug** .

   Successivamente, verrà aggiunto il codice per monitorare lo stato di un controllo nel Windows Forms dall'applicazione MFC.

1. Aggiungere un gestore per OnInitDialog.

   Visualizzare la finestra **Proprietà** (F4). In **Visualizzazione classi**selezionare CHostForWinForm. Nella finestra **Proprietà** selezionare sostituzioni e nella riga per OnInitDialog, fare clic nella colonna a sinistra e selezionare \< Aggiungi >. In questo modo viene aggiunta la riga seguente a CHostForWinForm. h:

    ```cpp
    virtual BOOL OnInitDialog();
    ```

1. Definire OnInitDialog (in CHostForWinForm. cpp) come indicato di seguito:

    ```cpp
    BOOL CHostForWinForm::OnInitDialog() {
       CWinFormsDialog<WindowsControlLibrary1::UserControl1>::OnInitDialog();
       GetControl()->button1->Click += MAKE_DELEGATE(System::EventHandler, OnButton1);
       return TRUE;
    }
    ```

1. Aggiungere quindi il gestore OnButton1. Aggiungere le righe seguenti alla sezione public della classe CHostForWinForm in CHostForWinForm. h:

    ```cpp
    virtual void OnButton1( System::Object^ sender, System::EventArgs^ e );

    BEGIN_DELEGATE_MAP( CHostForWinForm )
       EVENT_DELEGATE_ENTRY( OnButton1, System::Object^, System::EventArgs^ );
    END_DELEGATE_MAP()
    ```

   In CHostForWinForm. cpp aggiungere questa definizione:

    ```cpp
    void CHostForWinForm::OnButton1( System::Object^ sender, System::EventArgs^ e )
    {
       System::Windows::Forms::MessageBox::Show("test");
    }
    ```

1. Compilare ed eseguire il progetto. Quando si fa clic sul pulsante, che è in Windows Form, verrà eseguito il codice nell'applicazione MFC.

    Successivamente, verrà aggiunto il codice per visualizzare dal codice MFC il valore nella casella di testo del Windows Form.

1. Nella sezione public della classe CHostForWinForm in CHostForWinForm. h aggiungere la dichiarazione seguente:

    ```cpp
    CString m_sEditBoxOnWinForm;
    ```

1. Nella definizione di DoDataExchange in CHostForWinForm. cpp, aggiungere le tre righe seguenti alla fine della funzione:

    ```cpp
    if (pDX->m_bSaveAndValidate)
       m_sEditBoxOnWinForm = CString( GetControl()->textBox1->Text);
    else
       GetControl()->textBox1->Text = gcnew System::String(m_sEditBoxOnWinForm);
    ```

1. Nella definizione di OnButton1 in CHostForWinForm. cpp, aggiungere le tre righe seguenti alla fine della funzione:

    ```cpp
    this->UpdateData(TRUE);
    System::String ^ z = gcnew System::String(m_sEditBoxOnWinForm);
    System::Windows::Forms::MessageBox::Show(z);
    ```

1. Compilare ed eseguire il progetto.

## <a name="see-also"></a>Vedere anche

<xref:System.Windows.Forms.UserControl?displayProperty=fullName>
[utilizzando un controllo utente Windows Form in MFC](../dotnet/using-a-windows-form-user-control-in-mfc.md)
