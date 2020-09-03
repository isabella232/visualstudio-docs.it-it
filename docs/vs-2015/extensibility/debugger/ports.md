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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153695"
---
# <a name="ports"></a>Porte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, una **porta**:  
  
- È un contenitore per un set di processi in esecuzione in un server. Una porta, ad esempio, potrebbe rappresentare una connessione a un dispositivo basato su Windows CE da un cavo seriale o a un computer non DCOM connesso in rete. Una porta speciale, denominata porta locale, contiene tutti i processi in esecuzione nel computer locale.  
  
- Può identificare se stesso in base al nome o all'identificatore.  
  
- Può enumerare tutti i processi in esecuzione sulla porta e avviare e terminare questi processi.  
  
- È rappresentato da un'interfaccia [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) , che viene creata passando un argomento [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) a [addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornisce una porta predefinita che gestisce tutti i processi basati su Windows, nativi e gestiti. Una porta personalizzata deve essere implementata per le connessioni con dispositivi esterni che non sono basati su Windows. Per fornire tali porte personalizzate, è necessario implementare anche un fornitore di porte personalizzato.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)
