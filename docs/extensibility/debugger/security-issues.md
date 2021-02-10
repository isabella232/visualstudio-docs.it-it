---
title: Problemi di sicurezza | Microsoft Docs
description: Informazioni sulle autorizzazioni necessarie per eseguire il debug di un programma con Visual Studio, inclusi il debug remoto e le situazioni che coinvolgono altri servizi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 7e7b834dc41fb019e70aa40bca995770985d4c05
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99960923"
---
# <a name="security-issues"></a>Problemi di sicurezza
Per eseguire il debug di un programma con Visual Studio, le uniche autorizzazioni necessarie sono le stesse richieste da uno sviluppatore per eseguire il programma. Questo include il debug remoto per la maggior parte delle situazioni. Alcune situazioni, che coinvolgono altri servizi, ad esempio Internet Information Service, possono richiedere un livello di autorizzazioni più elevato.

 Mentre Visual Studio è in esecuzione, Process Debug Manager (PDM) tiene traccia dei processi di debug nel computer locale. In remoto, un programma denominato *msvsmon.exe* viene avviato dallo sviluppatore per gestire il debug remoto e rendere disponibile il PDM. (*msvsmon.exe* non è un servizio e deve essere avviato manualmente per abilitare il debug remoto su tale computer.) Quando Visual Studio (o *msvsmon.exe*) non è in esecuzione, non viene rilevato alcun processo per il debug.

 Uno sviluppatore può eseguire il debug di programmi avviati senza autorizzazioni speciali. Lo sviluppatore può anche eseguire il debug dei processi avviati da un altro utente se l'altra persona è membro dello stesso gruppo di sicurezza. Per abilitare il debug remoto, è necessario solo copiare i file necessari nel computer remoto e avviare *msvsmon.exe*. Per ulteriori informazioni, vedere [Remote Debugging](../../debugger/remote-debugging.md).

## <a name="see-also"></a>Vedi anche
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
- [Gestione debug processo](../../extensibility/debugger/process-debug-manager.md)
- [Debug remoto](../../debugger/remote-debugging.md)
