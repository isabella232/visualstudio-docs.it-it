---
title: Problemi di sicurezza - Documenti Microsoft
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
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80713045"
---
# <a name="security-issues"></a>Problemi di sicurezza
Per eseguire il debug di un programma utilizzando Visual Studio, le uniche autorizzazioni necessarie sono le stesse che uno sviluppatore richiede per eseguire il programma. Ciò include il debug remoto per la maggior parte delle situazioni. Alcune situazioni, che coinvolgono altri servizi, ad esempio Internet Information Service, potrebbero richiedere un livello superiore di autorizzazioni.

 Mentre Visual Studio è in esecuzione, il gestore di debug dei processi (PDM) tiene traccia dei processi di debug nel computer locale. In remoto, un programma denominato *msvsmon.exe* viene avviato dallo sviluppatore per gestire il debug remoto e rendere disponibile il PDM. (*msvsmon.exe* non è un servizio e deve essere avviato manualmente per abilitare il debug remoto in tale computer.) Quando Visual Studio (o *msvsmon.exe*) non è in esecuzione, non viene tenuta traccia di alcun processo per il debug.

 Uno sviluppatore può eseguire il debug di programmi che hanno iniziato senza autorizzazioni speciali. Lo sviluppatore può anche eseguire il debug dei processi avviati da un altro utente se quest'è membro dello stesso gruppo di sicurezza. Inoltre, per abilitare il debug remoto, è necessario solo copiare i file necessari nel computer remoto e avviare *msvsmon.exe*. Per ulteriori informazioni, vedere [Debug remoto](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Vedere anche
- [Attività di debugDebugging tasks](../../extensibility/debugger/debugging-tasks.md)
- [Gestione debug processo](../../extensibility/debugger/process-debug-manager.md)
- [Debug remoto](../../debugger/remote-debugging.md)
