---
title: "C++ (C++ moderno) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 1cb1b849-ed9c-4721-a972-fd8f3dab42e2
caps.latest.revision: 23
caps.handback.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# C++ (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

C\+\+ è uno dei linguaggi di programmazione più ampiamente adottati nel mondo.  I programmi in C\+\+ ben scritti sono veloci ed efficienti.  Il linguaggio è più flessibile di altri linguaggi, in quanto è possibile utilizzarlo per creare un'ampia gamma di applicazioni: da giochi divertenti ed emozionanti, a software scientifico a elevate prestazioni, fino a driver di dispositivo, programmi incorporati e applicazioni client Windows.  Per più di 20 anni C\+\+ è stato utilizzato per risolvere problemi come questi e molti altri.  Molti non sanno che un numero sempre maggiore di programmatori in C\+\+ ha abbandonato la vecchia programmazione di tipo C per ripiegare sul moderno C\+\+.  
  
 Uno dei requisiti originali di C\+\+ era la compatibilità con le versioni precedenti del linguaggio C.  Da allora C\+\+ si è evoluto con diverse iterazioni, C con classi, quindi la specifica del linguaggio C\+\+ originale e poi numerosi miglioramenti successivi.  In ragione di questa eredità, C\+\+ è spesso definito un linguaggio di programmazione multi\-paradigma.  In C\+\+ è possibile effettuare la programmazione di tipo C completamente procedurale che include puntatori non elaborati, matrici, stringhe di caratteri con terminazione Null, strutture di dati personalizzati e altre funzionalità che consentono ottime prestazioni ma potrebbero generare bug e complessità.  Poiché la programmazione di tipo C presenta rischi simili, uno degli obiettivi basilari di C\+\+ consiste nel creare programmi che siano indipendenti dai tipi e che risultino più semplici da scrivere, estendere e gestire.  Nella fase iniziale C\+\+ comprendeva paradigmi di programmazione come la programmazione orientata a oggetti.  Nel corso degli anni sono state aggiunte delle funzionalità al linguaggio, insieme ad alcune librerie standard altamente testate di strutture di dati e algoritmi.  Queste aggiunte hanno reso possibile lo stile moderno del linguaggio C\+\+.  
  
 Il linguaggio C\+\+ moderno sottolinea:  
  
-   Ambito basato su stack anziché ambito globale statico o con heap.  
  
-   Inferenza di tipi automatica anziché dei nomi di tipo espliciti.  
  
-   Puntatori intelligenti anziché puntatori non elaborati.  
  
-   Tipi`std::string` e `std::wstring` \(vedere [\<string\>](../standard-library/string.md)\) anziché le matrici `char[]` non elaborate.  
  
-   Contenitori della [libreria di modelli standard](../standard-library/cpp-standard-library-header-files.md) \(STL\) come `vector`, `list` e `map` anziché contenitori personalizzati o matrici non elaborate.  Vedere [\<vector\>](../standard-library/vector.md), [\<list\>](../standard-library/list.md) e [\< map \>](../standard-library/map.md).  
  
-   [Algoritmi STL](../standard-library/algorithm.md) anziché quelli codificati manualmente.  
  
-   Eccezioni, per notificare e gestire le condizioni di errore.  
  
-   Comunicazione tra thread senza blocco utilizzando STL `std::atomic<>` \(vedere [\<atomic\>](../standard-library/atomic.md)\) anziché altri meccanismi di comunicazione tra thread.  
  
-   [Funzioni lambda](../cpp/lambda-expressions-in-cpp.md) inline anziché piccole funzioni implementate separatamente.  
  
-   Cicli for basati su intervallo per scrivere cicli più affidabili eseguibili con matrici, contenitori STL e raccolte di [!INCLUDE[wrt](../atl/reference/includes/wrt_md.md)] nel formato `for ( for-range-declaration : expression )`.  Tale impostazione fa parte del supporto del linguaggio di base.  Per altre informazioni, vedere [Istruzione for basata su intervallo \(C\+\+\)](../cpp/range-based-for-statement-cpp.md).  
  
 Lo stesso linguaggio C\+\+ si è evoluto.  Confrontare i due frammenti di codice seguenti.  Qui viene illustrato il funzionamento in C\+\+:  
  
```cpp  
  
// circle and shape are user-defined types  
circle* p = new circle( 42 );   
vector<shape*> v = load_shapes();  
  
for( vector<circle*>::iterator i = v.begin(); i != v.end(); ++i ) {  
    if( *i && **i == *p )  
        cout << **i << “ is a match\n”;  
}  
  
for( vector<circle*>::iterator i = v.begin();  
        i != v.end(); ++i ) {  
    delete *i; // not exception safe  
}  
  
delete p;  
  
```  
  
 Di seguito viene illustrato il modo in cui viene eseguita la stessa operazione nel linguaggio C\+\+ moderno:  
  
```cpp  
  
#include <memory>  
#include <vector>  
// ...  
// circle and shape are user-defined types  
auto p = make_shared<circle>( 42 );  
vector<shared_ptr<shape>> v = load_shapes();  
  
for_each( begin(v), end(v), [&](const shared_ptr<shape>& s) {  
    if( s && *s == *p )  
        cout << *s << " is a match\n";  
} );  
  
```  
  
 In C\+\+ moderno non è necessario utilizzare la gestione delle eccezioni esplicita o new\/delete, poiché è possibile usare puntatori intelligenti.  Quando si utilizza la deduzione del tipo `auto` e la [funzione lambda](../cpp/lambda-expressions-in-cpp.md), è possibile scrivere codice più rapidamente, renderlo più conciso e più comprensibile.  Inoltre `for_each` è meno complesso, facilmente utilizzabile e meno soggetto a errori non intenzionali rispetto a un ciclo `for`.  Per scrivere l'applicazione, è possibile usare i boilerplate insieme alle righe minime di codice.  È inoltre possibile rendere tale codice indipendente dalle eccezioni e dalla memoria, senza allocazione\/deallocazione o codici di errore da gestire.  
  
 Il linguaggio C\+\+ moderno comprende due tipi di polimorfismo: fase di compilazione, tramite i modelli e fase di esecuzione tramite l'ereditarietà e la virtualizzazione.  È possibile combinare i due tipi di polimorfismo per un grande effetto.  Il modello STL `shared_ptr` utilizza metodi virtuali interni per eseguire la cancellazione del tipo apparentemente senza problemi.  Evitare tuttavia di utilizzare in modo eccessivo la virtualizzazione per il polimorfismo quando un modello costituisce la scelta migliore.  I modelli possono essere molto efficaci.  
  
 Se si usa C\+\+ dopo aver utilizzato un altro linguaggio, specialmente da un linguaggio gestito in cui la maggior parte dei tipi è costituita da tipi di riferimento e pochi sono tipi di valore, è importante sapere che le classi C\+\+ sono tipi di valore per impostazione predefinita.  È tuttavia possibile specificarli come tipi di riferimento per abilitare il comportamento polimorfico che supporta la programmazione orientata a oggetti.  Osservazione utile: i tipi di valore hanno maggiormente effetto sulla memoria e sul controllo del layout, i tipi di riferimento invece sulle classi di base e sulle funzioni virtuali per il supporto del polimorfismo.  Per impostazione predefinita, i tipi di valore sono copiabili. Ciascuno include un costruttore di copia e un operatore di assegnazione della copia.  Quando si specifica un tipo di riferimento, impostare la classe come non copiabile \(disattivare il costruttore di copia e l'operatore di assegnazione di copia\) e utilizzare un distruttore virtuale, che supporta il polimorfismo.  I tipi di valore riguardano anche il contenuto, che, quando vengono copiati, forniscono due valori indipendenti che è possibile modificare separatamente.  I tipi di riferimento riguardano tuttavia l'identità, ossia di quale oggetto si tratta, per questo motivo sono talvolta denominati tipi polimorfici.  
  
 C\+\+ sta sperimentando una "rinascita" perché la potenza è nuovamente diventata l'elemento più importante.  I linguaggi come Java e C\# sono validi quando è importante la produttività del programmatore, ma mostrano le relative limitazioni quando sono importanti la potenza e le prestazioni.  Per una buona efficienza e potenza, specialmente sui dispositivi con hardware ridotto, niente è meglio del linguaggio C\+\+ moderno.  
  
 Anche gli strumenti di sviluppo, oltre al linguaggio, sono moderni.  [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] rende tutte le parti del ciclo di sviluppo affidabili ed efficienti.  Include strumenti di Gestione del ciclo di vita delle applicazioni \(ALM\), miglioramenti IDE quali IntelliSense, meccanismi adatti agli strumenti come XAML, la compilazione, il debug e molti altri strumenti.  
  
 Gli articoli in questa parte della documentazione forniscono linee guida e procedure consigliate approfondite per le principali funzionalità e tecniche di scrittura dei moderni programmi in C\+\+.  
  
-   [Supporto delle funzionalità C\+\+11\/14\/17](../cpp/support-for-cpp11-14-17-features-modern-cpp.md)  
  
-   [Sistema di tipi C\+\+](../cpp/cpp-type-system-modern-cpp.md)  
  
-   [Inizializzazione uniforme e costruttori deleganti](../cpp/uniform-initialization-and-delegating-constructors.md)  
  
-   [Durata degli oggetti e gestione delle risorse](../cpp/object-lifetime-and-resource-management-modern-cpp.md)  
  
-   [Risorse proprie degli oggetti \(RAII\)](../cpp/objects-own-resources-raii.md)  
  
-   [Puntatori intelligenti](../cpp/smart-pointers-modern-cpp.md)  
  
-   [Pimpl per incapsulamento in fase di compilazione](../cpp/pimpl-for-compile-time-encapsulation-modern-cpp.md)  
  
-   [Contenitori](../cpp/containers-modern-cpp.md)  
  
-   [Algoritmi](../cpp/algorithms-modern-cpp.md)  
  
-   [Formattazione di stringhe e I\/O](../cpp/string-and-i-o-formatting-modern-cpp.md)  
  
-   [Gestione di errori ed eccezioni](../cpp/errors-and-exception-handling-modern-cpp.md)  
  
-   [Portabilità in base ai limiti ABI](../cpp/portability-at-abi-boundaries-modern-cpp.md)  
  
 Per altre informazioni, vedere l'articolo su StackOverflow relativo alle [espressioni idiomatiche di C\+\+ deprecate in C\+\+11](http://go.microsoft.com/fwlink/?LinkId=402836)  
  
## Vedere anche  
 [Riferimenti del linguaggio C\+\+](../cpp/cpp-language-reference.md)   
 [Espressioni lambda](../cpp/lambda-expressions-in-cpp.md)   
 [Libreria standard C\+\+](../standard-library/cpp-standard-library-reference.md)