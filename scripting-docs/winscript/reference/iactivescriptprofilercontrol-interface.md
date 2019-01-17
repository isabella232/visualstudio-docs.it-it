---
title: Interfaccia IActiveScriptProfilerControl | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7caa09f384ce460a3e73b21b10d6d8022182dde7
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349491"
---
# <a name="iactivescriptprofilercontrol-interface"></a>Interfaccia IActiveScriptProfilerControl
Implementato dal motore di script che supporta la profilatura. In genere, un oggetto che implementa il `IActiveScriptProfilerControl` implementa anche il [IActiveScript](../../winscript/reference/iactivescript.md) interfaccia. In questo caso, è possibile ottenere un handle per il `IActiveScriptProfilerControl` interfaccia chiamando il `IUnknown::QueryInterface` metodo sull'oggetto. L'interfaccia fornisce i metodi necessari per arrestare e avviare la profilatura sul motore di script.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Avvia la profilatura sul motore di scripting.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Imposta il profiler maschera evento nel motore di scripting.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Arresta la profilatura sul motore di scripting.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)