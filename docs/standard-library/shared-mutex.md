---
title: '&lt;shared_mutex&gt; | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- <shared_mutex>
- shared_mutex/std::swap
- shared_mutex/std::shared_lock
- shared_mutex/std::shared_lock::shared_lock
- shared_mutex/std::shared_lock::operator=
- shared_mutex/std::shared_lock::operator =
- shared_mutex/std::shared_lock::lock
- shared_mutex/std::shared_lock::try_lock
- shared_mutex/std::shared_lock::try_lock_for
- shared_mutex/std::shared_lock::try_lock_until
- shared_mutex/std::shared_lock::unlock
- shared_mutex/std::shared_lock::swap
- shared_mutex/std::shared_lock::release
- shared_mutex/std::shared_lock::owns_lock
- shared_mutex/std::shared_lock::operator bool
- shared_mutex/std::shared_lock::mutex
- shared_mutex/std::shared_mutex
- shared_mutex/std::shared_mutex::native_handle_type
- shared_mutex/std::shared_mutex::shared_mutex
- shared_mutex/std::shared_mutex::operator=
- shared_mutex/std::shared_mutex::operator =
- shared_mutex/std::shared_mutex::lock
- shared_mutex/std::shared_mutex::try_lock
- shared_mutex/std::shared_mutex::unlock
- shared_mutex/std::shared_mutex::lock_shared
- shared_mutex/std::shared_mutex::try_lock_shared
- shared_mutex/std::shared_mutex::unlock_shared
- shared_mutex/std::shared_mutex::native_handle
- shared_mutex/std::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::shared_timed_mutex
- shared_mutex/std::shared_timed_mutex::operator=
- shared_mutex/std::shared_timed_mutex::operator =
- shared_mutex/std::shared_timed_mutex::lock
- shared_mutex/std::shared_timed_mutex::try_lock
- shared_mutex/std::shared_timed_mutex::try_lock_for
- shared_mutex/std::shared_timed_mutex::try_lock_until
- shared_mutex/std::shared_timed_mutex::unlock
- shared_mutex/std::shared_timed_mutex::lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared
- shared_mutex/std::shared_timed_mutex::try_lock_shared_for
- shared_mutex/std::shared_timed_mutex::try_lock_shared_until
- shared_mutex/std::shared_timed_mutex::unlock_shared
dev_langs: C++
ms.assetid: 0b37a97d-ee5d-4050-b29f-09db9f76beb3
caps.latest.revision: "16"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2cdfa90b137da2e1a4c7460dfa54663ddb9a3581
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/21/2017
---
# <a name="ltsharedmutex"></a>&lt;shared_mutex >

Il &lt;shared_mutex > intestazione vengono fornite le primitive di sincronizzazione per la protezione dei dati condivisa che è possibile accedere da più thread. Oltre a fornire il controllo di accesso esclusivo, le classi mutex consentono anche la proprietà condivisa da più thread per l'accesso non esclusivo. I mutex condivisi consentono di controllare le risorse che possono essere lette da più thread, ma devono essere scritte esclusivamente da un unico thread, senza causare una race condition.

L'intestazione &lt;shared_mutex > definisce le classi `shared_mutex` e `shared_timed_mutex`, la classe modello `shared_lock`, la funzione di modello e `swap` per condivisi supporto mutex.

|Classi|Descrizione|
|-------------|-----------------|
|[Classe shared_mutex](../standard-library/shared-mutex.md#class_shared_mutex)|Tipo mutex condiviso che può essere bloccato in modo esclusivo da un solo agente o condiviso in modo non esclusivo da più agenti.|
|[Classe shared_timed_mutex](../standard-library/shared-mutex.md#class_shared_timed_mutex)|Tipo mutex condiviso programmato che può essere bloccato in modo esclusivo da un solo agente o condiviso in modo non esclusivo da più agenti.|
|[Classe shared_lock](../standard-library/shared-mutex.md#class_shared_lock)|Classe modello che esegue il wrapping di un mutex condiviso per supportare operazioni di blocco programmate e la condivisione non esclusiva da parte di più agenti.|

|Funzioni|Descrizione|
|---------------|-----------------|
|[swap](../standard-library/shared-mutex.md#function_swap)|Scambia il contenuto degli oggetti mutex condivisi a cui fanno riferimento i parametri della funzione.|

## <a name="syntax"></a>Sintassi

```cpp
namespace std {
    class shared_mutex;
    class shared_timed_mutex;
    template <class Mutex>
class shared_lock;
    template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
}
```

## <a name="remarks"></a>Note

Un'istanza della classe `shared_mutex` è un *tipo mutex condiviso*, ovvero un tipo che controlla la proprietà condivisa di un mutex all'interno di un ambito. Un tipo mutex condiviso soddisfa tutti i requisiti di un tipo mutex, nonché quelli dei membri, per supportare la proprietà condivisa non esclusiva.

Un tipo mutex condiviso supporta i metodi aggiuntivi `lock_shared`, `unlock_shared` e `try_lock_shared`:

- Il metodo `lock_shared` blocca il thread chiamante finché quest'ultimo non ottiene la proprietà condivisa del mutex.

- Il metodo `unlock_shared` rilascia la proprietà condivisa del mutex detenuta dal thread chiamante.

- Il metodo `try_lock_shared` tenta di ottenere la proprietà condivisa del mutex senza blocco. Il tipo restituito è convertibile in `bool` e `true` se il metodo ottiene la proprietà, mentre altrimenti è `false`.

La classe `shared_timed_mutex` è un *tipo mutex condiviso programmato*, ovvero un tipo che soddisfa i requisiti sia di un tipo mutex condiviso che di un tipo mutex programmato.

Un tipo mutex condiviso programmato supporta i metodi aggiuntivi `try_lock_shared_for` e `try_lock_shared_until`:

- Il metodo `try_lock_shared_for` tenta di ottenere la proprietà condivisa del mutex fino a quando non è trascorso il periodo di tempo specificato dal parametro. Se il periodo di tempo non è positivo, il metodo è equivalente a `try_lock_shared`. Il metodo non restituisce valori entro il periodo di tempo specificato a meno che non ottenga la proprietà condivisa. Il valore restituito è `true` se il metodo ottiene la proprietà; in caso contrario, è `false`.

- Il metodo `try_lock_shared_until` tenta di ottenere la proprietà condivisa del mutex fino a quando non è trascorso il tempo assoluto specificato. Se il tempo assoluto specificato è già trascorso, il metodo è equivalente a `try_lock_shared`. Il metodo non restituisce valori prima dell'ora specificata a meno che non ottenga la proprietà condivisa. Il valore restituito è `true` se il metodo ottiene la proprietà; in caso contrario, è `false`.

La classe modello `shared_lock` estende il supporto per il blocco programmato e il trasferimento della proprietà a un mutex condiviso. La proprietà del mutex può essere ottenuta al momento della costruzione o dopo di essa e può essere trasferita a un altro oggetto `shared_lock`. Gli oggetti di tipo `shared_lock` possono essere spostati ma non copiati.

> [!WARNING]
> A partire da Visual Studio 2015, i tipi di sincronizzazione della libreria Standard C++ si basano sulle primitive di sincronizzazione di Windows e non utilizzano più ConcRT (tranne quando la piattaforma di destinazione è Windows XP). I tipi definiti in &lt;shared_mutex > non deve essere utilizzato con qualsiasi tipo o funzione ConcRT.

## <a name="classes"></a>Classi

###  <a name="class_shared_mutex"></a> Classe shared_mutex

La classe `shared_mutex` implementa un mutex non ricorsivo con semantica di proprietà condivisa.

```cpp
class shared_mutex {
public:
   shared_mutex();
   ~shared_mutex();
   shared_mutex(const shared_mutex&) = delete;
   shared_mutex& operator=(const shared_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   void unlock_shared();
   // Getters
   typedef void** native_handle_type; // implementation defined
   native_handle_type native_handle();
   };
```

###  <a name="class_shared_timed_mutex"></a> Classe shared_timed_mutex

La classe `shared_timed_mutex` implementa un mutex non ricorsivo con semantica di proprietà condivisa che soddisfa i requisiti di un tipo mutex programmato.

```cpp
class shared_timed_mutex {
public:
   shared_timed_mutex();
   ~shared_timed_mutex();
   shared_timed_mutex(const shared_timed_mutex&) = delete;
   shared_timed_mutex& operator=(const shared_timed_mutex&) = delete;
   // Exclusive ownership
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Shared ownership
   void lock_shared();
   // blocking
   bool try_lock_shared();
   template <class Rep, class Period>
   bool try_lock_shared_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_shared_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock_shared();
   };
```

###  <a name="&lt;shared"></a> Classe shared_lock

La classe modello `shared_lock` controlla la proprietà condivisa di un oggetto mutex condiviso all'interno di un ambito. Il parametro di modello deve essere un tipo mutex condiviso.

```cpp
class shared_lock {
public:
   typedef Mutex mutex_type;
   shared_lock() noexcept;
   explicit shared_lock(mutex_type& m);
   // blocking
   shared_lock(mutex_type& m, defer_lock_t) noexcept;
   shared_lock(mutex_type& m, try_to_lock_t);
   shared_lock(mutex_type& m, adopt_lock_t);
   template <class Clock, class Duration>
   shared_lock(mutex_type& m,
   const chrono::time_point<Clock, Duration>& abs_time);
   template <class Rep, class Period>
   shared_lock(mutex_type& m,
   const chrono::duration<Rep, Period>& rel_time);
   ~shared_lock();
   shared_lock(shared_lock const&) = delete;
   shared_lock& operator=(shared_lock const&) = delete;
   shared_lock(shared_lock&& u) noexcept;
   shared_lock& operator=(shared_lock&& u) noexcept;
   void lock();
   // blocking
   bool try_lock();
   template <class Rep, class Period>
   bool try_lock_for(const chrono::duration<Rep, Period>& rel_time);
   template <class Clock, class Duration>
   bool try_lock_until(const chrono::time_point<Clock, Duration>& abs_time);
   void unlock();
   // Setters
   void swap(shared_lock& u) noexcept;
   mutex_type* release() noexcept;
   // Getters
   bool owns_lock() const noexcept;
   explicit operator bool () const noexcept;
   mutex_type* mutex() const noexcept;
private:
   mutex_type* pm; // exposition only
   bool owns; // exposition only
   };
```

## <a name="functions"></a>Funzioni

###  <a name="function_swap"></a>swap

Scambia gli oggetti `shared_lock`.

```cpp
template <class Mutex>
void swap(shared_lock<Mutex>& x, shared_lock<Mutex>& y) noexcept;
```

Scambia il contenuto di due oggetti `shared_lock`. È effettivamente uguale a `x.swap(y)`.

## <a name="requirements"></a>Requisiti

 **Intestazione:** &lt;shared_mutex>

 **Spazio dei nomi:** std

## <a name="see-also"></a>Vedere anche

[Riferimento file di intestazione](../standard-library/cpp-standard-library-header-files.md)  
[&lt;mutex>](../standard-library/mutex.md)