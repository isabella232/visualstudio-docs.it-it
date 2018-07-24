---
title: Eseguire il debug del pacchetto | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 04eb6802cabd4ae36151580c573d28b977ca348e
ms.sourcegitcommit: 36835f1b3ec004829d6aedf01938494465587436
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/23/2018
ms.locfileid: "39204044"
---
# <a name="debug-package"></a>Eseguire il debug del pacchetto
Il pacchetto di debug viene eseguito nella shell di Visual Studio e provvede a tutto l'interfaccia utente. Utilizza le interfacce di debug di Visual Studio e si comunica con gestore di sessione di debug (SDM).  
  
 Gli eventi di interruzione inviati tramite il modello SDM passare dalla modalità di esecuzione per modalità di interruzione e modificare lo stato attivo per il programma in cui si è verificato durante l'interruzione nel debugger. Il pacchetto di debug tiene traccia di stack frame e il thread dalle informazioni inviate dagli eventi.  
  
 Il pacchetto di debug non dispone di lingua o le dipendenze di ambiente run-time. Non è necessario implementare o modificare il pacchetto di debug.  
  
 Il pacchetto di debug viene implementato da *vsdebug.dll*.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione del debug della sessione](../../extensibility/debugger/session-debug-manager.md)   
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Thread](../../extensibility/debugger/threads.md)   
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)