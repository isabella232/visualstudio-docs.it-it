---
title: Interfaccia IActiveScriptStats | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptStats interface
ms.assetid: dbe84d6f-1b77-4877-aced-cd4e01ead5b5
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da69920ca78ad47e283fa8f99a28d037edbbe44d
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54350141"
---
# <a name="iactivescriptstats-interface"></a>Interfaccia IActiveScriptStats
Consente a un host interrogare le statistiche di esecuzione di script. L'host può utilizzare queste informazioni per determinare se lo script ha richiesto troppo tempo per il completamento.  
  
 Oltre ai metodi ereditati da `IUnknown`, il `IActiveScriptStats` interfaccia espone i metodi seguenti.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptStats::GetStat](../../winscript/reference/iactivescriptstats-getstat.md)|Restituisce una delle statistiche script standard.|  
|[IActiveScriptStats::GetStatEx](../../winscript/reference/iactivescriptstats-getstatex.md)|Restituisce una statistica di script personalizzato.|  
|[IActiveScriptStats::ResetStats](../../winscript/reference/iactivescriptstats-resetstats.md)|Reimposta le statistiche per questo script.|