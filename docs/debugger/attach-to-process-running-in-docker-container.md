---
title: Connettersi a un processo in esecuzione in un contenitore Docker
description: Informazioni su come eseguire il debug di un'app che esegue un contenitore Docker con Visual Studio
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jillfra
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: 5b32b402e2bbf85cf5c028ec2dc94821ec463644
ms.sourcegitcommit: 3d96f7a8c9affab40358c3e81e3472db31d841b2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/17/2020
ms.locfileid: "94674779"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Connettersi a un processo in esecuzione in un contenitore Docker 

È possibile eseguire il debug di app in esecuzione in un contenitore Docker di Windows o in un contenitore Docker di Linux .NET Core usando Visual Studio.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a>Connettersi a un processo in esecuzione in un contenitore Docker Linux

È possibile collegare il debugger di Visual Studio a un processo in esecuzione in un contenitore Docker di Linux .NET Core nel computer locale o remoto usando la finestra **di dialogo Connetti a processo** .

> [!IMPORTANT]
> Per usare questa funzionalità, è necessario installare il carico di lavoro sviluppo multipiattaforma .NET Core e avere accesso locale al codice sorgente.

**Per connettersi a un processo in esecuzione in un contenitore Docker Linux:**

1. In Visual Studio selezionare **Debug > Connetti a processo (CTRL + ALT + P)** per aprire la finestra di dialogo **Connetti a processo** .

![Menu Connetti a processo](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Impostare il **tipo di connessione** su **Docker (contenitore Linux)**.
3. Selezionare **trova..** . per impostare la **destinazione della connessione** tramite la finestra di dialogo **Seleziona contenitore Docker** .

    È possibile eseguire il debug di un processo del contenitore Docker in locale o in remoto.

    **Per eseguire il debug di un processo contenitore Docker in locale:**
    1. Impostare host dell'interfaccia della riga di comando **Docker** sul **computer locale**.
    1. Selezionare un contenitore in esecuzione a cui connettersi dall'elenco e fare clic su **OK**.

    ![Selezionare il menu contenitore Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **B. Per eseguire il debug remoto di un processo del contenitore docker:**

    > [!NOTE]
    > Sono disponibili due opzioni per la connessione remota a un processo in esecuzione in un contenitore docker. La prima opzione, per usare SSH, è ideale se gli strumenti Docker non sono installati nel computer locale.  Se gli strumenti Docker sono installati localmente e si ha un daemon Docker configurato per accettare le richieste remote, provare la seconda opzione usando un daemon docker.

    1. **_Per connettersi a un computer remoto tramite SSH:_* _
        1. Selezionare _ *Aggiungi...* * per connettersi a un sistema remoto.<br/>
        ![Connettersi a un sistema remoto](../debugger/media/connect-remote-system.png "Connettersi a un sistema remoto")
        1. Selezionare un contenitore in esecuzione a cui connettersi dopo aver eseguito correttamente la connessione a SSH o daemon e quindi fare clic su **OK**.

    1. **_Per impostare la destinazione su un contenitore remoto che esegue un processo tramite un [daemon Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)_* _
        1. Specificare l'indirizzo del daemon (ad esempio tramite TCP, IP e così via) in _ *Docker host (facoltativo)** e fare clic sul collegamento Refresh (Aggiorna).
        1. Selezionare un contenitore in esecuzione a cui connettersi dopo la connessione al daemon e fare clic su **OK**.

4. Scegliere il processo contenitore corrispondente nell'elenco dei **processi disponibili** e selezionare **Connetti** per avviare il debug del processo contenitore C# in Visual Studio.

    ![Menu Docker collegato completato](../debugger/media/docker-attach-complete.png "Menu Docker collegato Linux completato")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a>Connettersi a un processo in esecuzione in un contenitore Docker di Windows

È possibile collegare il debugger di Visual Studio a un processo in esecuzione in un contenitore Docker di Windows sul computer locale usando la finestra **di dialogo Connetti a processo** .

> [!IMPORTANT]
> Per usare questa funzionalità con un processo di .NET Core, è necessario installare il carico di lavoro sviluppo multipiattaforma .NET Core e avere accesso locale al codice sorgente.

**Per connettersi a un processo in esecuzione in un contenitore Docker di Windows:**

1. In Visual Studio selezionare **Debug > Connetti a processo** (o **CTRL + ALT + P**) per aprire la finestra di dialogo **Connetti a processo** .

   ![Menu Connetti a processo](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Impostare il **tipo di connessione** su **Docker (contenitore di Windows)**.
3. Selezionare **trova..** . per impostare la **destinazione della connessione** usando la finestra di dialogo **Seleziona contenitore Docker** .

    > [!IMPORTANT]
    > Il processo di destinazione deve avere la stessa architettura del processore del contenitore di Windows Docker in cui è in esecuzione.

   L'impostazione della destinazione su un contenitore remoto tramite SSH non è attualmente disponibile e può essere eseguita solo tramite un daemon docker.

    **_Per impostare la destinazione su un contenitore remoto che esegue un processo tramite un [daemon Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)_* _
    1. Specificare l'indirizzo del daemon (ad esempio tramite TCP, IP e così via) in _ *Docker host (facoltativo)** e fare clic sul collegamento Refresh (Aggiorna).

    1. Selezionare un contenitore in esecuzione a cui connettersi dopo la connessione al daemon e scegliere OK.

4. Scegliere il processo contenitore corrispondente nell'elenco dei **processi disponibili** e selezionare **Connetti** per avviare il debug del processo contenitore C#.

    ![Menu Docker collegato completato](../debugger/media/docker-attach-complete-windows.png "Menu di alconnessione Docker Windows completato")

5.  Scegliere il processo contenitore corrispondente nell'elenco dei processi disponibili e scegliere **Connetti** per avviare il debug del processo contenitore C#.