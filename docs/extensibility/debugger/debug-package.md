---
title: Debug del pacchetto | Microsoft Docs
description: Informazioni su come il pacchetto di debug viene eseguito Visual Studio shell e gestisce l'interfaccia utente utilizzando le interfacce di debug e comunicando con la gestione del debug della sessione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: c2692f99388fe5cba3103605480dda1f27b62ff3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122153602"
---
# <a name="debug-package"></a>Pacchetto di debug
Il pacchetto di debug viene eseguito nella shell Visual Studio e gestisce tutta l'interfaccia utente. Usa le interfacce Visual Studio di debug e comunica con la gestione del debug di sessione (SDM).

 Gli eventi di interruzione inviati tramite SDM passano dalla modalità di esecuzione alla modalità di interruzione e passano lo stato attivo al programma in cui si è verificata l'interruzione. Il pacchetto di debug tiene traccia stack frame e il thread dalle informazioni inviate dagli eventi.

 Il pacchetto di debug non presenta dipendenze del linguaggio o dell'ambiente di runtime. Non è necessario implementare o modificare il pacchetto di debug.

 Il pacchetto di debug viene implementato *davsdebug.dll*.

## <a name="see-also"></a>Vedi anche
- [Gestione debug sessione](../../extensibility/debugger/session-debug-manager.md)
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Thread](../../extensibility/debugger/threads.md)
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
