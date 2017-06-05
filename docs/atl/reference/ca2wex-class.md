---
title: Classe CA2WEX | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CA2WEX
- ATLCONV/ATL::CA2WEX
- ATLCONV/ATL::CA2WEX::CA2WEX
- ATLCONV/ATL::CA2WEX::m_psz
- ATLCONV/ATL::CA2WEX::m_szBuffer
dev_langs:
- C++
helpviewer_keywords:
- CA2WEX class
ms.assetid: 317d9ffb-e84f-47e8-beda-57e28fb19124
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 93f3fdbd9c728dcaea0262cb774fe5891e6a9838
ms.contentlocale: it-it
ms.lasthandoff: 03/31/2017

---
# <a name="ca2wex-class"></a>Classe CA2WEX
Questa classe viene utilizzata per le macro di conversione di stringhe `CA2TEX`, `CA2CTEX`, `CT2WEX`, e `CT2CWEX`e typedef **CA2W**.  
  
> [!IMPORTANT]
>  Questa classe e i relativi membri non possono essere utilizzati nelle applicazioni eseguite in Windows Runtime.  
  
## <a name="syntax"></a>Sintassi  
  
```
template <int t_nBufferLength = 128>
class CA2WEX
```  
  
#### <a name="parameters"></a>Parametri  
 `t_nBufferLength`  
 Le dimensioni del buffer utilizzato nel processo di conversione. La lunghezza predefinita è di 128 byte.  
  
## <a name="members"></a>Membri  
  
### <a name="public-constructors"></a>Costruttori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CA2WEX::CA2WEX](#ca2wex)|Costruttore.|  
|[CA2WEX:: ~ CA2WEX](#dtor)|Distruttore.|  
  
### <a name="public-operators"></a>Operatori pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CA2WEX::operator LPWSTR](#operator_lpwstr)|Operatore di conversione.|  
  
### <a name="public-data-members"></a>Membri dati pubblici  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[CA2WEX::m_psz](#m_psz)|Il membro dati che archivia la stringa di origine.|  
|[CA2WEX::m_szBuffer](#m_szbuffer)|Il buffer statico, utilizzato per archiviare la stringa convertita.|  
  
## <a name="remarks"></a>Note  
 A meno che non è necessaria la funzionalità aggiuntiva, utilizzare `CA2TEX`, `CA2CTEX`, `CT2WEX`, `CT2CWEX`, o **CA2W** nel codice.  
  
 Questa classe contiene un buffer a dimensione fissa statico viene utilizzato per archiviare il risultato della conversione. Se il risultato è troppo grande per il buffer statico, la classe alloca memoria con `malloc`, liberando la memoria quando l'oggetto esce dall'ambito. Ciò garantisce che, a differenza del testo macro di conversione disponibili nelle versioni precedenti di ATL, questa classe è possibile utilizzare nei cicli e che non sarà un overflow dello stack.  
  
 Se la classe tenta di allocare memoria in cui l'heap e non riesce, chiama `AtlThrow` con un argomento di **E_OUTOFMEMORY**.  
  
 Per impostazione predefinita, le classi di conversione ATL e le macro utilizzano la tabella codici ANSI del thread corrente per la conversione. Se si desidera ignorare il comportamento per una conversione specifica, specificare la tabella codici come secondo parametro per il costruttore della classe.  
  
 Le macro seguenti sono basate su questa classe:  
  
- `CA2TEX`  
  
- `CA2CTEX`  
  
- `CT2WEX`  
  
- `CT2CWEX`  
  
 La seguente dichiarazione typedef è basato su questa classe:  
  
- **CA2W**  
  
 Per una discussione su queste macro di conversione di testo, vedere [macro di conversione di stringhe MFC e ATL](string-conversion-macros.md).  
  
## <a name="example"></a>Esempio  
 Vedere [macro di conversione di stringhe MFC e ATL](string-conversion-macros.md) per un esempio dell'utilizzo di queste macro di conversione di stringhe.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** atlconv. h  
  
##  <a name="ca2wex"></a>CA2WEX::CA2WEX  
 Costruttore.  
  
```
CA2WEX(LPCSTR psz, UINT nCodePage) throw(...);
CA2WEX(LPCSTR psz) throw(...);
```  
  
### <a name="parameters"></a>Parametri  
 `psz`  
 La stringa di testo da convertire.  
  
 `nCodePage`  
 La tabella codici utilizzata per eseguire la conversione. Vedere la descrizione del parametro pagina codice per il [!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)] funzione [MultiByteToWideChar](http://msdn.microsoft.com/library/windows/desktop/dd319072) per altri dettagli.  
  
### <a name="remarks"></a>Note  
 Consente di allocare il buffer utilizzato nel processo di conversione.  
  
##  <a name="dtor"></a>CA2WEX:: ~ CA2WEX  
 Distruttore.  
  
```
~CA2WEX() throw();
```  
  
### <a name="remarks"></a>Note  
 Consente di liberare il buffer allocato.  
  
##  <a name="m_psz"></a>CA2WEX::m_psz  
 Il membro dati che archivia la stringa di origine.  
  
```
LPWSTR m_psz;
```  
  
##  <a name="m_szbuffer"></a>CA2WEX::m_szBuffer  
 Il buffer statico, utilizzato per archiviare la stringa convertita.  
  
```
wchar_t m_szBuffer[t_nBufferLength];
```  
  
##  <a name="operator_lpwstr"></a>CA2WEX::operator LPWSTR  
 Operatore di conversione.  
  
```  
operator LPWSTR() const throw();
```  
  
### <a name="return-value"></a>Valore restituito  
 Restituisce la stringa di testo come tipo **LPWSTR.**  
  
## <a name="see-also"></a>Vedere anche  
 [Classe CA2AEX](../../atl/reference/ca2aex-class.md)   
 [Classe CA2CAEX](../../atl/reference/ca2caex-class.md)   
 [Classe CW2AEX](../../atl/reference/cw2aex-class.md)   
 [Classe CW2CWEX](../../atl/reference/cw2cwex-class.md)   
 [Classe CW2WEX](../../atl/reference/cw2wex-class.md)   
 [Cenni preliminari sulla classe](../../atl/atl-class-overview.md)
