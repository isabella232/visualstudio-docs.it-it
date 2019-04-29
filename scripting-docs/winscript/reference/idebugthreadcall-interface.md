---
title: Interfaccia IDebugThreadCall | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugThreadCall interface
ms.assetid: 9a9a9892-f310-4ef3-8db2-4f868be52d7e
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 89f0fba2f5210cdcf4bb8f17443f948cb9ba1f4e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63004866"
---
# <a name="idebugthreadcall-interface"></a>Interfaccia IDebugThreadCall
Il `IDebugThreadCall` viene in genere implementata da un componente che effettua chiamate cross-thread con il `IDebugThread` marshalling implementazione fornita dalla gestione del processo di debug (PDM).  
  
 Le chiamate PDM il `IDebugThreadCall` interfaccia nel thread di desiderato e il `IDebugThreadCall` interfaccia invia la chiamata all'implementazione desiderata. Il `IDebugThreadCall` interfaccia viene eseguito il cast le informazioni sui parametri passati nei parametri appropriata nella parte superiore.  
  
 Il `IDebugThreadCall` interfaccia è un oggetto a thread libero.  
  
## <a name="methods"></a>Metodi  
 Oltre ai metodi ereditati da `IUnknown`, il `IDebugThreadCall` interfaccia espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugThreadCall::ThreadCallHandler](../../winscript/reference/idebugthreadcall-threadcallhandler.md)|Gestisce le chiamate per eseguire codice in un altro thread.|