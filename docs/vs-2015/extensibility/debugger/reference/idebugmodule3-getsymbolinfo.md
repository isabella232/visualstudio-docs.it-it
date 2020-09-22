---
title: 'IDebugModule3:: GetSymbolInfo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugModule3::GetSymbolInfo
helpviewer_keywords:
- GetSymbolInfo method
- IDebugModule3::GetSymbolInfo method
ms.assetid: dda5e8e1-6878-4aa9-9ee4-e7d0dcc11210
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 48dd08b8ef1a8b32497d03dc7989b32a22ee5a9c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840277"
---
# <a name="idebugmodule3getsymbolinfo"></a>IDebugModule3::GetSymbolInfo
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Recupera un elenco di percorsi in cui vengono cercati i simboli e i risultati della ricerca in ogni percorso.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametri  
 `dwFields`  
 in Combinazione di flag dell'enumerazione [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md) che specificano i campi da `pInfo` compilare.  
  
 `pInfo`  
 out Struttura [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) i cui membri devono essere compilati con le informazioni specificate. Se si tratta di un valore null, questo metodo restituisce `E_INVALIDARG` .  
  
## <a name="return-value"></a>Valore restituito  
 Se il metodo ha esito positivo, restituisce `S_OK` ; in caso contrario, restituisce un codice di errore.  
  
> [!NOTE]
> La stringa restituita (nella `MODULE_SYMBOL_SEARCH_INFO` struttura) può essere vuota anche se `S_OK` viene restituito. In questo caso, non sono presenti informazioni di ricerca da restituire.  
  
## <a name="remarks"></a>Commenti  
 Se il `bstrVerboseSearchInfo` campo della `MODULE_SYMBOL_SEARCH_INFO` struttura non è vuoto, contiene un elenco di percorsi cercati e i risultati della ricerca. L'elenco è formattato con un percorso, seguito da puntini di sospensione ("..."), seguito dal risultato. Se è presente più di una coppia di risultati di percorso, ogni coppia è separata da una coppia "\r\n" (ritorno a capo/avanzamento riga). Il modello ha un aspetto simile al seguente:  
  
 \<path>...\<result> \r\n \<path> ... \<result> \r\n \<path> ...\<result>  
  
 Si noti che l'ultima voce non ha una sequenza \r\n.  
  
## <a name="example"></a>Esempio  
 In questo esempio, questo metodo restituisce tre percorsi con tre risultati di ricerca diversi. Ogni riga termina con una coppia ritorno a capo/avanzamento riga. L'output di esempio stampa semplicemente i risultati della ricerca come una singola stringa.  
  
> [!NOTE]
> Un risultato di stato è tutto ciò che segue immediatamente "..." fino alla fine della riga.  
  
```cpp#  
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
  
 **c:\symbols\user32.pdb... Il file non è stato trovato.**  
**c:\winnt\symbols\user32.pdb... La versione non corrisponde.**  
**\\\symbols\symbols\user32.dll \0a8sd0ad8ad\user32.pdb... Simboli caricati.**   
## <a name="see-also"></a>Vedere anche  
 [SYMBOL_SEARCH_INFO_FIELDS](../../../extensibility/debugger/reference/symbol-search-info-fields.md)   
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)   
 [IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)
