---
title: 'IActiveScriptSite:: GetLcid | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetLCID
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetLCID
ms.assetid: 7b4a2dc1-bcf6-4bbf-884e-97b305a28eb7
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 913ca23ac687fdd080a778afb1dcba2e4dcdd6b8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72570733"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Recupera l'identificatore delle impostazioni locali associato all'interfaccia utente dell'host. Il motore di scripting usa l'identificatore per garantire che le stringhe di errore e altri elementi dell'interfaccia utente generati dal motore vengano visualizzati nella lingua appropriata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `plcid`  
 out Indirizzo di una variabile che riceve l'identificatore delle impostazioni locali per gli elementi dell'interfaccia utente visualizzati dal motore di scripting.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_NOTIMPL`|Questo metodo non è implementato. Utilizzare le impostazioni locali definite dal sistema.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
  
## <a name="remarks"></a>Note  
 Se questo metodo restituisce `E_NOTIMPL`, è necessario utilizzare l'identificatore delle impostazioni locali definito dal sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)