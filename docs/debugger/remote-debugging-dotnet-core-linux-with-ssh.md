---
title: Eseguire il debug remoto di .NET Core in Linux | Microsoft Docs
ms.date: 02/26/2020
ms.topic: conceptual
helpviewer_keywords:
- remote debugging, linux
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 23bc0fa990a79b1855ec382f42248a0f847c3c9c
ms.sourcegitcommit: 3d64bfb9bf85395357effe054db9a9afaa0be5ea
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/29/2020
ms.locfileid: "78200923"
---
# <a name="remote-debug-net-core-on-linux-using-ssh"></a>Eseguire il debug remoto di .NET Core in Linux con SSH

A partire da Visual Studio 2017, è possibile connettersi ai processi .NET Core in esecuzione in Linux tramite SSH. Questo articolo descrive come configurare il debug e come eseguire il debug.

## <a name="prerequisites"></a>Prerequisites

Nel computer che esegue Visual Studio è necessario installare il carico di lavoro **sviluppo di ASP.NET e Web** o il carico di lavoro **sviluppo multipiattaforma .NET Core** .

Sul server Linux è necessario installare il server SSH, decomprimerlo e installarlo con curl o wget. Ad esempio, in Ubuntu è possibile eseguire questa operazione eseguendo:

``` cmd
sudo apt-get install openssh-server unzip curl
```

## <a name="build-and-deploy-the-application"></a>Compilare e distribuire l'applicazione

Per preparare l'applicazione per il debug:

- Si consiglia di usare una configurazione di debug quando si compila l'applicazione. È molto più difficile eseguire il debug del codice compilato al dettaglio (una configurazione di rilascio) rispetto al codice compilato con debug. Se è necessario usare una configurazione di versione, disabilitare prima di tutto Just My Code. Per disabilitare questa impostazione, scegliere **strumenti** > **Opzioni** > **debug**, quindi deselezionare **Abilita Just My Code**.

- Verificare che il progetto sia configurato per produrre [PDB](https://github.com/OmniSharp/omnisharp-vscode/wiki/Portable-PDBs) portabili (impostazione predefinita) e assicurarsi che PBDs si trovino nella stessa posizione della dll. Per configurarlo in Visual Studio, fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **proprietà** > **Compila** > informazioni **Avanzate** > **debug**.

È possibile usare diversi metodi per distribuire l'app prima del debug. Ad esempio, è possibile:

- Copiare le origini nel computer di destinazione e compilare con ```dotnet build``` nel computer Linux.

- Compilare l'app in Windows e trasferire gli elementi di compilazione nel computer Linux. Gli elementi di compilazione sono costituiti dall'applicazione stessa, da tutte le librerie di runtime da cui dipendono e dal file con *estensione Deps. JSON* .

## <a name="attach-the-debugger"></a>Collegare il debugger

Una volta configurati i computer, avviare l'applicazione nel computer Linux, quindi è possibile connettersi al debugger.

1. In Visual Studio scegliere **Debug** > **Connetti a processo...** .

1. Nell'elenco **tipo di connessione** selezionare **SSH**.

1. Modificare la **destinazione di connessione** all'indirizzo IP o al nome host del computer di destinazione.

1. Individuare il processo di cui si desidera eseguire il debug.

   Il codice viene eseguito in un nome di processo univoco o in un processo denominato dotnet. Per trovare il processo a cui si è interessati, controllare la colonna **title** , che Mostra gli argomenti della riga di comando per il processo.

   Nell'esempio seguente viene visualizzato un elenco di processi da un computer Linux remoto su un trasporto SSH visualizzato nella finestra di dialogo **Connetti a processo** .

   ![Connetti a processo Linux](media/remote-debug-linux-over-ssh-attach.png)

1. Scegliere **Connetti**.

1. Nella finestra di dialogo visualizzata selezionare il tipo di codice di cui si desidera eseguire il debug. Scegliere **gestito (.NET Core per UNIX)** .

1. Usare le funzionalità di debug di Visual Studio per eseguire il debug dell'app.

   Nell'esempio seguente si noterà che il debugger di Visual Studio è stato interrotto in corrispondenza di un punto di interruzione nel codice in esecuzione in un computer Linux remoto.

   ![Raggiungere un punto di interruzione](media/remote-debug-linux-over-ssh-hit-breakpoint.png)