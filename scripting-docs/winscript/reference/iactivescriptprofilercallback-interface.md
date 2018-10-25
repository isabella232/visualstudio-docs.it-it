---
title: Interfaccia IActiveScriptProfilerCallback | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 76f9164b-b086-4b29-ac79-76f9c76f1d11
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2511b3e622dfa977c0ed05212203ad59fb0e71bd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49912623"
---
# <a name="iactivescriptprofilercallback-interface"></a>Interfaccia IActiveScriptProfilerCallback
Fornisce i metodi utilizzati dal motore di scripting per notificare a un oggetto del profiler quando si verificano eventi. Questa interfaccia viene implementata dall'oggetto del profiler.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback::Initialize](../../winscript/reference/iactivescriptprofilercallback-initialize.md)|Chiamato per inizializzare l'oggetto del profiler di profilatura all'avvio in un motore di scripting.|  
|[IActiveScriptProfilerCallback::Shutdown](../../winscript/reference/iactivescriptprofilercallback-shutdown.md)|Chiamato per liberare, rilasciare l'oggetto del profiler, ogni volta che viene arrestata la profilatura su un motore di scripting.|  
|[IActiveScriptProfilerCallback::ScriptCompiled](../../winscript/reference/iactivescriptprofilercallback-scriptcompiled.md)|Notifica al profiler che del motore di scripting compilato lo script.|  
|[IActiveScriptProfilerCallback::FunctionCompiled](../../winscript/reference/iactivescriptprofilercallback-functioncompiled.md)|Notifica al profiler che la creazione di script del motore ha rilevato una funzione quando la compilazione di uno script.|  
|[IActiveScriptProfilerCallback::OnFunctionEnter](../../winscript/reference/iactivescriptprofilercallback-onfunctionenter.md)|Indica all'oggetto di profiler che il motore di scripting sta per essere eseguita una chiamata di funzione che non è una chiamata nel modello DOM (Document Object).|  
|[IActiveScriptProfilerCallback::OnFunctionExit](../../winscript/reference/iactivescriptprofilercallback-onfunctionexit.md)|Notifica al profiler di oggetto che il motore di scripting finito l'esecuzione di una funzione chiamata che non è una chiamata nel DOM.|  
  
## <a name="remarks"></a>Note  
 Notifica delle chiamate di funzione nel modello DOM (Document Object) avviene tramite il [interfaccia IActiveScriptProfilerCallback2](../../winscript/reference/iactivescriptprofilercallback2-interface.md).  
  
> [!NOTE]
>  Per aggiungere la possibilità di avviare e interrompere la profilatura quando uno script è in esecuzione, chiamare i metodi seguenti. Usando questi metodi, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si avvia o arresta la profilatura.  
> 
> - Chiamare [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) per notificare al profiler che sia stato avviato di profilatura.  
>   -   Chiamare [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) per notificare al profiler che verrà presto interrompere la profilatura.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)