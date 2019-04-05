---
title: Problemi di sicurezza | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 874231333c87020c126eac4c066d53512ba0bbc9
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58954262"
---
# <a name="security-issues"></a>Problemi relativi alla sicurezza
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per eseguire il debug di un programma che Usa Visual Studio, le sole autorizzazioni necessite sono gli stessi uno sviluppatore deve eseguire il programma. Sono inclusi il debug remoto per la maggior parte delle situazioni (alcune situazioni che comportano altri servizi, ad esempio il servizio di informazioni Internet, potrebbe essere necessario un livello superiore di autorizzazioni).  
  
 Mentre è in esecuzione Visual Studio, il gestore di debug di processi (PDM) tiene traccia dei processi di debug nel computer locale. In modalità remota, viene avviato un programma denominato msvsmon.exe dallo sviluppatore per gestire il debug remoto e rendere disponibile il PDM. Si noti che msvsmon.exe non è un servizio e deve essere avviata manualmente per abilitare il debug remoto su tale computer. Quando Visual Studio (o msvsmon.exe) non è in esecuzione, nessun processo viene tenuta traccia per il debug.  
  
 Ciò significa che uno sviluppatore può eseguire il debug di programmi che potrà iniziare senza autorizzazioni speciali. Lo sviluppatore può anche eseguire il debug di processi avviati da un altro utente, se tale altra persona è un membro dello stesso gruppo di sicurezza. Per abilitare il debug remoto, è necessario solo per copiare i necessari file all'istanza remota del computer e avviare msvsmon.exe (vedere [Set Up the Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) per altri dettagli).  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [Gestione di Debug di processi](../../extensibility/debugger/process-debug-manager.md)   
 [Impostare Remote Tools sul dispositivo](http://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
