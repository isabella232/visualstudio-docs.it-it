---
title: Creazione di un pacchetto di debug . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: de6240ea5d938d02f8415009203962e124ff049e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739028"
---
# <a name="debug-package"></a>Pacchetto di debug
Il pacchetto di debug viene eseguito nella shell di Visual Studio e gestisce tutta l'interfaccia utente. Utilizza le interfacce di debug di Visual Studio e comunica con il gestore di debug della sessione (SDM).

 Gli eventi di interruzione inviati tramite Il modello SDM passano dalla modalità di esecuzione alla modalità di interruzione e spostano lo stato attivo sul programma in cui si è verificata l'interruzione. Il pacchetto di debug tiene traccia dello stack frame e del thread dalle informazioni inviate dagli eventi.

 Il pacchetto di debug non ha dipendenze di linguaggio o ambiente di runtime. Non è necessario implementare o modificare il pacchetto di debug.

 Il pacchetto di debug viene implementato da *vsdebug.dll*.

## <a name="see-also"></a>Vedere anche
- [Gestione debug sessione](../../extensibility/debugger/session-debug-manager.md)
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Discussioni](../../extensibility/debugger/threads.md)
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)
