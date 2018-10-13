---
title: Attacco basato su avvio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- debug engines, launching
- debug engines, attaching to programs
ms.assetid: 362f00ac-1909-4a3a-bacb-c0ceb5549816
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d3603f14d07eb8531480b89f24d73cbd5045da7c
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49188307"
---
# <a name="launch-based-attachment"></a>Collegamento basato su avvio
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Basato su avvio allegato a un programma è automatica. Quando il processo che ospita il programma viene avviato per il modello SDM, basato su avvio degli allegati segue un percorso simile a quella del metodo allegato manuale. Per informazioni, vedere [allegare al programma](../../extensibility/debugger/attaching-to-the-program.md).  
  
## <a name="the-attaching-process"></a>Il processo di collegamento  
 La differenza principale è la sequenza di eventi seguendo la **Attach** chiamare, come indicato di seguito:  
  
1.  Invio di un **IDebugEngineCreateEvent2** oggetto dell'evento per il modello SDM. Per informazioni dettagliate, vedere [l'invio di eventi](../../extensibility/debugger/sending-events.md).  
  
2.  Chiamare il `IDebugProgram2::GetProgramId` metodo sul **IDebugProgram2** interfaccia passato al **Attach** (metodo).  
  
3.  Invio di un **IDebugProgramCreateEvent2** oggetto dell'evento per notificare il modello SDM che locale **IDebugProgram2** oggetto è stato creato per rappresentare il programma per la Germania.  
  
4.  Invio di un [IDebugThreadCreateEvent2](../../extensibility/debugger/reference/idebugthreadcreateevent2.md) oggetto dell'evento per notificare il modello SDM che viene creato un nuovo thread per il processo che ha avviato.  
  
## <a name="see-also"></a>Vedere anche  
 [Invio degli eventi richiesti](../../extensibility/debugger/sending-the-required-events.md)   
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)

