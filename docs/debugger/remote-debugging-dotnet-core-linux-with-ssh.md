---
title: Eseguire il debug di .NET Core in Linux
description: Eseguire il debug di .NET Core in Linux usando Secure Shell (SSH) mediante la connessione a un processo. Preparare l'app per il debug. Compilare e distribuire l'app. Alleghi il debugger.
ms.custom: SEO-VS-2020
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 99bfd1df6d977830e5b8e332efa3d0af653d3aec
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934611"
---
# <a name="debug-net-core-on-linux-using-ssh-by-attaching-to-a-process"></a>Eseguire il debug di .NET Core in Linux tramite SSH mediante la connessione a un processo

A partire da Visual Studio 2017, è possibile connettersi ai processi .NET Core in esecuzione in una distribuzione Linux locale o remota tramite SSH. Questo articolo descrive come configurare il debug e come eseguire il debug. Per gli scenari di debug con i contenitori Docker, vedere la pagina [relativa alla connessione a un processo in esecuzione in un contenitore Docker](../debugger/attach-to-process-running-in-docker-container.md) e agli articoli sugli [strumenti contenitore](../containers/edit-and-refresh.md) . Per eseguire il debug di Linux in WSL 2 da Visual Studio (nessuna connessione al processo), vedere [eseguire il debug di app .NET Core in WSL 2 con Visual Studio](../debugger/debug-dotnet-core-in-wsl-2.md).

## <a name="prerequisites"></a>Prerequisiti

- Nel computer che esegue Visual Studio è necessario installare il carico di lavoro **sviluppo di ASP.NET e Web** o il carico di lavoro **sviluppo multipiattaforma .NET Core** .

- Sul server Linux è necessario installare il server SSH, decomprimerlo e installarlo con curl o wget. Ad esempio, in Ubuntu è possibile eseguire questa operazione eseguendo:

  ``` cmd
  sudo apt-get install openssh-server unzip curl
  ```

- Nel server Linux [installare il Runtime .NET in Linux](/dotnet/core/install/linux)e trovare la pagina corrispondente alla distribuzione Linux, ad esempio Ubuntu. .NET SDK non è obbligatorio.

- Per istruzioni complete ASP.NET Core, vedere [ASP.NET Core host in Linux con nginx](/aspnet/core/host-and-deploy/linux-nginx) e [ASP.NET Core host in Linux con Apache](/aspnet/core/host-and-deploy/linux-apache).

## <a name="prepare-your-application-for-debugging"></a>Preparare l'applicazione per il debug

Per preparare l'applicazione per il debug:

- Si consiglia di usare una configurazione di debug quando si compila l'applicazione. È molto più difficile eseguire il debug del codice compilato al dettaglio (una configurazione di rilascio) rispetto al codice compilato con debug. Se è necessario usare una configurazione di versione, disabilitare prima di tutto Just My Code. Per disabilitare questa impostazione, scegliere **strumenti**  >  **Opzioni**  >  **debug**, quindi deselezionare **Abilita Just My Code**.

- Verificare che il progetto sia configurato per produrre [PDB](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) portabili (impostazione predefinita) e assicurarsi che PDB si trovino nella stessa posizione della dll. Per configurarlo in Visual Studio, fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**  >  **Compila**  >    >  **informazioni di debug** avanzate.

## <a name="build-and-deploy-the-application"></a>Compilare e distribuire l'applicazione

È possibile usare diversi metodi per distribuire l'app prima del debug. Ad esempio, è possibile:

- Copiare le origini nel computer di destinazione e compilarle con ```dotnet build``` nel computer Linux.

- Compilare l'app in Windows e quindi trasferire gli artefatti di compilazione nel computer Linux. Gli artefatti di compilazione sono costituiti dall'applicazione stessa, dal PDB portatile, da tutte le librerie di runtime da cui dipendono e dall' *.deps.jssu* file.

Quando l'app viene distribuita, avviare l'applicazione.

## <a name="attach-the-debugger"></a>Collegare il debugger

Quando l'applicazione è in esecuzione nel computer Linux, è possibile connettersi al debugger.

1. In Visual Studio scegliere **debug**  >  **Connetti a processo...**.

1. Nell'elenco **tipo di connessione** selezionare **SSH**.

1. Modificare la **destinazione di connessione** all'indirizzo IP o al nome host del computer di destinazione.

   Se non sono già state fornite le credenziali, verrà richiesto di immettere una password e/o un file di chiave privata.

   Non sono previsti requisiti per la configurazione della porta, eccetto la porta su cui è in esecuzione il server SSH.

1. Individuare il processo di cui si desidera eseguire il debug.

   Il codice viene eseguito in un nome di processo univoco o in un processo denominato dotnet. Per trovare il processo a cui si è interessati, controllare la colonna **title** , che Mostra gli argomenti della riga di comando per il processo.

   Nell'esempio seguente viene visualizzato un elenco di processi da un computer Linux remoto su un trasporto SSH visualizzato nella finestra di dialogo **Connetti a processo** .

   ![Connetti a processo Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Scegliere **Connetti**.

1. Nella finestra di dialogo visualizzata selezionare il tipo di codice di cui si desidera eseguire il debug. Scegliere **gestito (.NET Core per UNIX)**.

1. Usare le funzionalità di debug di Visual Studio per eseguire il debug dell'app.

   Nell'esempio seguente si noterà che il debugger di Visual Studio è stato interrotto in corrispondenza di un punto di interruzione nel codice in esecuzione in un computer Linux remoto.

   ![Raggiungere un punto di interruzione](media/remote-debug-linux-over-ssh-hit-breakpoint.png)