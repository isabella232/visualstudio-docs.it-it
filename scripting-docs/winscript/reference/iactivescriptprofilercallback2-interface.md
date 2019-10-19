---
title: Interfaccia IActiveScriptProfilerCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IActiveScriptProfilerCallback2 interface
ms.assetid: 8f2e62e4-c232-4dc3-a2c0-54dd06298306
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 25f9616497192659df67feedfe16bd9ea0c5e3b1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577307"
---
# <a name="iactivescriptprofilercallback2-interface"></a>Interfaccia IActiveScriptProfilerCallback2
Fornisce metodi utilizzati dal motore di script per notificare a un oggetto del profiler quando si verificano eventi Document Object Model (DOM). Questa interfaccia viene implementata dall'oggetto Profiler.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Notifica all'oggetto profiler che il motore di scripting eseguirà una chiamata di funzione DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Notifica all'oggetto profiler che il motore di script ha terminato l'esecuzione di una chiamata di funzione DOM.|  
  
## <a name="remarks"></a>Note  
 Interfaccia `IActiveScriptProfilerCallback2` rilasciata per la prima volta con Internet Explorer 9.  
  
 La notifica delle chiamate di funzione che non sono chiamate al DOM viene fornita dall' [interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
> Per aggiungere la possibilità di avviare e arrestare la profilatura quando uno script è in esecuzione, chiamare i metodi seguenti. Usando questi metodi, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si avvia o si arresta la profilatura.  
> 
> - Chiamare [IActiveScriptProfilerControl2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) per notificare al profiler che è stata avviata la profilatura.  
>   - Chiamare [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) per notificare al profiler che la profilatura sarà presto arrestata.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)