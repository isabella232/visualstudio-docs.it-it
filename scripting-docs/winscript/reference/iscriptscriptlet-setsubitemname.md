---
title: IScriptScriptlet::SetSubItemName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.SetSubItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::SetSubItemName
ms.assetid: 619f222f-b4c3-4c7b-9d19-e4e7037343a6
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8b9a4f67fb5a383666cb9f83fc2e0e38fbffb51f
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58156385"
---
# <a name="iscriptscriptletsetsubitemname"></a>IScriptScriptlet::SetSubItemName
Imposta l'ultimo identificatore nel nome completo dell'host dell'oggetto di scriptlet.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT SetSubItemName(  
   LPCOLESTR          psz  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `psz`  
 Se l'host completo del nome di scriptlet ha più di un livello, `psz` è l'indirizzo del buffer dell'identificatore a livello di secondo.  
  
 Se l'host completo del nome di scriptlet include un livello, `psz` è l'indirizzo del buffer dell'identificatore al primo livello.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)