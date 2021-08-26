---
title: Eseguire il debug di .NET Core in Linux
description: Eseguire il debug di .NET Core in Linux usando Secure Shell (SSH) collegando a un processo. Preparare l'app per il debug. Compilare e distribuire l'app. Collegare il debugger.
ms.custom: SEO-VS-2020
ms.date: 08/24/2021
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 71f9c74e37eafcd8bdaa9e0f9da361a6684c7d4b
ms.sourcegitcommit: aef3e3f99e022675d339b7fe381cb37202be5be2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/24/2021
ms.locfileid: "122785975"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>Eseguire il debug di .NET Core in Linux tramite SSH collegando a un processo

A partire Visual Studio 2017, è possibile connettersi a processi .NET Core in esecuzione in una distribuzione Linux locale o remota tramite SSH. Questo articolo descrive come configurare il debug e come eseguirne il debug. Per scenari di debug con contenitori Docker, vedere invece gli articoli Connettersi a un processo in esecuzione in un contenitore [Docker](../debugger/attach-to-process-running-in-docker-container.md) e Gli [strumenti contenitore.](../containers/edit-and-refresh.md) Per eseguire il debug di Linux in WSL 2 da Visual Studio (nessun collegamento al processo), vedere Eseguire il debug di app [.NET Core in WSL 2 con Visual Studio](../debugger/debug-dotnet-core-in-wsl-2.md).

## <a name="prerequisites"></a>Prerequisiti

- Nel computer Visual Studio è necessario installare il carico di lavoro sviluppo **ASP.NET** e Web o il carico di lavoro **Sviluppo multipiattaforma .NET Core.**

- Nel server Linux è necessario installare il server SSH, decomprimerlo e installarlo con curl o wget. Ad esempio, in Ubuntu è possibile eseguire:

  ``` cmd
  sudo apt-get install openssh-server unzip curl
  ```

  È necessario che SFTP sia abilitato e SSH. La maggior parte delle distribuzioni SSH installa e abilita SFTP per impostazione predefinita, ma questo non è sempre il caso.

- Nel server Linux installare [il runtime .NET](/dotnet/core/install/linux)in Linux e trovare la pagina corrispondente alla distribuzione di Linux ,ad esempio Ubuntu. .NET SDK non è necessario.

- Per istruzioni ASP.NET Core, vedere [Host ASP.NET Core in Linux con Nginx](/aspnet/core/host-and-deploy/linux-nginx) e [Host ASP.NET Core in Linux con Apache.](/aspnet/core/host-and-deploy/linux-apache)

## <a name="prepare-your-application-for-debugging"></a>Preparare l'applicazione per il debug

Per preparare l'applicazione per il debug:

- Quando si compila l'applicazione, è consigliabile usare una configurazione di debug. È molto più difficile eseguire il debug di codice compilato per la vendita al dettaglio (una configurazione di rilascio) rispetto al codice compilato con debug. Se è necessario usare una configurazione di rilascio, disabilitare prima Just My Code. Per disabilitare questa impostazione, scegliere **Strumenti**  >  **Opzioni**  >  **debug**, quindi **deselezionare Abilita** Just My Code .

- Verificare che il progetto sia configurato per produrre [file PDB](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) portabili (impostazione predefinita) e assicurarsi che si trova nello stesso percorso della DLL. Per configurarlo in Visual Studio, fare clic con il pulsante destro del mouse sul progetto, quindi **scegliere** Proprietà  >  **Build**  >  **Advanced**  >  **Debugging Information**.

## <a name="build-and-deploy-the-application"></a>Compilare e distribuire l'applicazione

È possibile usare diversi metodi per distribuire l'app prima del debug. Ad esempio, è possibile:

- Copiare le origini nel computer di destinazione e ```dotnet build``` compilare con nel computer Linux.

- Compilare l'app Windows e quindi trasferire gli artefatti di compilazione nel computer Linux. Gli artefatti di compilazione sono costituiti dall'applicazione stessa, dai PDB portabili, dalle librerie di runtime da cui potrebbe dipendere e dal.deps.js *nel* file.

Quando l'app viene distribuita, avvia l'applicazione.

## <a name="attach-the-debugger"></a>Collegare il debugger

Quando l'applicazione è in esecuzione nel computer Linux, è possibile collegare il debugger.

1. In Visual Studio scegliere **Debug**  >  **Associa a processo...**.

1. **Nell'elenco Tipo di** connessione selezionare **SSH.**

1. Modificare Destinazione **connessione con** l'indirizzo IP o il nome host del computer di destinazione.

   Se non sono ancora state fornite le credenziali, verrà richiesto di immettere una password e/o un file di chiave privata.

   Non è necessario configurare alcuna porta, ad eccezione della porta su cui è in esecuzione il server SSH.

1. Trovare il processo di cui si vuole eseguire il debug.

   Il codice viene eseguito in un nome di processo univoco o in un processo denominato dotnet. Per trovare il processo a cui si è interessati, controllare la colonna **Titolo,** che mostra gli argomenti della riga di comando per il processo.

   Nell'esempio seguente viene visualizzato un elenco di processi da un computer Linux remoto tramite un trasporto SSH visualizzato nella finestra **di dialogo** Associa a processo.

   ![Connettersi a un processo Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Scegliere **Connetti**.

1. Nella finestra di dialogo visualizzata selezionare il tipo di codice di cui si vuole eseguire il debug. Scegliere **Gestito (.NET Core per Unix).**

1. Usare Visual Studio funzionalità di debug per eseguire il debug dell'app.

   Nell'esempio seguente viene visualizzato il debugger Visual Studio in corrispondenza di un punto di interruzione nel codice in esecuzione in un computer Linux remoto.

   ![Raggiungere un punto di interruzione](media/remote-debug-linux-over-ssh-hit-breakpoint.png)