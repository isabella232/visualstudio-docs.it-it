---
title: Pacchetto di debug | Microsoft Docs
description: Informazioni sul modo in cui il pacchetto di debug viene eseguito nella shell di Visual Studio e gestisce l'interfaccia utente tramite l'utilizzo delle interfacce di debug e la comunicazione con gestione debug della sessione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 90c4c82895f7a30d4df9126a280c6c9ffa7ffa76
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105067907"
---
# <a name="debug-package"></a>Debug del pacchetto
Il pacchetto di debug viene eseguito nella shell di Visual Studio e gestisce tutte le interfacce utente. Utilizza le interfacce di debug di Visual Studio e comunica con gestione debug sessione (SDM).

 Interrompi eventi inviati tramite SDM consente di passare dalla modalità di esecuzione al debugger alla modalità di interruzione e impostare lo stato attivo sul programma in cui si è verificata l'interruzione. Il pacchetto di debug tiene traccia del stack frame e del thread dalle informazioni inviate dagli eventi.

 Il pacchetto di debug non ha dipendenze in linguaggio o in fase di esecuzione. Non è necessario implementare o modificare il pacchetto di debug.

 Il pacchetto di debug viene implementato da *vsdebug.dll*.

## <a name="see-also"></a>Vedi anche
- [Gestione debug sessione](../../extensibility/debugger/session-debug-manager.md)
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Thread](../../extensibility/debugger/threads.md)
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
