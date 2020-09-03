---
title: Problemi di sicurezza | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 40898f5633eac374206ed40bfcac96d9c1c5b753
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "80713045"
---
# <a name="security-issues"></a>Problemi di sicurezza
Per eseguire il debug di un programma con Visual Studio, le uniche autorizzazioni necessarie sono le stesse richieste da uno sviluppatore per eseguire il programma. Questo include il debug remoto per la maggior parte delle situazioni. Alcune situazioni, che coinvolgono altri servizi, ad esempio Internet Information Service, possono richiedere un livello di autorizzazioni più elevato.

 Mentre Visual Studio è in esecuzione, Process Debug Manager (PDM) tiene traccia dei processi di debug nel computer locale. In remoto, un programma denominato *msvsmon.exe* viene avviato dallo sviluppatore per gestire il debug remoto e rendere disponibile il PDM. (*msvsmon.exe* non è un servizio e deve essere avviato manualmente per abilitare il debug remoto su tale computer.) Quando Visual Studio (o *msvsmon.exe*) non è in esecuzione, non viene rilevato alcun processo per il debug.

 Uno sviluppatore può eseguire il debug di programmi avviati senza autorizzazioni speciali. Lo sviluppatore può anche eseguire il debug dei processi avviati da un altro utente se l'altra persona è membro dello stesso gruppo di sicurezza. Per abilitare il debug remoto, è necessario solo copiare i file necessari nel computer remoto e avviare *msvsmon.exe*. Per ulteriori informazioni, vedere [Remote Debugging](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Vedere anche
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
- [Gestione debug processo](../../extensibility/debugger/process-debug-manager.md)
- [Debug remoto](../../debugger/remote-debugging.md)
