---
title: IActiveScriptSite::GetLCID | Microsoft Docs
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
ms.openlocfilehash: c6ebcfec9764aae98f7d74ac98e0c88ecec7c4da
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155511"
---
# <a name="iactivescriptsitegetlcid"></a>IActiveScriptSite::GetLCID
Recupera l'identificatore delle impostazioni locali associato all'interfaccia utente dell'host. Il motore di script utilizza l'identificatore per verificare che le stringhe di errore e altri elementi dell'interfaccia utente generati dal motore vengano visualizzati nella lingua appropriata.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetLCID(  
    LCID *plcid  // address of variable for language identifier  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `plcid`  
 [out] Indirizzo di una variabile che riceve l'identificatore delle impostazioni locali per gli elementi dell'interfaccia utente visualizzato dal motore di script.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce uno dei valori seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Operazione completata.|  
|`E_NOTIMPL`|Questo metodo non è implementato. Usare le impostazioni locali definiti dal sistema.|  
|`E_POINTER`|È stato specificato un puntatore non valido.|  
  
## <a name="remarks"></a>Note  
 Se questo metodo restituisce `E_NOTIMPL`, usare l'identificatore delle impostazioni locali definiti dal sistema.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)