---
title: Porte | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- ports
- debugging [Debugging SDK], ports
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dbc8778af1cbc82b4f9e7f577a95123a1c1f5843
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525417"
---
# <a name="ports"></a>Porte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [porte](https://docs.microsoft.com/visualstudio/extensibility/debugger/ports).  
  
In termini di architettura del debugger, un **porta**:  
  
-   È un contenitore per una serie di processi in esecuzione in un server. Ad esempio, una porta potrebbe rappresentare una connessione a un dispositivo tramite un cavo seriale basati su Windows CE, o a un computer in rete non DCOM. Una porta di speciale, denominata la porta locale, contiene tutti i processi in esecuzione nel computer locale.  
  
-   Grado di identificarsi per nome o identificatore.  
  
-   Possibile enumerare tutti i processi in esecuzione sulla porta e avviare e terminare questi processi.  
  
-   È rappresentato da un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia, che viene creato passando un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) argomento [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornisce una porta predefinita che gestisce tutti i processi basati su Windows, nativi e gestiti. Una porta personalizzata deve essere implementata per le connessioni con dispositivi esterni che non sono basati su Windows. Per fornire tali porte personalizzate, un fornitore di porte personalizzato deve inoltre essere implementata.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)

