---
title: Interfaccia IActiveScriptProfilerCallback2 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 6109e028dfc51a88314ce597a67847e95f7eaaed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49815702"
---
# <a name="iactivescriptprofilercallback2-interface"></a>Interfaccia IActiveScriptProfilerCallback2
Fornisce i metodi utilizzati dal motore di scripting per notificare a un oggetto del profiler quando si verificano gli eventi di Strumentazione gestione Windows (DOM, Document Object Model). Questa interfaccia viene implementata dall'oggetto del profiler.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerCallback2::OnFunctionEnterByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionenterbyname.md)|Indica all'oggetto di profiler che il motore di script verrà eseguito una chiamata di funzione DOM.|  
|[IActiveScriptProfilerCallback2::OnFunctionExitByName](../../winscript/reference/iactivescriptprofilercallback2-onfunctionexitbyname.md)|Notifica al profiler che la creazione di script del motore ha terminato l'esecuzione di una chiamata di funzione DOM.|  
  
## <a name="remarks"></a>Note  
 Il `IActiveScriptProfilerCallback2` interfaccia rilasciata inizialmente con Internet Explorer 9.  
  
 Notifica delle chiamate di funzione che non sono chiamate nel DOM avviene tramite il [interfaccia IActiveScriptProfilerCallback](../../winscript/reference/iactivescriptprofilercallback-interface.md).  
  
> [!NOTE]
>  Per aggiungere la possibilità di avviare e interrompere la profilatura quando uno script è in esecuzione, chiamare i metodi seguenti. Usando questi metodi, è possibile ottenere lo stack di chiamate completo se [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è in esecuzione quando si avvia o arresta la profilatura.  
> 
> - Chiamare [IActiveScriptProfilerControl2::CompleteProfilerStart](../../winscript/reference/iactivescriptprofilercontrol2-completeprofilerstart.md) per notificare al profiler che sia stato avviato di profilatura.  
>   -   Chiamare [IActiveScriptProfilerControl2::PrepareProfilerStop](../../winscript/reference/iactivescriptprofilercontrol2-prepareprofilerstop.md) per notificare al profiler che verrà presto interrompere la profilatura.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)