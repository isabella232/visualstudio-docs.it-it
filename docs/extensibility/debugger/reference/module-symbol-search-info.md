---
title: MODULE_SYMBOL_SEARCH_INFO . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 5f15587759c4f665d1593d1298c47459a0e64aac
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714247"
---
# <a name="module_symbol_search_info"></a>MODULE_SYMBOL_SEARCH_INFO

Contiene informazioni sullo stato dei percorsi di ricerca dei simboli in cui è stata eseguita la ricerca.

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

## <a name="members"></a>Membri

`dwValidFields`\
Combinazione di flag dell'enumerazione [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) che specifica il tipo di informazioni di ricerca descritto in questa struttura.

`bstrVerboseSearchInfo`\
Percorso di ricerca e risultati concatenati in un'unica stringa.

## <a name="remarks"></a>Osservazioni

Questa struttura viene restituita da una chiamata al [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) metodo.

Se `bstrVerboseSearchInfo` il campo non è vuoto, contiene un elenco di percorsi ricercati e i risultati di tale ricerca. L'elenco viene formattato con un percorso, seguito dai puntiri di sospensione ("..."), seguito dal risultato. Se è presente più di una coppia di risultati di percorso, ogni coppia è separata da una coppia di risultati di percorso (carriage-return/linefeed). Il modello è simile al seguente:The pattern looks like this:

\<> del percorso... \<risultato>-r-n\<percorso>... \<risultato>-r-n\<percorso>... \<> risultato

Si noti che l'ultima voce non dispone di una sequenza di n.

Ecco una `bstrVerboseSearchInfo` possibile stringa che è stata inviata allo standard out.

`c:\symbols\user32.pdb... File not found.`

`c:\winnt\symbols\user32.pdb... Version does not match.`

`\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Symbols loaded.`

## <a name="requirements"></a>Requisiti

Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche

- [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)
- [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md)
