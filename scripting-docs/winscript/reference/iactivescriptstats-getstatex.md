---
title: 'IActiveScriptStats:: GetStatEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStatEx
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStatEx
ms.assetid: f526f51d-8ab5-49ef-a8f7-ae0ac1cb46e4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2ca7cdb81fd7e228b26bfaa12d45e81335674a74
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576115"
---
# <a name="iactivescriptstatsgetstatex"></a>IActiveScriptStats::GetStatEx
Restituisce una statistica personalizzata dello script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetStatEx(  
   REFGUID  guid,  
   ULONG*   pluHi,  
   ULONG*   pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `guid`  
 in Specifica quale statistica restituire. La semantica di quale statistica corrisponde a un determinato GUID è completamente definita dal motore.  
  
 `pluHi`  
 out 32 bit alti di un Unsigned Integer a 64 bit che rappresentano la statistica.  
  
 `pluLo`  
 out Bit 32 bassi di un Unsigned Integer a 64 bit che rappresentano la statistica.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_NOTIMPL`|Il metodo non è implementato.|  
  
## <a name="remarks"></a>Note  
 Questo metodo consente a un motore di script personalizzato di restituire statistiche significative per un host personalizzato.  
  
> [!NOTE]
> Questo metodo non è attualmente implementato.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [IActiveScriptStats:: Getstat](../../winscript/reference/iactivescriptstats-getstat.md)  
 [Interfaccia IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)