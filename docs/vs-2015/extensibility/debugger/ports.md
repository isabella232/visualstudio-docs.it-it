---
title: Porte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 73003e00fef5c37db4a702e7a4a1121600673844
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58955603"
---
# <a name="ports"></a>Porte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **porta**:  
  
- È un contenitore per una serie di processi in esecuzione in un server. Ad esempio, una porta potrebbe rappresentare una connessione a un dispositivo tramite un cavo seriale basati su Windows CE, o a un computer in rete non DCOM. Una porta di speciale, denominata la porta locale, contiene tutti i processi in esecuzione nel computer locale.  
  
- Grado di identificarsi per nome o identificatore.  
  
- Possibile enumerare tutti i processi in esecuzione sulla porta e avviare e terminare questi processi.  
  
- È rappresentato da un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia, che viene creato passando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argomento [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornisce una porta predefinita che gestisce tutti i processi basati su Windows, nativi e gestiti. Una porta personalizzata deve essere implementata per le connessioni con dispositivi esterni che non sono basati su Windows. Per fornire tali porte personalizzate, un fornitore di porte personalizzato deve inoltre essere implementata.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
