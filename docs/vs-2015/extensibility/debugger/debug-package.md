---
title: Eseguire il debug del pacchetto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dda8b1ac6eaa2cd5352d441600ae720c3aac321c
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68181300"
---
# <a name="debug-package"></a>Pacchetto di debug
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il pacchetto di debug viene eseguito nella shell di Visual Studio e provvede a tutto l'interfaccia utente. Utilizza le interfacce di debug di Visual Studio e si comunica con gestore di sessione di debug (SDM).  
  
 Gli eventi di interruzione inviati tramite il modello SDM passare dalla modalità di esecuzione per modalità di interruzione e modificare lo stato attivo per il programma in cui si è verificato durante l'interruzione nel debugger. Il pacchetto di debug tiene traccia di stack frame e il thread dalle informazioni inviate dagli eventi.  
  
 Il pacchetto di debug non dispone di lingua o le dipendenze di ambiente run-time. Non è necessario implementare o modificare il pacchetto di debug.  
  
 Il pacchetto di debug viene implementato da vsdebug.dll.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione del Debug della sessione](../../extensibility/debugger/session-debug-manager.md)   
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Thread](../../extensibility/debugger/threads.md)   
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
