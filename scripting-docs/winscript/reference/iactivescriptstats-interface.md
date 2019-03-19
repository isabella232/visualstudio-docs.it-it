---
title: Interfaccia IActiveScriptStats | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: e7a0e1e616fdee2dac58c8a5a1d24ed120b28bc2
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58152561"
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