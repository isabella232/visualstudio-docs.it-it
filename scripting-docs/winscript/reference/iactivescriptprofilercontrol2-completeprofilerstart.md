---
title: IActiveScriptProfilerControl2::CompleteProfilerStart | Microsoft Docs
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
ms.openlocfilehash: 36a1f5d6a1401e2860b65a29c8e383627e83c6be
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62993024"
---
# <a name="iactivescriptprofilercontrol2completeprofilerstart"></a>IActiveScriptProfilerControl2::CompleteProfilerStart
Notifica al profiler che è stata avviata la profilatura su tutti i motori di scripting applicabili. Con questo metodo, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si avvia la profilatura.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
HRESULT CompleteProfilerStart();  
```  
  
#### <a name="parameters"></a>Parametri  
 Il metodo non accetta alcun parametro.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce un HRESULT. I valori possibili sono i seguenti:  
  
|Valore restituito|Significato|  
|------------------|-------------|  
|`S_OK`|Il metodo è riuscito.|  
|`E_FAIL`|Profilatura non può essere avviata.|  
|`S_FALSE`|Profilatura è stata avviata quando uno script non è stato in esecuzione.|  
|`ACTIVPROF_E_PROFILER_ABSENT`|Profilatura non è abilitata. Non è stato impostato alcun callback.|  
|`E_OUTOFMEMORY`|Non è possibile ottenere lo stack di chiamate a causa di una condizione di memoria insufficiente.|  
  
## <a name="remarks"></a>Note  
 La chiamata a `IActiveScriptProfilerControl2::CompleteProfilerStart` assicura che vengano inviati gli eventi per le funzioni già nello stack di chiamate. Questo metodo deve essere chiamato dopo la profilatura viene avviata in qualsiasi motore di scripting che si trova nella scheda corrente. Il metodo può essere chiamato per qualsiasi motore di scripting.  
  
## <a name="see-also"></a>Vedere anche  
 [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md)   
 [Interfaccia IActiveScriptProfilerControl2](../../winscript/reference/iactivescriptprofilercontrol2-interface.md)