---
title: 'IActiveScriptStats:: getstat | Microsoft Docs'
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
ms.openlocfilehash: 096f1cf5b9bf8b5533bd5c36d33f014c747ff9aa
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574342"
---
# <a name="iactivescriptstatsgetstat"></a>IActiveScriptStats::GetStat
Restituisce una delle statistiche standard dello script.  
  
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
 in Specifica quale statistica restituire. Deve essere il valore:  
  
|Costante|Value|Descrizione|  
|--------------|-----------|-----------------|  
|SCRIPTSTAT_STATEMENT_COUNT|1|Restituisce il numero di istruzioni eseguite dopo l'avvio dello script o la reimpostazione delle statistiche.|  
  
 `pluHi`  
 out 32 bit alti di un Unsigned Integer a 64 bit che rappresentano la statistica.  
  
 `pluLo`  
 out Bit 32 bassi di un Unsigned Integer a 64 bit che rappresentano la statistica.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati ai valori indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo restituisce una delle statistiche standard dello script.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [IActiveScriptStats:: GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)  
 [Interfaccia IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)