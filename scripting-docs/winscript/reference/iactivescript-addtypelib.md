---
title: IActiveScript::AddTypeLib | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.AddTypeLib
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_AddTypeLib
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c4943d1305c2f25de4eec9e782949a66827de879
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62955091"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Aggiunge una libreria dei tipi per lo spazio dei nomi per lo script. Ciò è simile al `#include` direttiva in C/C++. Consente un set di elementi predefiniti, ad esempio le definizioni di classe, `typedefs`e da aggiungere all'ambiente di runtime disponibile per lo script di costanti denominate.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guidTypeLib`  
 [in] CLSID della libreria dei tipi da aggiungere.  
  
 `dwMaj`  
 [in] Numero di versione principale.  
  
 `dwMin`  
 [in] Numero di versione secondario.  
  
 `dwFlags`  
 [in] Flag di opzione. Può essere il seguente:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|La libreria dei tipi descrive un controllo ActiveX utilizzato dall'host.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Un argomento non valido.|  
|`E_UNEXPECTED`|La chiamata non era previsto (ad esempio, il motore di scripting non è ancora caricato o inizializzato).|  
|`TYPE_E_CANTLOADLIBRARY`|Non è stato possibile caricare la libreria dei tipi specificata.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)