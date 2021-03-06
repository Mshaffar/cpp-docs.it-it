---
title: Gestione di eventi in C++ nativo
ms.date: 05/07/2019
helpviewer_keywords:
- event handling [C++]
ms.assetid: e4b9219a-15d8-42fb-83c8-6d2e4e087c8d
ms.openlocfilehash: cc9265cd3f9f400e2880405019e4d2c9a934f10a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180082"
---
# <a name="event-handling-in-native-c"></a>Gestione di eventi in C++ nativo

Nella gestione C++ degli eventi nativi è possibile configurare un'origine evento e un ricevitore di eventi utilizzando rispettivamente gli attributi [event_source](../windows/attributes/event-source.md) e [event_receiver](../windows/attributes/event-receiver.md) , specificando `type`=`native`. Questi attributi consentono alle classi, a cui sono applicati, di generare eventi e gestire eventi in un contesto nativo, non COM.

## <a name="declaring-events"></a>Dichiarazione di eventi

In una classe di origine evento, usare la parola chiave [__event](../cpp/event.md) in una dichiarazione di metodo per dichiarare il metodo come un evento. Assicurarsi di dichiarare il metodo, ma non di definirlo; così facendo verrà generato un errore del compilatore, poiché il compilatore definisce il metodo in modo implicito quando viene trasformato in un evento. Gli eventi nativi possono essere metodi con zero o più parametri. Il tipo restituito può essere void o qualsiasi tipo integrale.

## <a name="defining-event-handlers"></a>Definizione di gestori degli eventi

In una classe del ricevitore di eventi, è possibile definire i gestori eventi, ovvero i metodi con firme (tipi restituiti, convenzioni di chiamata e argomenti) che corrispondono all'evento che gestiranno.

## <a name="hooking-event-handlers-to-events"></a>Hook dei gestori eventi agli eventi

In una classe di ricevitori di eventi, inoltre, si utilizza la funzione intrinseca [__hook](../cpp/hook.md) per associare gli eventi ai gestori eventi e [__unhook](../cpp/unhook.md) per annullare l'associazione degli eventi dai gestori eventi. È possibile eseguire l'hook di più eventi a un singolo gestore eventi o di diversi gestori eventi a un singolo evento.

## <a name="firing-events"></a>Generazione di eventi

Per generare un evento, è sufficiente chiamare il metodo dichiarato come un evento nella classe di origine dell'evento. Se per l'evento è stato eseguito l'hook ai gestori, questi verranno chiamati.

### <a name="native-c-event-code"></a>Il codice evento in C++ nativo

Nell'esempio seguente viene illustrato come gestire un'evento in C++ nativo. Per compilare ed eseguire l'esempio, fare riferimento ai commenti presenti nel codice.

## <a name="example"></a>Esempio

### <a name="code"></a>Codice

```cpp
// evh_native.cpp
#include <stdio.h>

[event_source(native)]
class CSource {
public:
   __event void MyEvent(int nValue);
};

[event_receiver(native)]
class CReceiver {
public:
   void MyHandler1(int nValue) {
      printf_s("MyHandler1 was called with value %d.\n", nValue);
   }

   void MyHandler2(int nValue) {
      printf_s("MyHandler2 was called with value %d.\n", nValue);
   }

   void hookEvent(CSource* pSource) {
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __hook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }

   void unhookEvent(CSource* pSource) {
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler1);
      __unhook(&CSource::MyEvent, pSource, &CReceiver::MyHandler2);
   }
};

int main() {
   CSource source;
   CReceiver receiver;

   receiver.hookEvent(&source);
   __raise source.MyEvent(123);
   receiver.unhookEvent(&source);
}
```

### <a name="output"></a>Output

```Output
MyHandler2 was called with value 123.
MyHandler1 was called with value 123.
```

## <a name="see-also"></a>Vedere anche

[Gestione di eventi](../cpp/event-handling.md)
