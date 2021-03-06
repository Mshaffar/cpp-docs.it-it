---
title: db_param (C++ attributo COM)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.db_param
helpviewer_keywords:
- db_param attribute
ms.assetid: a28315f5-4722-459e-92ef-32e83c0b205a
ms.openlocfilehash: a3cfcf3c7ce3313eaff9a3b35854e1e077fc906f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148094"
---
# <a name="dbparam"></a>db_param

Consente di associare la variabile di membro specificato con un parametro di input o output e delimita la variabile.

## <a name="syntax"></a>Sintassi

```cpp
[ db_param(ordinal, paramtype="DBPARAMIO_INPUT", dbtype, precision, scale, status, length) ]
```

### <a name="parameters"></a>Parametri

*ordinal*<br/>
Numero di colonna (ordinale DBCOLUMNINFO) corrispondente a un campo nel set di righe a cui associare i dati.

*paramtype*<br/>
(Facoltativo) Il tipo da impostare per il parametro. Provider supportano solo i tipi dei / o di parametro supportati dall'origine dati sottostante. Il tipo è una combinazione di uno o più valori DBPARAMIOENUM:

- DBPARAMIO_INPUT un parametro di input.

- DBPARAMIO_OUTPUT un parametro di output.

- DBPARAMIO_NOTPARAM la funzione di accesso non ha parametri. Impostazione `eParamIO` a questo valore nella riga delle funzioni di accesso ricorda all'utente che i parametri vengono ignorati.

*dbtype*<br/>
(Facoltativo) OLE DB [indicatore del tipo](/previous-versions/windows/desktop/ms711251(v=vs.85)) per la voce di colonna.

*precision*<br/>
(Facoltativo) La precisione da utilizzare per la voce di colonna. Per informazioni dettagliate, vedere la descrizione del `bPrecision` dell'elemento di [struttura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))

*scale*<br/>
(Facoltativo) La scala da usare per la voce di colonna. Per informazioni dettagliate, vedere la descrizione del `bScale` dell'elemento di [struttura DBBINDING](/previous-versions/windows/desktop/ms716845(v=vs.85))

*status*<br/>
(Facoltativo) Una variabile membro usata per mantenere lo stato di questa colonna. Lo stato indica se il valore della colonna è un valore di dati o un altro valore, ad esempio valori NULL. Per i valori possibili, vedere [lo stato](/previous-versions/windows/desktop/ms722617(v=vs.85)) nel *riferimento per programmatori OLE DB*.

*length*<br/>
(Facoltativo) Una variabile membro usata per contenere le dimensioni della colonna in byte.

## <a name="remarks"></a>Note

**db_param** definisce i parametri che usano comandi; quindi viene usata con `db_command`. Ad esempio, è possibile usare **db_param** per associare i parametri nella query SQL o stored procedure. I parametri in una stored procedure sono indicati da punti interrogativi (?) e si devono associare i membri dati nell'ordine in cui vengono visualizzati i parametri.

**db_param** delimita i dati dei membri che può far parte di OLE DB `ICommandWithParameters`-associazione basata su. Imposta il tipo di parametro (di input o output), tipo OLE DB, precisione, scala, lo stato e lunghezza per il parametro specificato. Questo attributo consente di inserire le macro di consumer OLE DB BEGIN_PARAM_MAP... END_PARAM_MAP. Ogni membro è contrassegnare con il **db_param** attributo occupa una voce nella mappa sotto forma di un COLUMN_ENTRY.

**db_param** viene usato in combinazione con il [db_table](db-table.md) oppure [db_command](db-command.md) attributi.

Quando il provider di attributi del consumer applica questo attributo a una classe, il compilatore rinomina la classe in \_*NomeClasse*Accessor, dove *NomeClasse* è il nome assegnato alla classe. Il compilatore crea anche una classe denominata *NomeClasse*, che deriva da \_*NomeClasse*Accessor.  In Visualizzazione classi verranno visualizzate entrambe le classi.

## <a name="example"></a>Esempio

L'esempio seguente crea una classe di comando basata sulla procedura SalesbyYear archiviati nel database Northwind. Associa il primo parametro nella stored procedure con il `m_RETURN_VALUE` variabile e definisce come un parametro di output. Associa gli ultimi due parametri (inpui) con `m_Beginning_Date` e `m_Ending_Date`.

L'esempio seguente associa il `nOutput` variabile con un parametro di output.

```cpp
// db_param.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlplus.h>
#include <atldbcli.h>

[ db_source(L"my_connection_string"),
  db_command(L"{ ? = CALL dbo.\"Sales by Year\"(?,?) }")
]
struct CSalesbyYear {
   DBSTATUS m_dwShippedDateStatus;
   DBSTATUS m_dwOrderIDStatus;
   DBSTATUS m_dwSubtotalStatus;
   DBSTATUS m_dwYearStatus;

   DBLENGTH m_dwShippedDateLength;
   DBLENGTH m_dwOrderIDLength;
   DBLENGTH m_dwSubtotalLength;
   DBLENGTH m_dwYearLength;

   // Bind columns
   [ db_column("1", status="m_dwShippedDateStatus", length="m_dwShippedDateLength") ] DBTIMESTAMP m_ShippedDate;
   [ db_column("2", status="m_dwOrderIDStatus", length="m_dwOrderIDLength") ] LONG m_OrderID;
   [ db_column("3", status="m_dwSubtotalStatus", length="m_dwSubtotalLength") ] CURRENCY m_Subtotal;
   [ db_column("4", status="m_dwYearStatus", length="m_dwYearLength") ] TCHAR m_Year[31];

   // Bind parameters
   [ db_param("1", paramtype="DBPARAMIO_OUTPUT") ] LONG m_RETURN_VALUE;
   [ db_param("2", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Beginning_Date;
   [ db_param("3", paramtype="DBPARAMIO_INPUT") ] DBTIMESTAMP m_Ending_Date;
};
```

## <a name="requirements"></a>Requisiti

### <a name="attribute-context"></a>Contesto attributo

|||
|-|-|
|**Si applica a**|**classe**, **struct**, membro, metodo, locale|
|**Ripetibile**|No|
|**Attributi obbligatori**|Nessuna|
|**Attributi non validi**|nessuno|

Per altre informazioni sui contesti di attributi, vedere [Contesti di attributi](cpp-attributes-com-net.md#contexts).

## <a name="see-also"></a>Vedere anche

[Attributi del consumer OLE DB](ole-db-consumer-attributes.md)
