---
title: Inserimento del controllo in una pagina Web (Esercitazione di ATL, parte 7)
ms.custom: get-started-article
ms.date: 05/06/2019
ms.assetid: 50dc4c95-c95b-4006-b88a-9826f7bdb222
ms.openlocfilehash: db6dcc57ff9f3748d802e76617ef18dea8f9506c
ms.sourcegitcommit: 6cf0c67acce633b07ff31b56cebd5de3218fd733
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/24/2019
ms.locfileid: "67344348"
---
# <a name="putting-the-control-on-a-web-page-atl-tutorial-part-7"></a>Inserimento del controllo in una pagina Web (Esercitazione di ATL, parte 7)

Il controllo è stato completato. Per visualizzare il controllo funziona in una situazione reale, inserirlo in una pagina Web. Un file HTML che contiene il controllo è stato creato quando è stato definito il controllo. Aprire il file PolyCtl. htm **Esplora soluzioni**, ed è possibile visualizzare il controllo in una pagina Web.

In questo passaggio si aggiungono funzionalità al controllo e la pagina Web per rispondere a eventi di script. Si modificherà anche il controllo per Internet Explorer di informare che il controllo è sicuro per lo scripting.

## <a name="adding-new-functionality"></a>Aggiunta di nuove funzionalità

### <a name="to-add-control-features"></a>Per aggiungere funzionalità di controllo

1. Aprire PolyCtl e sostituire il codice seguente:

    ```cpp
    if (PtInRegion(hRgn, xPos, yPos))
        Fire_ClickIn(xPos, yPos);
    else
        Fire_ClickOut(xPos, yPos);
    ```

    con

    ```cpp
    short temp = m_nSides;
    if (PtInRegion(hRgn, xPos, yPos))
    {
        Fire_ClickIn(xPos, yPos);
        put_Sides(++temp);
    }
    else
    {
        Fire_ClickOut(xPos, yPos);
        put_Sides(--temp);
    }
    ```

La forma verrà a questo punto aggiungere o rimuovere i lati in base alla quale si fa clic su.

## <a name="scripting-the-web-page"></a>Scripting della pagina Web

Il controllo non esegue ancora alcuna operazione, quindi modificare la pagina Web per rispondere agli eventi inviati.

### <a name="to-script-the-web-page"></a>Eseguire lo script della pagina Web

1. Aprire PolyCtl. htm e selezionare la visualizzazione HTML. Aggiungere le righe seguenti al codice HTML. Devono essere aggiunte dopo `</OBJECT>` ma prima `</BODY>`.

    ```html
    <SCRIPT LANGUAGE="VBScript">
    <!--
        Sub PolyCtl_ClickIn(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - adding side")
        End Sub
        Sub PolyCtl_ClickOut(x, y)
            MsgBox("Clicked (" & x & ", " & y & ") - removing side")
        End Sub
    -->
    </SCRIPT>
    ```

1. Salvare il file HTM.

È stato aggiunto codice VBScript che ottiene la proprietà Sides dal controllo. Il numero di lati aumenta di uno se si fa clic all'interno del controllo. Se si fa clic all'esterno del controllo, è ridurre il numero di lati da uno.

## <a name="indicating-that-the-control-is-safe-for-scripting"></a>Che indica che il controllo è sicuro per lo Scripting

È possibile visualizzare la pagina Web con il controllo solo in Internet Explorer. Altri browser non supporta più i controlli ActiveX a causa di problemi di sicurezza.

> [!NOTE]
> Se il controllo non è visibile, significa che alcuni browser richiedono modifiche delle impostazioni per eseguire i controlli ActiveX. Consultare la documentazione del browser su come abilitare i controlli ActiveX.

In base alle impostazioni di sicurezza correnti di Internet Explorer, si potrebbe ricevere una finestra di dialogo Avviso di sicurezza. Afferma che il controllo potrebbe non essere sicuro eseguire lo script e potrebbe potenzialmente provocare danni. Ad esempio, se si disponeva di un controllo visualizzato un file, ma presenta anche un `Delete` metodo eliminato un file, potrebbe essere sicuro visualizzarlo in una pagina. Potrebbe non essere sicuro eseguire lo script, tuttavia, poiché qualcuno potrebbe chiamare il `Delete` (metodo).

> [!IMPORTANT]
> Per questa esercitazione, è possibile modificare le impostazioni di sicurezza in Internet Explorer per eseguire i controlli ActiveX non contrassegnati come sicuri. Nel Pannello di controllo, fare clic su **proprietà Internet** e fare clic su **sicurezza** per modificare le impostazioni appropriate. Dopo aver completato l'esercitazione, è possibile modificare le impostazioni di sicurezza nello stato originale.

È possibile avvisare a livello di programmazione Internet Explorer che non è necessario visualizzare la finestra di dialogo Avviso di sicurezza per questo controllo specifico. È possibile farlo usando il `IObjectSafety` interfaccia. ATL fornisce un'implementazione di questa interfaccia nella classe [IObjectSafetyImpl](../atl/reference/iobjectsafetyimpl-class.md). Per aggiungere l'interfaccia al controllo, aggiungere `IObjectSafetyImpl` al proprio elenco di classi ereditate e aggiungere una voce per tale nella mappa COM.

### <a name="to-add-iobjectsafetyimpl-to-the-control"></a>Per aggiungere IObjectSafetyImpl al controllo

1. Aggiungere la riga seguente alla fine dell'elenco di classi ereditate in PolyCtl. H e aggiungere una virgola alla riga precedente:

    [!code-cpp[NVC_ATL_Windowing#62](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_1.h)]

1. Aggiungere la riga seguente alla mappa COM in PolyCtl. H:

    [!code-cpp[NVC_ATL_Windowing#63](../atl/codesnippet/cpp/putting-the-control-on-a-web-page-atl-tutorial-part-7_2.h)]

## <a name="building-and-testing-the-control"></a>Compilazione e test del controllo

Compilare il controllo. Al termine della compilazione, aprire PolyCtl. htm nella visualizzazione esplorazione nuovamente. Questa volta, la pagina Web deve essere visualizzata direttamente senza la **avviso di sicurezza** nella finestra di dialogo. Se si fa clic all'interno del poligono, il numero di lati aumenta di uno. Fare clic all'esterno del poligono per ridurre il numero di lati.

[Torna al passaggio 6](../atl/adding-a-property-page-atl-tutorial-part-6.md)

## <a name="next-steps"></a>Passaggi successivi

Questo passaggio conclude l'esercitazione ATL. Per collegamenti a ulteriori informazioni su ATL, vedere la [pagina iniziale di ATL](../atl/active-template-library-atl-concepts.md).

## <a name="see-also"></a>Vedere anche

[Esercitazione](../atl/active-template-library-atl-tutorial.md)
