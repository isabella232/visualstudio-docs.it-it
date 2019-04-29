---
title: IActiveScript::GetScriptDispatch | Microsoft Docs
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
ms.openlocfilehash: c329a4dbf42461369441b86f6d9ba18992916366
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935599"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Recupera il `IDispatch` interfaccia per i metodi e proprietà associate allo script attualmente in esecuzione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pstrItemName`  
 [in] Indirizzo di un buffer che contiene il nome dell'elemento per cui il chiamante deve avere l'oggetto di distribuzione associati. Se questo parametro è `NULL`, contiene l'oggetto di distribuzione come relativi membri tutte le proprietà e metodi globali definite dallo script. Tramite il `IDispatch` associato e interfaccia `ITypeInfo` interfaccia, l'host può richiamare i metodi di script o una vista e modificare le variabili dello script.  
  
 `ppdisp`  
 [out] Indirizzo di una variabile che riceve un puntatore all'oggetto associato con i metodi globali e le proprietà dello script. Se il motore di scripting non supporta tale tipo di oggetto, `NULL` viene restituito.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting non è ancora caricato o inizializzato).|  
|`S_FALSE`|Il motore di scripting non supporta un oggetto di distribuzione; il `ppdisp` parametro è impostato su NULL.|  
  
## <a name="remarks"></a>Note  
 Poiché i metodi e proprietà possono essere aggiunti tramite la chiamata di [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) interfaccia, il `IDispatch` interfaccia restituita da questo metodo può supportare in modo dinamico nuovi metodi e proprietà. Analogamente, il `IDispatch::GetTypeInfo` metodo deve restituire un nuovo, univoco `ITypeInfo` quando vengono aggiunti proprietà e metodi di interfaccia. Si noti tuttavia che i motori di linguaggio non devono essere modificato il `IDispatch` interfaccia in modo che è incompatibile con uno precedente `ITypeInfo` interfaccia restituita. Ciò significa, ad esempio, che non verranno riutilizzati mai DISPID.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)