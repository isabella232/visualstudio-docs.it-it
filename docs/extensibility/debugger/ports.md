---
title: Porte | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d6a73aef5151b12360d1e227d440223df4ff3298
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2018
ms.locfileid: "39251049"
---
# <a name="ports"></a>Porte
Nell'architettura di debugger, un *porta*:  
  
-   È un contenitore per una serie di processi in esecuzione in un server. Ad esempio, una porta potrebbe rappresentare una connessione a un dispositivo tramite un cavo seriale basati su Windows CE o a un computer in rete non DCOM. Una porta di speciale, denominata la porta locale, contiene tutti i processi in esecuzione nel computer locale.  
  
-   Grado di identificarsi per nome o identificatore.  
  
-   Possibile enumerare tutti i processi in esecuzione sulla porta e avviare e terminare questi processi.  
  
-   È rappresentato da un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia, che viene creato passando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argomento [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce una porta predefinita che gestisce tutti i processi basati su Windows, sia nativi che gestiti. Una porta personalizzata debba essere configurata per le connessioni con dispositivi esterni che non sono basati su Windows. Per fornire tali porte personalizzate, è necessario impostare anche un fornitore di porte personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)