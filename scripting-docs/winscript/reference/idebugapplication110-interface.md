---
title: IDebugApplication110 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplication110 Interface
ms.assetid: ae943133-eb65-4ddc-a29f-9280a82dd8d6
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b13208d6a507ea4ed3157606f358b6b0168180cf
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349556"
---
# <a name="idebugapplication110-interface"></a>Interfaccia IDebugApplication110
Il `IDebugApplication110` interfaccia estende la funzionalità del [interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md). È possibile ottenere un'istanza di questa interfaccia chiamando QueryInterface sull'implementazione di [interfaccia IDebugApplication](../../winscript/reference/idebugapplication-interface.md).  
  
> [!IMPORTANT]
>  Questa interfaccia è implementata da PDM v11.0 e versione successiva. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IDebugApplication110` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplication110::SynchronousCallInMainThread](../../winscript/reference/idebugapplication110-synchronouscallinmainthread.md)|Effettua una chiamata sincrona nel thread principale.|  
|[IDebugApplication110::AsynchronousCallInMainThread](../../winscript/reference/idebugapplication110-asynchronouscallinmainthread.md)|Effettua una chiamata asincrona sul thread principale.|  
|[IDebugApplication110::CallableWaitForHandles](../../winscript/reference/idebugapplication110-callablewaitforhandles.md)|Attende che uno degli handle specificati per ricevere il segnale consentendo chiamata tra thread di essere pubblicata in questo thread. Questo metodo deve essere chiamato dal thread del debugger.|