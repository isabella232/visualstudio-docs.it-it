---
title: Modificare Visual Studio carichi di lavoro, componenti, & Language Pack
titleSuffix: ''
description: Informazioni dettagliate su come modificare Visual Studio.
ms.date: 10/12/2020
ms.topic: how-to
ms.custom: vs-acquisition
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 435ee6ad72141453e89aadcfd4ac3310bde0d538
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391075"
---
# <a name="modify-visual-studio-workloads-components-and-language-packs"></a>Modificare Visual Studio carichi di lavoro, componenti e Language Pack

::: moniker range=">=vs-2019"

Visual Studio può essere facilmente modificato in modo da includere solo gli elementi desiderati, quando sono necessari. A tale scopo, aprire il programma di installazione di Visual Studio per aggiungere o rimuovere carichi di lavoro e componenti.

::: moniker-end

::: moniker range="vs-2017"

Oltre ad aver semplificato la personalizzazione di Visual Studio in base alle attività da eseguire, è stata semplificata anche la modifica di Visual Studio. A tale scopo, aprire il nuovo Programma di installazione di Visual Studio e apportare le modifiche desiderate.

::: moniker-end

## <a name="prerequisites"></a>Prerequisiti

+ Per installare, aggiornare o modificare Visual Studio, è necessario accedere con un account con autorizzazioni amministrative. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).

+ Le procedure seguenti presuppongono che si abbia una connessione Internet. Per altre informazioni su come modificare un'[installazione offline](create-an-offline-installation-of-visual-studio.md) di Visual Studio creata in precedenza, vedere sia la pagina [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md) che la pagina [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md).

## <a name="launch-the-installer"></a>Avviare il programma di installazione

Per apportare modifiche all'installazione, è necessario avviare il Visual Studio di installazione.

::: moniker range="vs-2017"

1. Individuare il programma di installazione di Visual Studio all'interno del computer in uso.

     Ad esempio, in un computer che esegue Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

     ![Programma di installazione di Visual Studio](media/locate-the-visual-studio-installer.png "Individuare il programma Microsoft Visual Studio installazione")

     >[!TIP]
     >In alcuni computer il programma di installazione di Visual Studio potrebbe trovarsi sotto la lettera **"M"** come **Microsoft Visual Studio: programma di installazione**.<br/><br/> In alternativa, è possibile trovare il programma di installazione di Visual Studio nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Aprire il programma di installazione e quindi scegliere **Modifica**.

     ![Avviare o modificare Visual Studio](media/modify-visual-studio.png "Modificare Visual Studio 2017")

     > [!IMPORTANT]
     > Se è presente un aggiornamento in sospeso, il pulsante Modifica si trova in una posizione diversa. In questo modo è possibile modificare Visual Studio senza aggiornarlo, se si preferisce. Fare clic su **Altro** e scegliere **Modifica**.
     >
     > ![Aggiornare o modificare Visual Studio](media/modify-or-update-visual-studio.png "Aggiornare o modificare Visual Studio 2017")

::: moniker-end

::: moniker range=">=vs-2019"

1. Individuare il **programma di installazione di Visual Studio** all'interno del computer in uso.

     Nel menu Start di Windows è possibile cercare "programma di installazione".

     ![Programma di installazione di Visual Studio](media/vs-2019/visual-studio-installer.png "Cercare il Programma di installazione di Visual Studio")

     > [!NOTE]
     > È anche possibile trovare il programma di installazione di Visual Studio nella posizione seguente:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata e quindi scegliere **Modifica**.

     ![Scegliere Visual Studio edition e quindi modificare](media/vs-2019/vs-installer-modify.png "Scegliere Visual Studio edizione 2019 e quindi modificare")

     > [!IMPORTANT]
     > Se è presente un aggiornamento in sospeso, il pulsante Modifica si trova in una posizione diversa. In questo modo, è possibile Visual Studio senza aggiornarlo, se necessario. Scegliere **Altro** e quindi **Modifica**.
     >
     > ![Aggiornare o modificare Visual Studio](media/vs-2019/modify-update-visual-studio.png "Aggiornare o modificare Visual Studio 2019")

::: moniker-end

## <a name="change-workloads-or-individual-components"></a>Modificare carichi di lavoro o singoli componenti

::: moniker range="vs-2017"

 [I carichi](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) di lavoro contengono le funzionalità necessarie per il linguaggio di programmazione o la piattaforma in uso. Usare i carichi di lavoro per modificare Visual Studio in modo che supporti il lavoro da eseguire quando desiderato.

1. Nel Programma di installazione di Visual Studio scegliere la scheda **Carichi** di lavoro e quindi selezionare o deselezionare i carichi di lavoro desiderati.

   In alternativa, se non si vogliono usare i carichi di lavoro per personalizzare l'installazione di Visual Studio, scegliere la scheda **Singoli** componenti e selezionare i componenti desiderati e quindi seguire le istruzioni.

    ![Finestra di dialogo di installazione di Visual Studio 2017](media/modify-workloads.png "Scegliere un carico di lavoro in Visual Studio 2019")

1. Scegliere se accettare l'opzione predefinita **Installa durante il download** o selezionare l'opzione **Scarica tutto, quindi installa**.

    ![Visual Studio opzioni di installazione di 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Scegliere di installare durante il download o per scaricare prima e installare in un secondo momento")

    L'opzione "Scarica tutto, quindi installa" è utile se si preferisce scaricare prima tutto il software e quindi installarlo in un secondo momento.

1. Scegliere **Modifica**.

1. Se lo si desidera, scegliere la scheda **Carichi** di lavoro e quindi selezionare o deselezionare i carichi di lavoro desiderati.

1. Dopo aver installato i nuovi carichi di lavoro, **scegliere** Avvia dal Programma di installazione di Visual Studio per aprire Visual Studio.

::: moniker-end

::: moniker range=">=vs-2019"

 I carichi di lavoro contengono le funzionalità necessarie per il linguaggio di programmazione o la piattaforma in uso. Usare i carichi di lavoro per modificare Visual Studio in modo che supporti il lavoro da eseguire quando desiderato.

 > [!TIP]
>Per altre informazioni sui bundle di strumenti e componenti necessari per lo sviluppo, vedere Visual Studio [carichi di lavoro.](https://visualstudio.microsoft.com/vs/#workloads)

1. Nel Programma di installazione di Visual Studio scegliere la scheda **Carichi** di lavoro e quindi selezionare o deselezionare i carichi di lavoro desiderati.

    ![Visual Studio finestra di dialogo di installazione di 2019](media/vs-2019/vs-installer-modify-workloads.png "Scegliere un carico di lavoro in Visual Studio 2019")

1. Scegliere se accettare l'opzione predefinita **Installa durante il download** o selezionare l'opzione **Scarica tutto, quindi installa**.

    ![Visual Studio opzioni di installazione di 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Scegliere di installare durante il download o per scaricare prima e installare in un secondo momento")

    L'opzione "Scarica tutto, quindi installa" è utile se si preferisce scaricare prima tutto il software e quindi installarlo in un secondo momento.

1. Scegliere **Modifica**.

1. Dopo aver installato i nuovi carichi di lavoro, **scegliere** Avvia dal Programma di installazione di Visual Studio per aprire Visual Studio.

::: moniker-end

>[!TIP]
> Per informazioni sul componente SQL Server Data Tools (SSDT), vedere Scaricare e installare [SSDT per](/sql/ssdt/download-sql-server-data-tools-ssdt?view=sql-server-ver15&preserve-view=true)Visual Studio .

## <a name="modify-language-packs"></a>Modificare i Language Pack

Per impostazione predefinita, il programma di installazione corrisponde alla lingua del sistema operativo quando viene eseguito per la prima volta. Tuttavia, è possibile modificare la lingua ogni volta che si vuole. 

A tale scopo, procedere nel seguente modo:

1. Scegliere la **scheda Language Pack** nel Programma di installazione di Visual Studio.
1. Selezionare la lingua preferita.
1. Seguire le istruzioni.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedi anche

* [Elenco degli ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
