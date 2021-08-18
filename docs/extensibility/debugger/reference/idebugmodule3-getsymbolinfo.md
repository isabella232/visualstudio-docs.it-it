---
description: Recupera un elenco di percorsi in cui vengono cercati i simboli, nonché i risultati della ricerca di ogni percorso.
title: IDebugModule3::GetSymbolInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d187673c7f2a5f33ecdedd5fe88a3b62d518edc0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133120"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
Recupera un elenco di percorsi in cui vengono cercati i simboli, nonché i risultati della ricerca di ogni percorso.

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
[in] Combinazione di flag [dell'SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) che specifica i campi di da `pInfo` determinare.

`pInfo`\
[out] Struttura [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) i cui membri devono essere compilati con le informazioni specificate. Se si tratta di un valore Null, questo metodo restituisce `E_INVALIDARG` .

## <a name="return-value"></a>Valore restituito
Se il metodo ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore.

> [!NOTE]
> La stringa restituita (nella `MODULE_SYMBOL_SEARCH_INFO` struttura ) potrebbe essere vuota anche se viene `S_OK` restituita. In questo caso, non sono presenti informazioni di ricerca da restituire.

## <a name="remarks"></a>Commenti
Se il campo della struttura non è vuoto, contiene un elenco di percorsi cercati e `bstrVerboseSearchInfo` `MODULE_SYMBOL_SEARCH_INFO` i risultati della ricerca. L'elenco è formattato con un percorso, seguito da puntini di sospensione ("..."), seguiti dal risultato. Se è presente più di una coppia di risultati del percorso, ogni coppia è separata da una coppia "\r\n" (ritorno a capo/avanzamento riga). Il modello è simile al seguente:

\<path>...\<result>\r\n... \<path> \<result>\r\n\<path> ...\<result>

Si noti che l'ultima voce non ha una \r\n sequenza.

## <a name="example"></a>Esempio
In questo esempio, questo metodo restituisce tre percorsi con tre risultati di ricerca diversi. Ogni riga viene terminata con una coppia ritorno a capo/avanzamento riga. L'output di esempio stampa semplicemente i risultati della ricerca come una singola stringa.

> [!NOTE]
> Un risultato di stato è tutto immediatamente dopo "..." fino alla fine della riga.

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

**c:\symbols\user32.pdb... File non trovato.** 
 **c:\winnt\symbols\user32.pdb... La versione non corrisponde.** 
 **\\\symbols\symbols\user32.dll\0a8sd0ad8ad\user32.pdb... Simboli caricati.**

## <a name="see-also"></a>Vedi anche

- [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)
- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)
- [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
