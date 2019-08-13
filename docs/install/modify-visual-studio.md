---
title: Modificare Visual Studio
titleSuffix: ''
description: Informazioni dettagliate su come modificare Visual Studio.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 07/31/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: ad5b8a0c261ed967710480b0abd3a2b9d34f01ce
ms.sourcegitcommit: 5694c5236fa32ba7f5bc1236a853f725ec7557e9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/31/2019
ms.locfileid: "68681379"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modificare Visual Studio aggiungendo o rimuovendo carichi di lavoro e componenti

::: moniker range="vs-2019"

Visual Studio può essere facilmente modificato in modo da includere solo gli elementi desiderati, quando sono necessari. A tale scopo, aprire il programma di installazione di Visual Studio per aggiungere o rimuovere carichi di lavoro e componenti.

::: moniker-end

::: moniker range="vs-2017"

Oltre ad aver semplificato la personalizzazione di Visual Studio in base alle attività da eseguire, è stata semplificata anche la modifica di Visual Studio. Per eseguire questa operazione, avviare il nuovo programma di installazione di Visual Studio e apportare le modifiche necessarie.

::: moniker-end

Ecco come fare.

## <a name="modify-workloads"></a>Modificare i carichi di lavoro

 I carichi di lavoro contengono le funzionalità necessarie per il linguaggio di programmazione o la piattaforma in uso. Usare i carichi di lavoro per modificare Visual Studio in modo che supporti il lavoro da eseguire quando desiderato.

>[!IMPORTANT]
>Per installare, aggiornare o modificare Visual Studio, è necessario accedere con un account con autorizzazioni amministrative. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).

>[!TIP]
> La procedura seguente presuppone una connessione a Internet. Per altre informazioni su come modificare un'[installazione offline](create-an-offline-installation-of-visual-studio.md) di Visual Studio creata in precedenza, vedere la pagina [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md).

::: moniker range="vs-2017"

1. Individuare il programma di installazione di Visual Studio all'interno del computer in uso.

     Ad esempio, in un computer che esegue Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

     ![Programma di installazione di Visual Studio](media/vs2017-locate-the-visual-studio-installer.PNG "Individuare il programma di installazione di Microsoft Visual Studio")

     >[!NOTE]
     >In alcuni computer il programma di installazione di Visual Studio potrebbe trovarsi sotto la lettera **"M"** come **Microsoft Visual Studio: programma di installazione**.<br/><br/> In alternativa, è possibile trovare il programma di installazione di Visual Studio nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Fare clic o toccare per avviare il programma di installazione e selezionare **Modifica**.

     ![Avviare o modificare Visual Studio](media/modify-visual-studio.png "Modificare Visual Studio 2017")

     Se è presente un aggiornamento in sospeso, il pulsante Modifica si trova in una posizione diversa. In questo modo è possibile modificare Visual Studio senza aggiornarlo, se si preferisce. Fare clic su **Altro** e scegliere **Modifica**.

     ![Aggiornare o modificare Visual Studio](media/modify-or-update-visual-studio.png "Aggiornare o modificare Visual Studio 2017")

1. Nella schermata **Carichi di lavoro** selezionare o deselezionare i carichi di lavoro da installare o disinstallare.

    ![Finestra di dialogo di installazione di Visual Studio 2017](media/vs2017-modify-workloads.PNG "Scegliere un carico di lavoro in Visual Studio 2017")

1. Scegliere nuovamente **Modifica**.

1. Dopo aver installato i carichi di lavoro e i componenti nuovi, scegliere **Avvia**.

::: moniker-end

::: moniker range="vs-2019"

1. Individuare il programma di installazione di Visual Studio all'interno del computer in uso.

     Ad esempio, in un computer che esegue Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

     ![Aprire il programma di installazione di Visual Studio da Windows](media/vs-2019/vs-installer-windows-start.png "Aprire il programma di installazione di Visual Studio")

     > [!NOTE]
     > È anche possibile trovare il programma di installazione di Visual Studio nella posizione seguente:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata e quindi scegliere **Modifica**.

     ![Aggiornare o modificare Visual Studio](media/vs-2019/vs-installer-modify.png "Aggiornare o modificare Visual Studio 2019")

1. Nella scheda **Carichi di lavoro** selezionare o deselezionare i carichi di lavoro da installare o disinstallare.

    ![Finestra di dialogo di installazione di Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Scegliere un carico di lavoro in Visual Studio 2019")

1. Scegliere se accettare l'opzione predefinita **Installa durante il download** o selezionare l'opzione **Scarica tutto, quindi installa**.

    ![Opzioni di installazione di Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Scegliere se eseguire l'installazione durante il download o se eseguire prima il download e quindi l'installazione")

    L'opzione "Scarica tutto, quindi installa" è utile se si preferisce scaricare prima tutto il software e quindi installarlo in un secondo momento.

1. Scegliere **Modifica**.

1. Dopo aver installato i carichi di lavoro e i componenti nuovi, scegliere **Avvia** dal programma di installazione di Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Modificare i singoli componenti

Se si preferisce non installare carichi di lavoro per personalizzare l'installazione di Visual Studio, scegliere la scheda **Singoli componenti** dal programma di installazione di Visual Studio, selezionare i componenti da installare e seguire le istruzioni visualizzate.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Aggiornare Visual Studio](update-visual-studio.md)
* [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aggiornare Visual Studio secondo una baseline di manutenzione](update-servicing-baseline.md)
* [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
