---
title: IScriptScriptlet::GetSubItemName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptScriptlet.GetSubItemName
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptScriptlet::GetSubItemName
ms.assetid: 9ad963fc-9ce8-4b77-92c1-fb90d6307801
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0c48517b7f9f5fab3250b8cff68ad288525145b9
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58155904"
---
# <a name="iscriptscriptletgetsubitemname"></a>IScriptScriptlet::GetSubItemName
Restituisce l'ultimo identificatore in specificare il nome completo dell'host dell'oggetto di scriptlet.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetSubItemName(  
   BSTR               *pbstr  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstr`  
 [out] Se l'host completo del nome di scriptlet ha più di un livello, `pbstr` restituisce l'indirizzo del buffer dell'identificatore a livello di secondo.  
  
 Se l'host completo del nome di scriptlet include un livello, `pbstr` restituisce l'indirizzo del buffer dell'identificatore al primo livello.  
  
## <a name="return-value"></a>Valore restituito  
 Oggetto `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IScriptScriptlet](../../winscript/reference/iscriptscriptlet-interface.md)