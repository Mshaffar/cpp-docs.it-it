---
title: Semantica di CString
ms.date: 11/04/2016
helpviewer_keywords:
- semantics in Cstring
- CString objects, assignment semantics
- assignment statements, assigning CString objects
ms.assetid: d4023480-526f-499a-85f6-324b4de5b85f
ms.openlocfilehash: b5398f8a0f17ffcc93c7f5f6158ecc56606e9279
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62236261"
---
# <a name="cstring-semantics"></a>Semantica di CString

Sebbene [CString](../atl-mfc-shared/reference/cstringt-class.md) gli oggetti sono oggetti dinamici che possono raggiungere, funzionano come tipi primitivi incorporati e le classi semplici. Ogni `CString` oggetto rappresenta un valore univoco. `CString` gli oggetti devono essere considerati come stringhe effettive anziché come puntatori alle stringhe.

È possibile assegnare uno `CString` oggetto a altro. Tuttavia, quando si modifica uno dei due `CString` oggetti, l'altro `CString` oggetto non venga modificato, come illustrato nell'esempio seguente:

[!code-cpp[NVC_ATLMFC_Utilities#188](../atl-mfc-shared/codesnippet/cpp/cstring-semantics_1.cpp)]

Si noti nell'esempio che i due `CString` gli oggetti sono considerati "equal" poiché rappresentano la stessa stringa di caratteri. Il `CString` classe esegue l'overload dell'operatore di uguaglianza (`==`) per confrontare due `CString` gli oggetti in base al relativo valore (contenuto) anziché la propria identità (indirizzo).

## <a name="see-also"></a>Vedere anche

[Stringhe (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)
