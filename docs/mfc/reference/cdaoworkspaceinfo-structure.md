---
title: Struttura CDaoWorkspaceInfo
ms.date: 11/04/2016
f1_keywords:
- CDaoWorkspaceInfo
helpviewer_keywords:
- CDaoWorkspaceInfo structure [MFC]
- DAO (Data Access Objects), Workspaces collection
ms.assetid: a1f4b25e-f9c6-4196-b075-d1df99c54124
ms.openlocfilehash: afbc73c079a6deec3f3e1b7455f9f2dbface5025
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62253633"
---
# <a name="cdaoworkspaceinfo-structure"></a>Struttura CDaoWorkspaceInfo

Il `CDaoWorkspaceInfo` struttura contiene informazioni su un'area di lavoro definito per l'accesso al database di data access Object (DAO).

## <a name="syntax"></a>Sintassi

```
struct CDaoWorkspaceInfo
{
    CString m_strName;           // Primary
    CString m_strUserName;       // Secondary
    BOOL m_bIsolateODBCTrans;    // All
};
```

#### <a name="parameters"></a>Parametri

*m_strName*<br/>
Identifica in modo univoco l'oggetto dell'area di lavoro. Per recuperare direttamente il valore di questa proprietà, chiamare l'oggetto di querydef [GetName](../../mfc/reference/cdaoquerydef-class.md#getname) funzione membro. Per altre informazioni, vedere l'argomento "Proprietà di nome" nella Guida di DAO.

*m_strUserName*<br/>
Un valore che rappresenta il proprietario di un oggetto dell'area di lavoro. Per informazioni correlate, vedere l'argomento "Proprietà UserName" nella Guida di DAO.

*m_bIsolateODBCTrans*<br/>
Un valore che indica se più transazioni che coinvolgono lo stesso database ODBC sono isolate. Per altre informazioni, vedere [CDaoWorkspace::SetIsolateODBCTrans](../../mfc/reference/cdaoworkspace-class.md#setisolateodbctrans). Per informazioni correlate, vedere l'argomento "Proprietà IsolateODBCTrans" nella Guida di DAO.

## <a name="remarks"></a>Note

L'area di lavoro è un oggetto della classe [CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md). I riferimenti al database primario, secondario e tutti sopra indicano la modalità in cui vengono restituite le informazioni per il [funzione membro GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) funzione di membro nella classe `CDaoWorkspace`.

Le informazioni recuperate dal [CDaoWorkspace::GetWorkspaceInfo](../../mfc/reference/cdaoworkspace-class.md#getworkspaceinfo) le funzioni membro vengono archiviate un `CDaoWorkspaceInfo` struttura. `CDaoWorkspaceInfo` definisce inoltre un `Dump` compila la funzione membro in modalità debug. È possibile usare `Dump` per scaricare il contenuto di un `CDaoWorkspaceInfo` oggetto.

## <a name="requirements"></a>Requisiti

**Intestazione:** afxdao. h

## <a name="see-also"></a>Vedere anche

[Strutture, stili, callback e mappe messaggi](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[Classe CDaoWorkspace](../../mfc/reference/cdaoworkspace-class.md)
