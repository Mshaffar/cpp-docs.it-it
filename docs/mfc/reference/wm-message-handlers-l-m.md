---
title: 'Gestori messaggi WM _: L - M'
ms.date: 11/04/2016
f1_keywords:
- ON_WM_MENUSELECT
- ON_WM_MBUTTONDBLCLK
- ON_WM_MOUSEACTIVATE
- ON_WM_MOUSEMOVE
- ON_WM_MOVING
- ON_WM_LBUTTONUP
- ON_WM_LBUTTONDBLCLK
- ON_WM_MEASUREITEM
- ON_WM_MDIACTIVATE
- ON_WM_MOVE
- ON_WM_LBUTTONDOWN
- ON_WM_MBUTTONDOWN
- ON_WM_MENUCHAR
- ON_WM_MBUTTONUP
helpviewer_keywords:
- ON_WM_MENUSELECT [MFC]
- ON_WM_MBUTTONDBLCLK [MFC]
- ON_WM_MOVE [MFC]
- ON_WM_MOUSEACTIVATE [MFC]
- ON_WM_MBUTTONUP [MFC]
- ON_WM_MOUSEMOVE [MFC]
- ON_WM_MENUCHAR [MFC]
- ON_WM_MBUTTONDOWN [MFC]
- ON_WM_MEASUREITEM [MFC]
- ON_WM_MOVING [MFC]
- ON_WM_LBUTTONDOWN [MFC]
- ON_WM_MDIACTIVATE [MFC]
- ON_WM_LBUTTONDBLCLK [MFC]
- ON_WM_LBUTTONUP [MFC]
- WM_ messages
ms.assetid: 96ecaaf1-6d13-4e12-a454-535635967489
ms.openlocfilehash: 6ebf5ced1f8e36dc059922b67552b19ca4672443
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62309161"
---
# <a name="wm-message-handlers-l---m"></a>Gestori messaggi WM _: L - M

Le seguenti voci della mappa a sinistra corrispondono ai prototipi di funzione a destra:

|Voce della mappa|Prototipo di funzione|
|---------------|------------------------|
|ON_WM_LBUTTONDBLCLK()|void afx_msg [OnLButtonDblClk](../../mfc/reference/cwnd-class.md#onlbuttondblclk)(UINT, CPoint);|
|ON_WM_LBUTTONDOWN()|void afx_msg [OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)(UINT, CPoint);|
|ON_WM_LBUTTONUP()|void afx_msg [OnLButtonUp](../../mfc/reference/cwnd-class.md#onlbuttonup)(UINT, CPoint);|
|ON_WM_MBUTTONDBLCLK()|void afx_msg [OnMButtonDblClk](../../mfc/reference/cwnd-class.md#onmbuttondblclk)(UINT, CPoint);|
|ON_WM_MBUTTONDOWN()|void afx_msg [OnMButtonDown](../../mfc/reference/cwnd-class.md#onmbuttondown)(UINT, CPoint);|
|ON_WM_MBUTTONUP()|void afx_msg [OnMButtonUp](../../mfc/reference/cwnd-class.md#onmbuttonup)(UINT, CPoint);|
|ON_WM_MDIACTIVATE()|afx_msg void [OnMDIActivate](../../mfc/reference/cwnd-class.md#onmdiactivate)(BOOL, CWnd\*, CWnd\*);|
|ON_WM_MEASUREITEM()|void afx_msg [OnMeasureItem](../../mfc/reference/cwnd-class.md#onmeasureitem)(LPMEASUREITEMSTRUCT);|
|ON_WM_MENUCHAR()|afx_msg PROLUNGATA [OnMenuChar](../../mfc/reference/cwnd-class.md#onmenuchar)(UINT, UINT, CMenu\*);|
|ON_WM_MENUDRAG()|afx_msg UINT [OnMenuDrag](../../mfc/reference/cwnd-class.md#onmenudrag)(UINT, CMenu\*);|
|ON_WM_MENUGETOBJECT()|afx_msg UINT [OnMenuGetObject](../../mfc/reference/cwnd-class.md#onmenugetobject)(MENUGETOBJECTINFO\*);|
|ON_WM_MENURBUTTONUP()|void afx_msg [OnMenuRButtonUp](../../mfc/reference/cwnd-class.md#onmenurbuttonup)(UINT, CMenu\*);|
|ON_WM_MENUSELECT()|void afx_msg [OnMenuSelect](../../mfc/reference/cwnd-class.md#onmenuselect)(UINT, UINT, HMENU);|
|ON_WM_MOUSEACTIVATE()|afx_msg int [OnMouseActivate](../../mfc/reference/cwnd-class.md#onmouseactivate)( CWnd\*, UINT, UINT );|
|ON_WM_MOUSEHOVER()|void afx_msg [OnMouseHover](../../mfc/reference/cwnd-class.md#onmousehover)(UINT, CPoint);|
|ON_WM_MOUSEHWHEEL()|void afx_msg [OnMouseHWheel](../../mfc/reference/cwnd-class.md#onmousehwheel)(UINT, short, CPoint);|
|ON_WM_MOUSELEAVE()|void afx_msg [OnMouseLeave](../../mfc/reference/cwnd-class.md#onmouseleave)();|
|ON_WM_MOUSEMOVE()|void afx_msg [OnMouseMove](../../mfc/reference/cwnd-class.md#onmousemove)(UINT, CPoint);|
|ON_WM_MOUSEWHEEL()|BOOL afx_msg [OnMouseWheel](../../mfc/reference/cwnd-class.md#onmousewheel)(UINT, short, CPoint);|
|ON_WM_MOVE()|void afx_msg [OnMove](../../mfc/reference/cwnd-class.md#onmove)(int, int);|
|ON_WM_MOVING()|void afx_msg [OnMoving](../../mfc/reference/cwnd-class.md#onmoving)(UINT, LPRECT);|

## <a name="see-also"></a>Vedere anche

[Mappe messaggi](../../mfc/reference/message-maps-mfc.md)<br/>
[Gestori per WM_ Messages](../../mfc/reference/handlers-for-wm-messages.md)
