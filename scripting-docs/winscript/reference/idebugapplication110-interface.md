---
title: IDebugApplication110 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3c040df103bac464e4f440f23674da966063f0ae
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/19/2019
ms.locfileid: "58149669"
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