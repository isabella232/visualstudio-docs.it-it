---
title: IActiveScriptStats::GetStat | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 0d00c438f0fe03566dfb7efb93645cad02dc7477
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54095394"
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
  
|Costante|Valore|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Restituisce il numero di istruzioni eseguite perché lo script avviato o le statistiche sono state reimpostate.|  
  
 `pluHi`  
 [out] 32 bit alti di un intero senza segno a 64 bit che rappresenta la statistica.  
  
 `pluLo`  
 [out] 32 bit bassi di un intero senza segno a 64 bit che rappresenta la statistica.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati ai valori nella tabella seguente.  
  
|Valore|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce una delle statistiche script standard.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)   
 [Interfaccia IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)