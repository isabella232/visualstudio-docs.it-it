---
title: Problemi di sicurezza | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4dc31022611d7148d2cb52182b2a10336215afdc
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66345620"
---
# <a name="security-issues"></a>Problemi di sicurezza
Per eseguire il debug di un programma che Usa Visual Studio, le sole autorizzazioni necessite sono uguali a quelle necessarie a eseguire il programma di uno sviluppatore. Sono inclusi il debug remoto per la maggior parte delle situazioni. Alcune situazioni, che includono altri servizi, ad esempio il servizio di informazioni Internet, potrebbero richiedere un livello superiore di autorizzazioni.

 Mentre è in esecuzione Visual Studio, il gestore di debug di processi (PDM) tiene traccia dei processi di debug nel computer locale. In modalità remota, un programma denominato *msvsmon.exe* viene avviata dallo sviluppatore per gestire il debug remoto e rendere disponibile il PDM. (*msvsmon.exe* non è un servizio e deve essere avviata manualmente per abilitare il debug remoto su tale macchina.) Quando Visual Studio (o *msvsmon.exe*) è non in esecuzione, processi non vengono rilevati per il debug.

 Uno sviluppatore può eseguire il debug di programmi che vengono avviati senza autorizzazioni speciali. Lo sviluppatore può anche eseguire il debug di processi avviati da un altro utente, se tale altra persona è un membro dello stesso gruppo di sicurezza. E, per abilitare il debug remoto, è necessario solo copiare i file necessari nel computer remoto e avviare *msvsmon.exe*. Per altre informazioni, vedere [debug remoto](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Vedere anche
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
- [Gestione debug del processo](../../extensibility/debugger/process-debug-manager.md)
- [Debug remoto](../../debugger/remote-debugging.md)
