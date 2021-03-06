---
title: Esplorazione del file system
description: Come utilizzare le API del file system della libreria standard di C.
ms.date: 04/13/2020
ms.assetid: f7cc5f5e-a541-4e00-87c7-a3769ef6096d
ms.openlocfilehash: 412d865582a14da7b8c31d9f07a43106b0c49491
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368435"
---
# <a name="file-system-navigation"></a>Esplorazione del file system

L'intestazione \<filesystem> implementa la specifica tecnica del file system di ISO/IEC TS 18822:2015 di C++ (bozza finale [ISO/IEC JTC 1/SC 22/WG 21 N4100](https://wg21.link/n4100)) e contiene tipi e funzioni che consentono di scrivere codice indipendente dalla piattaforma per l'esplorazione del file system. Poiché è multipiattaforma, contiene API che non sono rilevanti per i sistemi Windows.Because it's cross-platform, it's contains APIs that aren't relevant for Windows systems. Ad esempio, restituisce sempre false in Windows.For example, `is_fifo(const path&)` always returns **false** on Windows.

## <a name="overview"></a>Panoramica

Usare le API \<filesystem> per le attività seguenti:

- eseguire l'iterazione su file e directory in un percorso specificato

- ottenere informazioni sui file inclusi data e ora di creazione, dimensioni, estensione e directory principale

- comporre, scomporre e confrontare percorsi

- creare, copiare ed eliminare directory

- copiare ed eliminare i file

Per altre informazioni sull'I/O file con la libreria standard, vedere la [Programmazione di iostream](../standard-library/iostream-programming.md).

## <a name="paths"></a>Percorsi

### <a name="constructing-and-composing-paths"></a>Costruzione e composizione di percorsi

I percorsi in Windows (a partire da XP) vengono archiviati in modo nativo in formato Unicode. La classe [path](../standard-library/path-class.md) esegue automaticamente tutte le conversioni di stringhe necessarie. Accetta argomenti di matrici di caratteri wide e `std::string` `std::wstring` narrow e sia i tipi formattati come UTF8 o UTF16. La classe `path` normalizza automaticamente anche i separatori del percorso. È possibile usare una singola barra come separatore di directory in argomenti del costruttore. Questo separatore consente di utilizzare le stesse stringhe per archiviare i percorsi in ambienti Windows e UNIX:

```cpp
path pathToDisplay(L"/FileSystemTest/SubDir3");     // OK!
path pathToDisplay2(L"\\FileSystemTest\\SubDir3");  // Still OK as always
path pathToDisplay3(LR"(\FileSystemTest\SubDir3)"); // Raw string literals are OK, too.
```

Per concatenare due percorsi, è possibile usare gli operatori `/` e `/=` in rapporto di overload, che sono analoghi agli operatori `+` e `+=` in `std::string` e `std::wstring`. L'oggetto `path` fornirà comodamente i separatori in caso contrario.

```cpp
path myRoot("C:/FileSystemTest");  // no trailing separator, no problem!
myRoot /= path("SubDirRoot");      // C:/FileSystemTest/SubDirRoot
```

### <a name="examining-paths"></a>Esame dei percorsi

La classe path dispone di diversi metodi che restituiscono informazioni sulle varie parti del percorso stesso. Queste informazioni sono distinte dalle informazioni sull'entità del file system a cui potrebbe fare riferimento. È possibile ottenere la radice, il percorso relativo, il nome del file, l'estensione del file e molto altro. È possibile eseguire l'iterazione su un oggetto path per esaminare tutte le cartelle nella gerarchia. Nell'esempio seguente viene illustrato come scorrere un oggetto percorso. E, come recuperare informazioni sulle sue parti.

```cpp
// filesystem_path_example.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <sstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

wstring DisplayPathInfo()
{
    // This path may or may not refer to an existing file. We are
    // examining this path string, not file system objects.
    path pathToDisplay(L"C:/FileSystemTest/SubDir3/SubDirLevel2/File2.txt ");

    wostringstream wos;
    int i = 0;
    wos << L"Displaying path info for: " << pathToDisplay << endl;
    for (path::iterator itr = pathToDisplay.begin(); itr != pathToDisplay.end(); ++itr)
    {
        wos << L"path part: " << i++ << L" = " << *itr << endl;
    }

    wos << L"root_name() = " << pathToDisplay.root_name() << endl
        << L"root_path() = " << pathToDisplay.root_path() << endl
        << L"relative_path() = " << pathToDisplay.relative_path() << endl
        << L"parent_path() = " << pathToDisplay.parent_path() << endl
        << L"filename() = " << pathToDisplay.filename() << endl
        << L"stem() = " << pathToDisplay.stem() << endl
        << L"extension() = " << pathToDisplay.extension() << endl;

    return wos.str();
}

int main()
{
    wcout << DisplayPathInfo() << endl;
    // wcout << ComparePaths() << endl; // see following example
    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

Il codice produce il seguente output:

```Output
Displaying path info for: C:\FileSystemTest\SubDir3\SubDirLevel2\File2.txt
path part: 0 = C:
path part: 1 = \
path part: 2 = FileSystemTest
path part: 3 = SubDir3
path part: 4 = SubDirLevel2
path part: 5 = File2.txt
root_name() = C:
root_path() = C:\
relative_path() = FileSystemTest\SubDir3\SubDirLevel2\File2.txt
parent_path() = C:\FileSystemTest\SubDir3\SubDirLevel2
filename() = File2.txt
stem() = File2
extension() = .txt
```

### <a name="comparing-paths"></a>Confronto tra percorsi

La classe `path` è in rapporto di overload con gli stessi operatori di confronto di `std::string` e `std::wstring`. Quando si confrontano due percorsi, si esegue un confronto tra stringhe dopo che i separatori sono stati normalizzati. Se manca una barra finale (o barra rovesciata), non viene aggiunta e ciò influisce sul confronto. L'esempio seguente dimostra come confrontare i valori di percorso:

```cpp
wstring ComparePaths()
{
    path p0(L"C:/Documents");                 // no trailing separator
    path p1(L"C:/Documents/");                // p0 < p1
    path p2(L"C:/Documents/2013/");           // p1 < p2
    path p3(L"C:/Documents/2013/Reports/");   // p2 < p3
    path p4(L"C:/Documents/2014/");           // p3 < p4
    path p5(L"D:/Documents/2013/Reports/");   // p4 < p5

    wostringstream wos;
    wos << boolalpha <<
        p0.wstring() << L" < " << p1.wstring() << L": " << (p0 < p1) << endl <<
        p1.wstring() << L" < " << p2.wstring() << L": " << (p1 < p2) << endl <<
        p2.wstring() << L" < " << p3.wstring() << L": " << (p2 < p3) << endl <<
        p3.wstring() << L" < " << p4.wstring() << L": " << (p3 < p4) << endl <<
        p4.wstring() << L" < " << p5.wstring() << L": " << (p4 < p5) << endl;
    return wos.str();
}
```

```Output
C:\Documents < C:\Documents\: true
C:\Documents\ < C:\Documents\2013\: true
C:\Documents\2013\ < C:\Documents\2013\Reports\: true
C:\Documents\2013\Reports\ < C:\Documents\2014\: true
C:\Documents\2014\ < D:\Documents\2013\Reports\: true
```

Per eseguire questo codice, incollarlo nell'esempio completo sopra prima di `main` e rimuovere il commento dalla riga che chiama tale codice.

### <a name="converting-between-path-and-string-types"></a>Conversione tra tipi di stringa e percorso

Un oggetto `path` è convertibile in modo implicito in un oggetto `std::wstring` o `std::string`. Ciò significa che è possibile passare un percorso a funzioni quali [wofstream::open](../standard-library/basic-ofstream-class.md#open), come illustrato nell'esempio seguente:

```cpp
// filesystem_path_conversion.cpp
// compile by using: /EHsc /W4 /permissive- /std:c++17 (or /std:c++latest)
#include <string>
#include <iostream>
#include <fstream>
#include <filesystem>

using namespace std;
using namespace std::filesystem;

int main()
{
    const wchar_t* p{ L"C:/Users/Public/Documents" };
    path filePath(p);

    filePath /= L"NewFile.txt";

    // Open, write to, and close the file.
    wofstream writeFile(filePath, ios::out);  // implicit conversion
    writeFile << L"Lorem ipsum\nDolor sit amet";
    writeFile.close();

    // Open, read, and close the file.
    wifstream readFile;
    wstring line;
    readFile.open(filePath);  // implicit conversions
    wcout << L"File " << filePath << L" contains:" << endl;
    while (readFile.good())
    {
        getline(readFile, line);
        wcout << line << endl;
    }
    readFile.close();

    wcout << endl << L"Press Enter to exit" << endl;
    wstring input;
    getline(wcin, input);
}
```

```Output
File C:\Users\Public\Documents\NewFile.txt contains:
Lorem ipsum
Dolor sit amet

Press Enter to exit
```

## <a name="iterating-directories-and-files"></a>Iterazione di directory e file

L'intestazione \<filesystem> specifica il tipo [directory_iterator](../standard-library/directory-iterator-class.md) per eseguire l'iterazione sulle singole directory e la classe [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) per eseguire l'iterazione in modo ricorsivo su una directory e le relative sottodirectory. Dopo aver creato un iteratore passandovi un oggetto `path` , l'iteratore punta al primo oggetto directory_entry nel percorso. Creare l'iteratore finale chiamando il costruttore predefinito.

Quando si scorre una directory, ci sono diversi tipi di elementi che si potrebbero scoprire. Questi elementi includono directory, file, collegamenti simbolici, file socket e altri. `directory_iterator` restituisce gli elementi come oggetti [directory_entry](../standard-library/directory-entry-class.md).
