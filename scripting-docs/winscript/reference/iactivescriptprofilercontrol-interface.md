---
title: Interfaccia IActiveScriptProfilerControl | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 1448b394-9743-41b5-8eb9-5026a45773a4
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ef127e3a4463d112b9ea424702fb2650c80cce7d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571595"
---
# <a name="iactivescriptprofilercontrol-interface"></a>Interfaccia IActiveScriptProfilerControl
Implementato dal motore di script che supporta la profilatura. In genere, un oggetto che implementa l'`IActiveScriptProfilerControl` implementa anche l'interfaccia [IActiveScript](../../winscript/reference/iactivescript.md) . In questo caso, è possibile ottenere un handle per l'interfaccia `IActiveScriptProfilerControl` chiamando il metodo `IUnknown::QueryInterface` sull'oggetto. L'interfaccia fornisce i metodi necessari per arrestare e avviare la profilatura sul motore di scripting.  
  
## <a name="methods"></a>Metodi  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IActiveScriptProfilerControl::StartProfiling](../../winscript/reference/iactivescriptprofilercontrol-startprofiling.md)|Avvia la profilatura sul motore di scripting.|  
|[IActiveScriptProfilerControl::SetProfilerEventMask](../../winscript/reference/iactivescriptprofilercontrol-setprofilereventmask.md)|Imposta la maschera eventi del profiler nel motore di scripting.|  
|[IActiveScriptProfilerControl::StopProfiling](../../winscript/reference/iactivescriptprofilercontrol-stopprofiling.md)|Arresta la profilatura sul motore di scripting.|  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del profiler di script ActiveX](../../winscript/reference/active-script-profiler-interfaces.md)