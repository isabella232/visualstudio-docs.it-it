---
title: 'IActiveScript:: AddTypeLib | Microsoft Docs'
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
ms.openlocfilehash: 254a5133d42689020eaaae290a1016de4b848100
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575804"
---
# <a name="iactivescriptaddtypelib"></a>IActiveScript::AddTypeLib
Aggiunge una libreria dei tipi allo spazio dei nomi per lo script. Questa operazione è simile alla direttiva `#include` in C/C++. Consente l'aggiunta di un set di elementi predefiniti come definizioni di classe, `typedefs` e costanti denominate all'ambiente di runtime disponibile per lo script.  
  
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
 in CLSID della libreria dei tipi da aggiungere.  
  
 `dwMaj`  
 in Numero di versione principale.  
  
 `dwMin`  
 in Numero di versione secondario.  
  
 `dwFlags`  
 in Flag di opzione. Può essere il seguente:  
  
|Value|Significato|  
|-----------|-------------|  
|SCRIPTTYPELIB_ISCONTROL|La libreria dei tipi descrive un controllo ActiveX usato dall'host.|  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_INVALIDARG`|Argomento non valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista (ad esempio, il motore di scripting non è ancora stato caricato o inizializzato).|  
|`TYPE_E_CANTLOADLIBRARY`|Impossibile caricare la libreria dei tipi specificata.|  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)