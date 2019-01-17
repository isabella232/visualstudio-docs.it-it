---
title: Interfaccia IDebugThreadCall | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: a2167538f2251d961dfcad4a873658d9635a612e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346267"
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