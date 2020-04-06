---
title: Proprietà IDebugModule3::GetSymbolInfo . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3aafb28715f58eaba4499b47a2e1dee15b82ed14
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726897"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Recupera un elenco di percorsi in cui vengono cercati i simboli e i risultati della ricerca in ogni percorso.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetSymbolInfo(
    SYMBOL_SEARCH_INFO_FIELDS  dwFields,
    MODULE_SYMBOL_SEARCH_INFO* pInfo
);
```

```csharp
int GetSymbolInfo(
    enum_SYMBOL_SEARCH_INFO_FIELDS dwFields,
    MODULE_SYMBOL_SEARCH_INFO[]    pinfo
);
```

## <a name="parameters"></a>Parametri
`dwFields`\
[in] Combinazione di flag dell'enumerazione [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) `pInfo` che specifica i campi di da compilare.

`pInfo`\
[fuori] Una [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) struttura i cui membri devono essere compilati con le informazioni specificate. Se si tratta di un `E_INVALIDARG`valore null, questo metodo restituisce .

## <a name="return-value"></a>Valore restituito
Se il metodo ha `S_OK`esito positivo, restituisce ; in caso contrario, restituisce un codice di errore.

> [!NOTE]
> La stringa restituita `MODULE_SYMBOL_SEARCH_INFO` (nella struttura) potrebbe `S_OK` essere vuota anche se viene restituito. In questo caso, non c'erano informazioni di ricerca da restituire.

## <a name="remarks"></a>Osservazioni
Se `bstrVerboseSearchInfo` il campo `MODULE_SYMBOL_SEARCH_INFO` della struttura non è vuoto, contiene un elenco di percorsi ricercati e i risultati di tale ricerca. L'elenco viene formattato con un percorso, seguito dai puntiri di sospensione ("..."), seguito dal risultato. Se è presente più di una coppia di risultati di percorso, ogni coppia è separata da una coppia di risultati di percorso (carriage-return/linefeed). Il modello è simile al seguente:The pattern looks like this:

\<> del percorso... \<risultato>-r-n\<percorso>... \<risultato>-r-n\<percorso>... \<> risultato

Si noti che l'ultima voce non dispone di una sequenza di n.

## <a name="example"></a>Esempio
In questo esempio, questo metodo restituisce tre percorsi con tre risultati di ricerca diversi. Ogni riga termina con una coppia di ritorno a capo/avanzamento riga. L'output di esempio stampa solo i risultati della ricerca come singola stringa.

> [!NOTE]
> Un risultato di stato è tutto immediatamente dopo il "..." fino alla fine della linea.

```cpp
void ShowSymbolSearchResults(IDebugModule3 *pIDebugModule3)
{
    MODULE_SYMBOL_SEARCH_INFO ssi = { 0 };
    HRESULT hr;
    hr = pIDebugModule3->GetSymbolInfo(SSIF_VERBOSE_SEARCH_INFO,&ssi);
    if (SUCCEEDED(hr)) {
        CComBSTR searchInfo = ssi.bstrVerboseSearchInfo;
        if (searchInfo.Length() != 0) {
            std::wcout << (wchar_t *)(BSTR)searchInfo;
            std::wcout << std::endl;
        }
    }
}
```

**c: . . . . . . . . . File non trovato.** 
 **c: . winnt simboli utente32.pdb... La versione non corrisponde.** 
: i simboli dell'utente32.dll/0a8sd0ad8ad,user32.pdb... ** \\ Simboli caricati.**

## <a name="see-also"></a>Vedere anche

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
