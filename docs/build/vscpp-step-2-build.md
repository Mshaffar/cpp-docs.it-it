---
title: Compilare ed eseguire un progetto di app console C++
description: Compilare ed eseguire un'app console Hello World in Visual C++
ms.custom: mvc
ms.date: 04/20/2020
ms.topic: tutorial
ms.devlang: cpp
ms.assetid: 45138d71-719d-42dc-90d7-1d0ca31a2f55
ms.openlocfilehash: d1e92e598b370312730a7c4e208b935a264010bf
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81749249"
---
# <a name="build-and-run-a-c-console-app-project"></a>Compilare ed eseguire un progetto di app console C++

È stato creato un progetto di app console C++ e il codice è stato immesso. A questo punto è possibile compilare ed eseguire l'operazione in Visual Studio. Quindi, eseguirlo come app autonoma dalla riga di comando.

## <a name="prerequisites"></a>Prerequisiti

- Visual Studio con il carico di lavoro Sviluppo di applicazioni desktop con C++ deve essere installato e in esecuzione nel computer. Se non è ancora installato, seguire la procedura descritta in [installare il supporto di C++ in Visual Studio](vscpp-step-0-installation.md).

- Crea una "Hello, World!" progetto e immettere il codice sorgente. Se questo passaggio non è ancora stato fatto, seguire la procedura descritta in [creare un progetto di app console in C++](vscpp-step-1-create.md).

Se Visual Studio è simile a questo, è possibile creare ed eseguire l'app:

   ![Pronto per la compilazione del nuovo progetto](media/vscpp-ready-to-build.png "Pronto per la compilazione del nuovo progetto")

## <a name="build-and-run-your-code-in-visual-studio"></a>Compilare ed eseguire il codice in Visual Studio

1. Per compilare il progetto scegliere **Compila soluzione** dal menu **Compila**. Nella finestra **Output** vengono visualizzati i risultati del processo di compilazione.

   ![Compilare il progetto](media/vscpp-build-solution.gif "Compilare il progetto")

1. Per eseguire il codice, nella barra dei menu selezionare **Debug**, **Avvia senza eseguire debug**.

   ![Avviare il progetto](media/vscpp-start-without-debugging.gif "Avviare il progetto")

   Si apre una finestra della console si apre e quindi viene eseguita l'app. Quando viene avviata in Visual Studio, un'app console esegue il codice, quindi stampa "Premere un tasto per continuare. . ." per consentire di visualizzare l'output.

Congratulazioni! Si è creata la prima app console "Hello, World!" in Visual Studio. Premere un tasto per chiudere la finestra della console e tornare a Visual Studio.

[Si è verificato un problema.](#build-and-run-your-code-in-visual-studio-issues)

## <a name="run-your-code-in-a-command-window"></a>Eseguire il codice in una finestra di comando

In genere, le app console vengono eseguite al prompt dei comandi, non in Visual Studio. Una volta che l'app è stata compilata da Visual Studio, è possibile eseguirla da qualsiasi finestra di comando. Ecco come trovare ed eseguire la nuova app in una finestra del prompt dei comandi.

1. In **Esplora soluzioni**selezionare la soluzione HelloWorld (non il progetto HelloWorld) e fare clic con il pulsante destro del mouse per aprire il menu di scelta rapida. Scegliere **Apri cartella in Esplora file** per aprire una finestra **Esplora file** nella cartella della soluzione HelloWorld.

1. Nella finestra **Esplora file** aprire la cartella debug. Questa cartella contiene l'app, *HelloWorld. exe*e un paio di altri file di debug. Tenere premuto il tasto **MAIUSC** e fare clic con il pulsante destro del mouse su *HelloWorld. exe* per aprire il menu di scelta rapida. Scegliere **copia come percorso** per copiare il percorso dell'app negli Appunti.

1. Per aprire una finestra del prompt dei comandi, premere **Windows + R** per aprire la finestra di dialogo **Esegui** . Immettere *cmd. exe* nella casella di testo **Apri** , quindi scegliere **OK** per eseguire una finestra del prompt dei comandi.

1. Nella finestra del prompt dei comandi fare clic con il pulsante destro del mouse per incollare il percorso dell'app nel prompt dei comandi. Premere INVIO per eseguire l'app.

   ![Eseguire l'app al prompt dei comandi](media/vscpp-run-in-cmd.gif "Eseguire l'app al prompt dei comandi")

Congratulazioni, è stata creata ed eseguita un'app console in Visual Studio.

[Si è verificato un problema.](#run-your-code-in-a-command-window-issues)

## <a name="next-steps"></a>Passaggi successivi

Una volta compilata ed eseguita questa semplice app, si è pronti per progetti più complessi. Per ulteriori informazioni, vedere [utilizzo dell'IDE di Visual Studio per lo sviluppo di applicazioni desktop C++](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md). Sono disponibili procedure dettagliate più dettagliate per l'esplorazione delle funzionalità di Microsoft C++ in Visual Studio.

## <a name="troubleshooting-guide"></a>Guida per la risoluzione dei problemi

Ecco le soluzioni ai problemi comuni quando si crea il primo progetto C++.

### <a name="build-and-run-your-code-in-visual-studio-issues"></a>Compilare ed eseguire il codice in Visual Studio: problemi

Se la controllo ortografia durante rossa viene visualizzata sotto qualsiasi elemento nell'editor del codice sorgente, la compilazione potrebbe contenere errori o avvisi. Verificare che il codice corrisponda all'esempio in ortografia, punteggiatura e maiuscole/minuscole.

[Indietro.](#build-and-run-your-code-in-visual-studio)

### <a name="run-your-code-in-a-command-window-issues"></a>Eseguire il codice in una finestra di comando: problemi

Se il percorso visualizzato in Esplora file termina con * \\HelloWorld\\HelloWorld*, è stato aperto il *progetto* HelloWorld invece della *soluzione*HelloWorld. Ci si confonderà con una cartella di debug che non contiene l'app. Spostarsi verso l'alto di un livello in Esplora file per accedere alla cartella della soluzione, il primo *HelloWorld* nel percorso. Questa cartella contiene anche una cartella di debug e l'app è disponibile.

È anche possibile passare alla cartella di debug della soluzione dalla riga di comando per eseguire l'app. L'app non verrà eseguita da altre directory senza specificare il percorso dell'app. Tuttavia, è possibile copiare l'app in un'altra directory ed eseguirla da questa posizione. È anche possibile copiarla in una directory specificata dalla variabile di ambiente PATH, quindi eseguirla ovunque.

Se nel menu di scelta rapida non viene visualizzato **copia come percorso** , chiudere il menu e quindi tenere premuto il tasto **MAIUSC** mentre si apre di nuovo. Questo comando è sufficiente per praticità. È anche possibile copiare il percorso della cartella dalla barra di ricerca di Esplora file e incollarlo nella finestra di dialogo **Esegui** , quindi immettere il nome del file eseguibile alla fine. Si tratta solo di una digitazione più semplice, ma ha lo stesso risultato.

[Indietro.](#run-your-code-in-a-command-window)

<iframe src="" height="0" width="0" frameborder="0" name="frameTarget" />
