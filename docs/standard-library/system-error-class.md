---
title: Classe system_error
ms.date: 11/04/2016
f1_keywords:
- system_error/std::system_error
helpviewer_keywords:
- system_error class
ms.assetid: 2eeaacbb-8a4a-4ad7-943a-997901a77f32
ms.openlocfilehash: 7a18d2f9f229a62a539be072870e38a990677636
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076370"
---
# <a name="system_error-class"></a>Classe system_error

Rappresenta la classe di base per tutte le eccezioni generate per segnalare un errore di sistema di basso livello.

## <a name="syntax"></a>Sintassi

```cpp
class system_error : public runtime_error {
    explicit system_error(error_code _Errcode, const string& _Message = "");
    system_error(error_code _Errcode, const char *_Message);
    system_error(error_code::value_type _Errval, const error_category& _Errcat, const string& _Message);
    system_error(error_code::value_type _Errval, const error_category& _Errcat, const char *_Message);

    const error_code& code() const throw();
    const char* what() const noexcept override;
};
```

## <a name="remarks"></a>Osservazioni

Il valore restituito da `what` nella classe [exception](../standard-library/exception-class.md) è costruito da `_Message` e dall'oggetto archiviato di tipo [error_code](../standard-library/error-code-class.md) (`code` o `error_code(_Errval, _Errcat)`).

La funzione membro `code` restituisce l'oggetto [error_code](../standard-library/error-code-class.md) archiviato.
