---
title: Eseguire il debug del pacchetto | Microsoft Docs
description: Informazioni su come il pacchetto di debug viene eseguito Visual Studio shell e gestisce l'interfaccia utente usando le interfacce di debug e comunicando con la gestione del debug della sessione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 8be920ae352067a6e77593ca0a922474d68851d9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112905670"
---
# <a name="debug-package"></a>Pacchetto di debug
Il pacchetto di debug viene eseguito nella shell Visual Studio e gestisce tutta l'interfaccia utente. Usa le interfacce Visual Studio debug e comunica con gestione del debug di sessione (SDM).

 Gli eventi di interruzione inviati tramite SDM passano dalla modalità di esecuzione alla modalità di interruzione e passano dallo stato attivo al programma in cui si è verificata l'interruzione. Il pacchetto di debug tiene traccia stack frame thread e le informazioni inviate dagli eventi.

 Il pacchetto di debug non ha dipendenze del linguaggio o dell'ambiente di runtime. Non è necessario implementare o modificare il pacchetto di debug.

 Il pacchetto di debug viene implementato da *vsdebug.dll*.

## <a name="see-also"></a>Vedere anche
- [Gestione debug sessione](../../extensibility/debugger/session-debug-manager.md)
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Thread](../../extensibility/debugger/threads.md)
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
