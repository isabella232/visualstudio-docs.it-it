---
title: IScriptScriptlet::GetEventName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.GetEventName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::GetEventName
ms.assetid: 548fa650-808e-4c96-8253-5c72e67e8215
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 56566c85aed88faadf740392ad3ec06aa848431e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62786757"
---
# <a name="iscriptscriptletgeteventname"></a>IScriptScriptlet::GetEventName
Restituisce il nome dell'evento associato allo scriptlet.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetEventName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstr`  
 [out] Un buffer che contiene il nome dell'evento che è associato il `IScriptScriptlet` oggetto.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)