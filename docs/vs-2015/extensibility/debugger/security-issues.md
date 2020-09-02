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
ms.openlocfilehash: fb6209882a7a71a68728299064edcc13afabff35
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704414"
---
# <a name="security-issues"></a>Problemi di sicurezza
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per eseguire il debug di un programma con Visual Studio, le uniche autorizzazioni necessarie sono le stesse che uno sviluppatore deve eseguire per eseguire il programma. Questo include il debug remoto per la maggior parte delle situazioni (alcune situazioni che interessano altri servizi, ad esempio Internet Information Service, possono richiedere un livello di autorizzazioni più elevato).  
  
 Mentre Visual Studio è in esecuzione, Process Debug Manager (PDM) tiene traccia dei processi di debug nel computer locale. In remoto, un programma denominato msvsmon.exe viene avviato dallo sviluppatore per gestire il debug remoto e rendere disponibile il PDM. Si noti che msvsmon.exe non è un servizio e deve essere avviato manualmente per abilitare il debug remoto su tale computer. Quando Visual Studio (o msvsmon.exe) non è in esecuzione, non viene rilevato alcun processo per il debug.  
  
 Questo significa che uno sviluppatore può eseguire il debug di programmi avviati senza autorizzazioni speciali. Lo sviluppatore può anche eseguire il debug dei processi avviati da un altro utente se l'altra persona è membro dello stesso gruppo di sicurezza. Per abilitare il debug remoto, è necessario solo copiare i file necessari nel computer remoto e avviare msvsmon.exe. per ulteriori informazioni, vedere la pagina [relativa alla configurazione del strumenti remoti nel dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c) .  
  
## <a name="see-also"></a>Vedere anche  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)   
 [Gestione debug processo](../../extensibility/debugger/process-debug-manager.md)   
 [Impostare Remote Tools sul dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)
