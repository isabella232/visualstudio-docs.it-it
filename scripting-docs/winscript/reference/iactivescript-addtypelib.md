---
title: IActiveScript::AddTypeLib | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 695edbd6f5356959785e54dc38f28b68c8c0400e
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54092547"
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
  
|Valore|Significato|  
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