---
title: Connettersi a un processo in esecuzione in un contenitore Docker
description: Informazioni su come eseguire il debug di un'app che esegue un contenitore Docker usando Visual Studio
ms.date: 11/11/2020
ms.topic: conceptual
helpviewer_keywords:
- debugging, linux Docker container
- debugging, Docker container
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: bf895fefa858c8445d7a625c946821afa9ce3ab8b609d66059ad52149c97dda3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346147"
---
# <a name="attach-to-a-process-running-on-a-docker-container"></a>Connettersi a un processo in esecuzione in un contenitore Docker 

È possibile eseguire il debug di app in esecuzione in un contenitore Docker Windows o in un contenitore Docker .NET Core Linux usando Visual Studio.

## <a name="attach-to-a-process-running-on-a-linux-docker-container"></a>Connettersi a un processo in esecuzione in un contenitore Docker Linux

È possibile connettere il debugger Visual Studio a un processo in esecuzione in un contenitore Docker .NET Core Linux nel computer locale o remoto usando la finestra di dialogo Collega **a** processo .

> [!IMPORTANT]
> Per usare questa funzionalità, è necessario installare il carico di lavoro Sviluppo multipiattaforma .NET Core e avere accesso locale al codice sorgente.

**Per connettersi a un processo in esecuzione in un contenitore Docker Linux:**

1. In Visual Studio selezionare Debug > collega a processo **(CTRL+ALT+P)** per aprire la **finestra** di dialogo Collega a processo .

![Screenshot della finestra di dialogo Collega a processo in Visual Studio tipo di connessione Docker (contenitore Linux).](../debugger/media/attach-process-menu.png "Attach_To_Process_Menu")

2. Impostare Tipo **di connessione** su **Docker (contenitore Linux).**
3. Selezionare **Trova...** per impostare la destinazione **connessione** tramite la finestra di dialogo **Seleziona contenitore Docker.**

    È possibile eseguire il debug di un processo del contenitore Docker in locale o in remoto.

    **Per eseguire il debug di un processo contenitore Docker in locale:**
    1. Impostare **l'host dell'interfaccia della riga di** comando di Docker su Computer **locale**.
    1. Selezionare un contenitore in esecuzione a cui connettersi dall'elenco e fare clic su **OK.**

    ![Selezionare il menu del contenitore Docker](../debugger/media/select-docker-container.png "Select_Docker_Container_Menu")

    **B. Per eseguire il debug di un processo del contenitore Docker in modalità remota:**

    > [!NOTE]
    > Esistono due opzioni per la connessione remota a un processo in esecuzione in un contenitore Docker. La prima opzione, per usare SSH, è ideale se gli strumenti Docker non sono installati nel computer locale.  Se gli strumenti Docker sono installati in locale e si dispone di un daemon Docker configurato per accettare richieste remote, provare la seconda opzione usando un daemon Docker.

    1. ***Per connettersi a un computer remoto tramite SSH:***
        1. Selezionare **Aggiungi...** per connettersi a un sistema remoto.<br/>
        ![Connessione a un sistema remoto](../debugger/media/connect-remote-system.png "Connessione a un sistema remoto")
        1. Selezionare un contenitore in esecuzione a cui connettersi dopo aver eseguito correttamente la connessione al daemon o SSH e aver fatto clic **su OK.**

    1. ***Per impostare la destinazione su un contenitore remoto che esegue un processo tramite un [daemon Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
        1. Specificare l'indirizzo del daemon (ad esempio tramite TCP, IP e così via) in **Host Docker (Facoltativo)** e fare clic sul collegamento di aggiornamento.
        1. Selezionare un contenitore in esecuzione a cui connettersi dopo aver eseguito correttamente la connessione al daemon e aver fatto clic **su OK.**

4. Scegliere il processo contenitore corrispondente nell'elenco  Processi **disponibili** e selezionare Collega per avviare il debug del processo contenitore C# in Visual Studio!

    ![Screenshot della finestra di dialogo Collega a processo in Visual Studio. Il tipo di connessione è impostato su Docker (contenitore Linux) e il processo dotnet è selezionato.](../debugger/media/docker-attach-complete.png "Menu Di collegamento Docker Linux completato")

## <a name="attach-to-a-process-running-on-a-windows-docker-container"></a>Connettersi a un processo in esecuzione in un Windows Docker

È possibile connettere il debugger Visual Studio a un processo in esecuzione in un contenitore Docker Windows nel computer locale usando la finestra di dialogo Collega **a** processo .

> [!IMPORTANT]
> Per usare questa funzionalità con un processo .NET Core, è necessario installare il carico di lavoro Sviluppo multipiattaforma .NET Core e avere accesso locale al codice sorgente.

**Per connettersi a un processo in esecuzione in Windows contenitore Docker:**

1. In Visual Studio selezionare **Debug > Collega a** processo (o **CTRL+ALT+P)** per aprire la finestra di dialogo **Collega** a processo .

   ![Screenshot della finestra di dialogo Collega a processo in Visual Studio che mostra un tipo di connessione docker (Windows contenitore).](../debugger/media/attach-process-menu-docker-windows.png "Attach_To_Process_Menu")

2. Impostare Tipo **di connessione** su **Docker (Windows Container).**
3. Selezionare **Trova...** per impostare la destinazione **connessione usando** la finestra di dialogo Seleziona **contenitore Docker.**

    > [!IMPORTANT]
    > Il processo di destinazione deve avere la stessa architettura del processore del Windows Docker in cui è in esecuzione.

   L'impostazione della destinazione su un contenitore remoto tramite SSH non è attualmente disponibile e può essere eseguita solo usando un daemon Docker.

    ***Per impostare la destinazione su un contenitore remoto che esegue un processo tramite un [daemon Docker](https://docs.docker.com/engine/reference/commandline/dockerd/)***
    1. Specificare l'indirizzo del daemon (ad esempio tramite TCP, IP e così via) in **Host Docker (Facoltativo)** e fare clic sul collegamento di aggiornamento.

    1. Selezionare un contenitore in esecuzione a cui connettersi dopo aver eseguito correttamente la connessione al daemon e scegliere OK.

4. Scegliere il processo contenitore corrispondente nell'elenco **Processi disponibili** e selezionare **Collega** per avviare il debug del processo contenitore C#.

    ![Screenshot della finestra di dialogo Collega a processo in Visual Studio. Il tipo di connessione è impostato su Docker (Windows Container) e viene selezionato dotnet.exe processo di connessione.](../debugger/media/docker-attach-complete-windows.png "Completata Windows menu Docker Attach")

5. Scegliere il processo contenitore corrispondente nell'elenco dei processi disponibili e scegliere **Collega** per avviare il debug del processo contenitore C#.