---
description: Contiene informazioni sullo stato dei percorsi di ricerca dei simboli in cui è stata ricercata.
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 78308844f64e87c95a41b662c2055f770809f262
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627359"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Contiene informazioni sullo stato dei percorsi di ricerca dei simboli in cui è stata ricercata.

## <a name="syntax"></a>Sintassi

```cpp
typedef struct _tagSYMBOL_SEARCH_INFO
{
    SYMBOL_SEARCH_INFO_FIELDS dwValidFields;
    BSTR                      bstrVerboseSearchInfo;
} MODULE_SYMBOL_SEARCH_INFO;
```

```csharp
public struct MODULE_SYMBOL_SEARCH_INFO {
    public uint   dwValidFields;
    public string bstrVerboseSearchInfo;
}
```

## <a name="members"></a>Members

`dwValidFields`\
Combinazione di flag [dell'enumerazione SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) che specifica il tipo di informazioni di ricerca descritte in questa struttura .

`bstrVerboseSearchInfo`\
Percorso di ricerca e risultati concatenati in un'unica stringa.

## <a name="remarks"></a>Commenti

Questa struttura viene restituita da una chiamata [al metodo GetSymbolInfo.](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)

Se il campo non è vuoto, contiene un elenco di percorsi cercati `bstrVerboseSearchInfo` e i risultati della ricerca. L'elenco è formattato con un percorso, seguito da puntini di sospensione ("..."), seguiti dal risultato. Se è presente più di una coppia di risultati di percorso, ogni coppia è separata da una coppia "\r\n" (ritorno a capo/avanzamento riga). Il modello è simile al seguente:

\<path>...\<result>\r\n... \<path> \<result>\r\n\<path> ...\<result>

Si noti che l'ultima voce non ha una \r\n sequenza.

Ecco una possibile `bstrVerboseSearchInfo` stringa che è stata inviata a standard out.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
