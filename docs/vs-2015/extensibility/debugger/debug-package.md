---
title: Pacchetto di debug | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68181300"
---
# <a name="debug-package"></a>Pacchetto di debug
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Il pacchetto di debug viene eseguito nella shell di Visual Studio e gestisce tutte le interfacce utente. Utilizza le interfacce di debug di Visual Studio e comunica con gestione debug sessione (SDM).  
  
 Interrompi eventi inviati tramite SDM consente di passare dalla modalità di esecuzione al debugger alla modalità di interruzione e impostare lo stato attivo sul programma in cui si è verificata l'interruzione. Il pacchetto di debug tiene traccia del stack frame e del thread dalle informazioni inviate dagli eventi.  
  
 Il pacchetto di debug non ha dipendenze in linguaggio o in fase di esecuzione. Non è necessario implementare o modificare il pacchetto di debug.  
  
 Il pacchetto di debug viene implementato da vsdebug.dll.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione debug sessione](../../extensibility/debugger/session-debug-manager.md)   
 [Stack frame](../../extensibility/debugger/stack-frames.md)   
 [Thread](../../extensibility/debugger/threads.md)   
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
