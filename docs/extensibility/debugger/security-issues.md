---
title: Problemi di sicurezza | Microsoft Docs
description: Informazioni sulle autorizzazioni necessarie per eseguire il debug di un programma Visual Studio, tra cui il debug remoto e situazioni che coinvolgono altri servizi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- security [Debugging SDK]
- debugging [Debugging SDK], security
ms.assetid: d6ffff0a-afb4-4f38-86d8-476c881c4e4b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: eaf0df177b59d14f07a1b71499841ffb447a45ab3df022ef03e5724d85e49310
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377015"
---
# <a name="security-issues"></a>Problemi di sicurezza
Per eseguire il debug di un programma Visual Studio, le uniche autorizzazioni necessarie sono le stesse richieste da uno sviluppatore per eseguire il programma. Ciò include il debug remoto per la maggior parte delle situazioni. Alcune situazioni, che coinvolgono altri servizi, ad esempio Internet Information Service, possono richiedere un livello superiore di autorizzazioni.

 Mentre Visual Studio è in esecuzione, gestione debug processi (PDM) tiene traccia dei processi di debug nel computer locale. In remoto, un programma denominato *msvsmon.exe* viene avviato dallo sviluppatore per gestire il debug remoto e rendere disponibile PDM. *(msvsmon.exe* non è un servizio e deve essere avviato manualmente per abilitare il debug remoto nel computer. Quando Visual Studio (o *msvsmon.exe*) non è in esecuzione, non viene monitorato alcun processo per il debug.

 Uno sviluppatore può eseguire il debug di programmi avviati senza autorizzazioni speciali. Lo sviluppatore può anche eseguire il debug dei processi avviati da un altro utente se l'altra persona è membro dello stesso gruppo di sicurezza. Inoltre, per abilitare il debug remoto, è necessario solo copiare i file necessari nel computer remoto e *avviare* msvsmon.exe. Per altre informazioni, vedere [Debug remoto.](../../debugger/remote-debugging.md)

## <a name="see-also"></a>Vedi anche
- [Attività di debug](../../extensibility/debugger/debugging-tasks.md)
- [Gestione debug processi](../../extensibility/debugger/process-debug-manager.md)
- [Debug remoto](../../debugger/remote-debugging.md)
