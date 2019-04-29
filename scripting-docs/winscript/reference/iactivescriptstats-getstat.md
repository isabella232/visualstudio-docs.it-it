---
title: IActiveScriptStats::GetStat | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.GetStat
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::GetStat
ms.assetid: 31fd15b3-0713-4b55-b4f7-bfd7ea198493
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8befb3da4e4b6f060a5f58aedec3604afe70aefb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992007"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Restituisce una delle statistiche script standard.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT GetStat(  
   DWORD   stid,  
   ULONG*  pluHi,  
   ULONG*  pluLo  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `stid`  
 [in] Specifica quale statistica da restituire. Il valore deve essere:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Restituisce il numero di istruzioni eseguite perché lo script avviato o le statistiche sono state reimpostate.|  
  
 `pluHi`  
 [out] 32 bit alti di un intero senza segno a 64 bit che rappresenta la statistica.  
  
 `pluLo`  
 [out] 32 bit bassi di un intero senza segno a 64 bit che rappresenta la statistica.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati ai valori nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce una delle statistiche script standard.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Interfaccia IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)