---
title: Leggere e comprendere il codice C++ in Visual Studio
description: Usare l'editor di codice C++ in Visual Studio per formattare e comprendere il codice.
ms.date: 05/28/2019
ms.openlocfilehash: 9ed0a20fb73e4cc976392bc5e5f698f9658a0b48
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377297"
---
# <a name="read-and-understand-c-code-in-visual-studio"></a>Leggere e comprendere il codice C++ in Visual Studio

L'editor di codice C++ e l'IDE di Visual Studio includono numerosi strumenti per la scrittura di codice. Alcuni sono specifici di C++ e altri sono sostanzialmente uguali per tutti i linguaggi di Visual Studio. Per altre informazioni sulle funzionalità condivise, vedere [Scrittura di codice nell'editor di testo e di codice](/visualstudio/ide/writing-code-in-the-code-and-text-editor).  

## <a name="colorization"></a>Colorazione

Visual Studio colora gli elementi della sintassi per distinguere tra loro i tipi di simboli, ad esempio parole chiave del linguaggio, nomi di tipi, nomi di variabili, parametri di funzione, valori letterali stringa e così via.

![Applicazione di colori al codice](../ide/media/code-outline-colorization.png "Colorazione di C")

Il codice non usato, ad esempio il codice sotto un #if 0, ha un colore più sbiadito.

![Codice inattivo](../ide/media/inactive-code-cpp.png "Codice inattivo di C")

È possibile personalizzare i colori digitando "Tipi di carattere" in **Avvio veloce** e quindi scegliendo **Tipi di carattere e colori**. Nella finestra di dialogo **Tipi di carattere e colori** scorrere verso il basso fino alle opzioni di C/C++, quindi scegliere un tipo di carattere e/o un colore personalizzato.

## <a name="outlining"></a>struttura

Fare clic con il pulsante destro del mouse in un punto qualsiasi di un file del codice sorgente e scegliere **Struttura** per comprimere o espandere i blocchi di codice e/o le aree personalizzate e individuare più facilmente solo il codice che interessa. Per altre informazioni, vedere [Struttura](/visualstudio/ide/outlining).

![Struttura&#43;&#43; C](../ide/media/vs2015_cpp_outlining.png "struttura")

Quando si posiziona il cursore davanti a una parentesi graffa, '{' o '}', l'editor evidenzia la controparte corrispondente.

Altre opzioni di struttura si trovano in **Modifica** > **struttura** nel menu principale.

## <a name="line-numbers"></a>Numeri di riga

È possibile aggiungere numeri di riga al progetto accedendo a**Opzioni** >  **di Strumenti** > **Editor** > di testo**Tutti i linguaggi** > **Generali** o cercando "riga num" con **Avvio veloce (CTRL e Q)**. I numeri riga possono essere impostati per tutti i linguaggi o solo per determinati linguaggi, tra cui C++.

## <a name="scroll-and-zoom"></a>Scorrimento e zoom

È possibile fare zoom avanti o indietro nell'editor premendo il tasto **CTRL** e scorrere usando la rotellina del mouse. Nell'angolo inferiore sinistro è disponibile anche l'impostazione dello zoom.

![C controllo zoom&#43;&#43; ](../ide/media/zoom-control.png "Controllo zoom")

La **modalità mappa** della barra di scorrimento consente di scorrere rapidamente ed esplorare un file di codice senza abbandonare la posizione attuale. Fare clic in un punto qualsiasi della mappa del codice per passare direttamente a tale posizione.

![Mappa del codice nel&#43;&#43;CCode Map in C&#43;&#43;](../ide/media/vs2015-cpp-code-map.png "Mappa codice")

Per attivare la **modalità Mappa,** digitare "mappa" nella casella di ricerca **Avvio veloce** della barra degli strumenti principale e scegliere **Usa modalità mappa**di scorrimento . Per altre informazioni, vedere [Procedura: Tenere traccia del codice personalizzando la barra di scorrimento](/visualstudio/ide/how-to-track-your-code-by-customizing-the-scrollbar).

Quando la **modalità mappa** è disattivata, la barra di scorrimento evidenzia comunque le modifiche apportate al file. Verde indica le modifiche salvate e giallo le modifiche non salvate.

## <a name="quick-info-and-parameter-info"></a>Informazioni rapide e Informazioni sul parametro

Passare il mouse su una qualsiasi variabile, funzione o su un altro simbolo per ottenere informazioni al suo riguardo, tra cui la dichiarazione e i commenti che si trovano appena prima.

::: moniker range="vs-2019"

![Informazioni rapide in C&#43;&#43;](../ide/media/quick-info-vs2019.png "Informazioni rapide")

La descrizione comando **Informazioni rapide** ha un collegamento **Ricerca in linea**. Andare a**Opzioni di** >  **opzioni** > **C++** > **Editor** > di testo**Di E** così via per specificare il provider di ricerca.

Se il codice contiene un errore, passare il puntatore su di esso per visualizzare il messaggio di errore in **Informazioni rapide**. Il messaggio di errore viene visualizzato anche nella finestra Elenco errori.

![Informazioni rapide in caso di errore](../ide/media/quickinfo-on-error.png "Informazioni rapide in caso di errore")

::: moniker-end

::: moniker range="<=vs-2017"

![Informazioni rapide in C&#43;&#43;](../ide/media/quick-info.png "Informazioni rapide")

Se il codice contiene un errore, passare il puntatore su di esso per visualizzare il messaggio di errore in **Informazioni rapide**. Il messaggio di errore viene visualizzato anche nella finestra **Elenco errori**.

![Informazioni rapide in caso di errore](../ide/media/quickinfo-on-error.png "Informazioni rapide in caso di errore")

::: moniker-end

Quando si chiama una funzione, in **Informazioni sul parametro** vengono mostrati i tipi di parametri e l'ordine in cui sono previsti.

![Informazioni sui parametri in C&#43;&#43;](../ide/media/parameter-info.png "Informazioni sul parametro")

## <a name="peek-definition"></a>Visualizza definizione

Passare il mouse su una dichiarazione di variabile o di funzione, fare clic con il pulsante destro del mouse e scegliere **Visualizza definizione** per accedere a una visualizzazione inline della relativa definizione senza allontanarsi dalla posizione attuale. Per altre informazioni, vedere [Visualizza definizione (ALT+F12)](/visualstudio/ide/how-to-view-and-edit-code-by-using-peek-definition-alt-plus-f12).

![C definizione di anteprima&#43;&#43; ](../ide/media/vs2015_cpp_peek_definition.png "vs2015_cpp_peek_definition")

## <a name="f1-help"></a>Guida sensibile al contesto

Posizionare il cursore su o subito dopo qualsiasi tipo, parola chiave o funzione e premere **F1** per passare direttamente all'argomento di riferimento pertinente su docs.microsoft.com. **F1** funziona anche sugli elementi nell'elenco degli errori e in molte finestre di dialogo.

## <a name="class-view"></a>Visualizzazione classi

**Visualizzazione classi** visualizza una serie di strutture ad albero disponibili per la ricerca di tutti i simboli di codice, del relativo ambito e delle gerarchie padre/figlio organizzate in base al progetto. Configurare che cosa visualizzare nella **Visualizzazione classi** con **Visualizzazione classi - impostazioni** facendo clic sull'icona della casella a forma di ingranaggio nella parte superiore della finestra.

![Visualizzazione classi in C&#43;&#43;](../ide/media/class-view.png "Visualizzazione classi")

## <a name="generate-graph-of-include-files"></a>Genera grafico dei file di inclusione

Fare clic con il pulsante destro del mouse su un file del codice del progetto e scegliere **Genera grafico dei file di inclusione** per visualizzare un grafico dei file inclusi da altri file.

![C&#43;&#43; grafico dei file di inclusione](../ide/media/vs2015_cpp_include_graph.png "vs2015_cpp_include_graph")

## <a name="view-call-hierarchy"></a>Visualizza gerarchia delle chiamate

Fare clic con il pulsante destro del mouse su una qualsiasi chiamata di funzione per visualizzare un elenco ricorsivo di tutte le funzioni chiamate e di tutte le funzioni che la chiamano. È possibile espandere nello stesso modo tutte le singole funzioni dell'elenco. Per altre informazioni, vedere [Gerarchia delle chiamate](/visualstudio/ide/reference/call-hierarchy).

![C&#43;&#43; gerarchia di chiamata](../ide/media/vs2015_cpp_call_hierarchy.png "vs2015_cpp_call_hierarchy")

## <a name="see-also"></a>Vedere anche

[Scrittura e refactoring del codice (C++)](writing-and-refactoring-code-cpp.md)</br>
[Spostarsi all'interno del codice C++ in Visual Studio](navigate-code-cpp.md)</br>
[Collaborare con Live Share per C++](live-share-cpp.md)
