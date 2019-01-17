---
title: IDebugApplicationThreadEvents110 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationThreadEvents110 Interface
ms.assetid: 91a98b0e-7c81-4118-af75-82f75fd4f25a
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: db20440d4dc797ce9a0f21c3ac0c6c89c5d4e036
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348243"
---
# <a name="idebugapplicationthreadevents110-interface"></a>Interfaccia IDebugApplicationThreadEvents110
Aggiunge più eventi di thread. Questi eventi sono solo locali. Vale a dire, è possibile sottoscrivere li solo nel processo che viene eseguito il debug, usando il [IConnectionPoint](http://go.microsoft.com/fwlink/?LinkId=232738) consigliarti e annullare i metodi su oggetti di thread dell'applicazione di PDM (oggetti che implementano [IDebugApplicationThread Interfaccia](../../winscript/reference/idebugapplicationthread-interface.md)). Si verificano nel thread da che provengano.  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IDebugActivationThreadEvents110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|Una chiamata nel thread con thread di PDM ha iniziato il passaggio.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Il thread si riattiva da un punto di interruzione e sarà attivo anche in questo caso.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Il thread sta per sospendere per un punto di interruzione e può gestire le chiamate che richiedono il thread completamente da sospendere.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Una chiamata nel thread thread di PDM tramite il passaggio è stata completata.|