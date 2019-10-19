---
title: 'IActiveScriptProfilerControl2:: CompleteProfilerStart | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerControl2::CompleteProfilerStart
ms.assetid: e14d94a2-39d3-40a1-84d9-6300fbe2b339
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f0230ecb480792b5b24b7375f5b95926735d0a61
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571563"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Notifica al profiler che è stata avviata la profilatura su tutti i motori di scripting applicabili. Utilizzando questo metodo, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si avvia la profilatura.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parametri  
 Il metodo non accetta parametri.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un valore HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Non è possibile avviare la profilatura.|  
|`S_FALSE`|Profilatura avviata quando uno script non è in esecuzione.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|La profilatura non è abilitata. Non è stato impostato alcun callback.|  
|`E_OUTOFMEMORY`|Impossibile ottenere lo stack di chiamate a causa di una condizione di memoria insufficiente.|  
  
## <a name="remarks"></a>Note  
 La chiamata di `IActiveScriptProfilerControl2::CompleteProfilerStart` garantisce che vengano inviati gli eventi per le funzioni già presenti nello stack di chiamate. Questo metodo deve essere chiamato dopo l'avvio della profilatura in un motore di script che si trova nella scheda corrente. Il metodo può essere chiamato per qualsiasi motore di scripting.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)    
 [Interfaccia IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)