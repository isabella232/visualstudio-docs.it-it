---
title: MODULE_SYMBOL_SEARCH_INFO | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- MODULE_SYMBOL_SEARCH_INFO
helpviewer_keywords:
- MODULE_SYMBOL_SEARCH_INFO structure
ms.assetid: 432aff03-08a5-4c5a-b2d5-e212090fc70a
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6886373e521c411c3823b9f15138c8f798a373f4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62913817"
---
# <a name="modulesymbolsearchinfo"></a>MODULE_SYMBOL_SEARCH_INFO

Contiene informazioni sullo stato sui percorsi di ricerca dei simboli che sono stati cercati.

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

## <a name="parameters"></a>Parametri

`dwValidFields`

Una combinazione di flag dal [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) enumerazione che specifica il tipo di informazioni di ricerca descritte in questa struttura.

`bstrVerboseSearchInfo`

Percorso di ricerca e i risultati concatenati in un'unica stringa.

## <a name="remarks"></a>Note

Questa struttura viene restituita da una chiamata per il [GetSymbolInfo](../../../extensibility/debugger/reference/idebugmodule3-getsymbolinfo.md) (metodo).

Se il `bstrVerboseSearchInfo` campo non è vuoto, quindi contiene un elenco di percorsi di ricerca e i risultati della ricerca. L'elenco viene formattato con un percorso, seguito dai puntini di sospensione ("..."), seguito dal risultato. Se è presente più di una coppia di risultati di percorso, quindi ogni coppia è separato da una coppia di "\r\n" (ritorno a capo-/ avanzamento riga). Il modello è simile alla seguente:

\<percorso >... \<risultati > \r\n\<path >... \<risultati > \r\n\<path >... \<risultato >

Si noti che l'ultima voce non dispone di una sequenza \r\n.

Ecco un possibile `bstrVerboseSearchInfo` stringa che è stato inviato a un output standard.

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