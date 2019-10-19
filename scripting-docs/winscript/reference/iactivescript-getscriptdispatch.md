---
title: 'IActiveScript:: GetScriptDispatch | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ba53f2eccde18bd5b2d9c609ea680b50cb7261c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575754"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Recupera l'interfaccia `IDispatch` per i metodi e le proprietà associati allo script attualmente in esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrItemName`  
 in Indirizzo di un buffer che contiene il nome dell'elemento per il quale il chiamante necessita dell'oggetto dispatch associato. Se questo parametro è `NULL`, l'oggetto dispatch contiene come membri tutti i metodi e le proprietà globali definiti dallo script. Tramite l'interfaccia `IDispatch` e l'interfaccia `ITypeInfo` associata, l'host può richiamare metodi script o visualizzare e modificare le variabili di script.  
  
 `ppdisp`  
 out Indirizzo di una variabile che riceve un puntatore all'oggetto associato alle proprietà e ai metodi globali dello script. Se il motore di scripting non supporta tale oggetto, viene restituito `NULL`.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting non è ancora stato caricato o inizializzato).|  
|`S_FALSE`|Il motore di scripting non supporta un oggetto dispatch. il parametro `ppdisp` è impostato su NULL.|  
  
## <a name="remarks"></a>Note  
 Poiché i metodi e le proprietà possono essere aggiunti chiamando l'interfaccia [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) , l'interfaccia `IDispatch` restituita da questo metodo può supportare in modo dinamico nuovi metodi e proprietà. Analogamente, il metodo `IDispatch::GetTypeInfo` deve restituire una nuova interfaccia `ITypeInfo` univoca quando vengono aggiunti metodi e proprietà. Si noti, tuttavia, che i motori di linguaggio non devono modificare l'interfaccia `IDispatch` in modo che sia incompatibile con qualsiasi interfaccia `ITypeInfo` precedente restituita. Ciò implica, ad esempio, che i DISPID non verranno mai riutilizzati.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)