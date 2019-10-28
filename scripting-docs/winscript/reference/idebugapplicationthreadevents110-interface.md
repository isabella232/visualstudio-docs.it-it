---
title: Interfaccia IDebugApplicationThreadEvents110 | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 5dd666d825c40155675714f5945209f22198993c
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72984398"
---
# <a name="idebugapplicationthreadevents110-interface"></a>Interfaccia IDebugApplicationThreadEvents110
Aggiunge altri eventi thread. Questi eventi sono solo locali. Ovvero è possibile sottoscriverli solo nel processo di cui è in corso il debug, usando i metodi di notifica e Unadvise di [IConnectionPoint](/windows/win32/api/ocidl/nn-ocidl-iconnectionpoint) negli oggetti thread dell'applicazione PDM (oggetti che implementano l' [interfaccia IDebugApplicationThread](../../winscript/reference/idebugapplicationthread-interface.md)). Si verificano nel thread da cui provengono.  
  
> [!IMPORTANT]
> Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IDebugActivationThreadEvents110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationThreadEvents110 ::OnBeginThreadRequest](../../winscript/reference/idebugapplicationthreadevents110-onbeginthreadrequest.md)|È iniziata una chiamata al thread usando il cambio di thread di PDM.|  
|[IDebugApplicationThreadEvents110::OnResumeFromBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onresumefrombreakpoint.md)|Il thread riprende da un punto di interruzione e sarà nuovamente attivo.|  
|[IDebugApplicationThreadEvents110::OnSuspendForBreakPoint](../../winscript/reference/idebugapplicationthreadevents110-onsuspendforbreakpoint.md)|Il thread sta per sospendere un punto di interruzione e può gestire le chiamate che richiedono la completa sospensione del thread.|  
|[IDebugApplicationThreadEvents110::OnThreadRequestComplete](../../winscript/reference/idebugapplicationthreadevents110-onthreadrequestcomplete.md)|Una chiamata al thread con il cambio di thread di PDM è stata completata.|