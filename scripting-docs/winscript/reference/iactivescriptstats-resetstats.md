---
title: IActiveScriptStats::ResetStats | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptStats.ResetStats
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptStats::ResetStats
ms.assetid: d98276fc-ad47-4e7b-aae4-254d63aece77
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fbd18719cde85b12e9ec5de3b19dbf8e81bd8575
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62992000"
---
# <a name="iactivescriptstatsresetstats"></a>IActiveScriptStats::ResetStats
Reimposta le statistiche per questo script.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT ResetStats();  
```  
  
#### <a name="parameters"></a>Parametri  
 Questo metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Il metodo restituisce un tipo `HRESULT`. I valori possibili includono, ma non sono limitati a, quelli indicati nella tabella seguente.  
  
|Value|Descrizione|  
|-----------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## <a name="remarks"></a>Note  
 Questo metodo reimposta le statistiche per questo script.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IActiveScriptStats](../../winscript/reference/iactivescriptstats-interface.md)