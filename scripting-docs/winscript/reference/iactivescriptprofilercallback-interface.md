---
title: Interfaccia IActiveScriptProfilerCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9ae520dcb36e00dfaba8702db6294a5a47484b0a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571708"
---
# <a name="iactivescriptprofilercallback-interface"></a>Interfaccia IActiveScriptProfilerCallback
Fornisce i metodi utilizzati dal motore di script per notificare a un oggetto del profiler quando si verificano gli eventi. Questa interfaccia viene implementata dall'oggetto Profiler.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Chiamato per inizializzare l'oggetto profiler ogni volta che viene avviata la profilatura in un motore di script.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Chiamato per liberare e rilasciare l'oggetto profiler ogni volta che la profilatura viene arrestata in un motore di script.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Notifica all'oggetto Profiler la compilazione dello script da parte del motore di script.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Notifica all'oggetto profiler che il motore di script ha rilevato una funzione durante la compilazione di uno script.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Notifica all'oggetto profiler che il motore di script sta per eseguire una chiamata di funzione che non è una chiamata nel Document Object Model (DOM).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Notifica all'oggetto profiler che il motore di script ha terminato l'esecuzione di una chiamata di funzione che non è una chiamata al DOM.|  
  
## <a name="remarks"></a>Note  
 La notifica delle chiamate di funzione nel Document Object Model (DOM) viene fornita dall' [interfaccia IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
> Per aggiungere la possibilità di avviare e arrestare la profilatura quando uno script è in esecuzione, chiamare i metodi seguenti. Usando questi metodi, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si avvia o si arresta la profilatura.  
> 
> - Chiamare [IActiveScriptProfilerControl2:: CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) per notificare al profiler che è stata avviata la profilatura.  
>   - Chiamare [IActiveScriptProfilerControl2::P repareprofilerstop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) per notificare al profiler che la profilatura sarà presto arrestata.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)