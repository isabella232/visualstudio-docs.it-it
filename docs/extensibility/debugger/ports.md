---
title: Porte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e62eb8c220276737cfbe0cd275b0fc81afaa859c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55012234"
---
# <a name="ports"></a>Porte
Nell'architettura di debugger, un *porta*:  
  
- È un contenitore per una serie di processi in esecuzione in un server. Ad esempio, una porta potrebbe rappresentare una connessione a un dispositivo tramite un cavo seriale basati su Windows CE o a un computer in rete non DCOM. Una porta di speciale, denominata la porta locale, contiene tutti i processi in esecuzione nel computer locale.  
  
- Grado di identificarsi per nome o identificatore.  
  
- Possibile enumerare tutti i processi in esecuzione sulla porta e avviare e terminare questi processi.  
  
- È rappresentato da un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia, che viene creato passando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argomento [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce una porta predefinita che gestisce tutti i processi basati su Windows, sia nativi che gestiti. Una porta personalizzata debba essere configurata per le connessioni con dispositivi esterni che non sono basati su Windows. Per fornire tali porte personalizzate, è necessario impostare anche un fornitore di porte personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)