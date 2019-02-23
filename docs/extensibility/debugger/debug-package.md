---
title: Eseguire il debug del pacchetto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debugging [Debugging SDK], packages
ms.assetid: 99947fd4-fb87-4c69-b26c-65634e17d285
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2ba784f3a544b2f66f1f2c9c229f85477bf6c782
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56705874"
---
# <a name="debug-package"></a>Eseguire il debug del pacchetto
Il pacchetto di debug viene eseguito nella shell di Visual Studio e provvede a tutto l'interfaccia utente. Utilizza le interfacce di debug di Visual Studio e si comunica con gestore di sessione di debug (SDM).

 Gli eventi di interruzione inviati tramite il modello SDM passare dalla modalità di esecuzione per modalità di interruzione e modificare lo stato attivo per il programma in cui si è verificato durante l'interruzione nel debugger. Il pacchetto di debug tiene traccia di stack frame e il thread dalle informazioni inviate dagli eventi.

 Il pacchetto di debug non dispone di lingua o le dipendenze di ambiente run-time. Non è necessario implementare o modificare il pacchetto di debug.

 Il pacchetto di debug viene implementato da *vsdebug.dll*.

## <a name="see-also"></a>Vedere anche
- [Gestione del debug della sessione](../../extensibility/debugger/session-debug-manager.md)
- [Stack frame](../../extensibility/debugger/stack-frames.md)
- [Thread](../../extensibility/debugger/threads.md)
- [Componenti del debugger](../../extensibility/debugger/debugger-components.md)