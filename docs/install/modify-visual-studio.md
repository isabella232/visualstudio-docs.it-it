---
title: Modificare Visual Studio
titleSuffix: ''
description: Informazioni dettagliate su come modificare Visual Studio.
ms.custom: H1Hack27Feb2017,seodec18
ms.date: 12/19/2019
ms.topic: conceptual
helpviewer_keywords:
- modify Visual Studio
- change visual studio
- changing Visual Studio
- customize Visual Studio
ms.assetid: 3399ea7b-a291-4a9e-80a1-b861a21afa1d
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 554b7a01ee4a7a8834c86c8a2c7e15b9cf331cf5
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75565838"
---
# <a name="modify-visual-studio-by-adding-or-removing-workloads-and-components"></a>Modificare Visual Studio aggiungendo o rimuovendo carichi di lavoro e componenti

::: moniker range="vs-2019"

Visual Studio può essere facilmente modificato in modo da includere solo gli elementi desiderati, quando sono necessari. A tale scopo, aprire il programma di installazione di Visual Studio per aggiungere o rimuovere carichi di lavoro e componenti.

::: moniker-end

::: moniker range="vs-2017"

Oltre ad aver semplificato la personalizzazione di Visual Studio in base alle attività da eseguire, è stata semplificata anche la modifica di Visual Studio. A tale scopo, aprire il nuovo Programma di installazione di Visual Studio e apportare le modifiche desiderate.

::: moniker-end

Ecco come fare.

>[!IMPORTANT]
>Per installare, aggiornare o modificare Visual Studio, è necessario accedere con un account con autorizzazioni amministrative. Per altre informazioni, vedere [Autorizzazioni utente e Visual Studio](../ide/user-permissions-and-visual-studio.md).

>[!NOTE]
> Nelle procedure riportate di seguito si presuppone che si disponga di una connessione Internet.
>
> Per altre informazioni su come modificare un'[installazione offline](create-an-offline-installation-of-visual-studio.md) di Visual Studio creata in precedenza, vedere sia la pagina [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md) che la pagina [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md).

## <a name="open-the-visual-studio-installer"></a>Aprire il Programma di installazione di Visual Studio

::: moniker range="vs-2017"

1. Individuare il programma di installazione di Visual Studio all'interno del computer in uso.

     Ad esempio, in un computer che esegue Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

     ![Programma di installazione di Visual Studio](media/locate-the-visual-studio-installer.png "Individuare il programma di installazione Microsoft Visual Studio")

     >[!TIP]
     >In alcuni computer il programma di installazione di Visual Studio potrebbe trovarsi sotto la lettera **"M"** come **Microsoft Visual Studio: programma di installazione**.<br/><br/> In alternativa, è possibile trovare il programma di installazione di Visual Studio nel percorso seguente: `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

1. Aprire il programma di installazione, quindi scegliere **modifica**.

     ![Avviare o modificare Visual Studio](media/modify-visual-studio.png "Modificare Visual Studio 2017")

     > [!IMPORTANT]
     > Se è presente un aggiornamento in sospeso, il pulsante Modifica si trova in una posizione diversa. In questo modo è possibile modificare Visual Studio senza aggiornarlo, se si preferisce. Fare clic su **Altro** e scegliere **Modifica**.
     >
     > ![Aggiornare o modificare Visual Studio](media/modify-or-update-visual-studio.png "Aggiornare o modificare Visual Studio 2017")

::: moniker-end

::: moniker range="vs-2019"

1. Individuare il programma di installazione di Visual Studio all'interno del computer in uso.

     Ad esempio, in un computer che esegue Windows 10 selezionare **Start** e scorrere fino alla lettera **P** in cui viene visualizzato come **Programma di installazione di Visual Studio**.

     ![Aprire il Programma di installazione di Visual Studio da Windows](media/vs-2019/vs-installer-windows-start.png "Aprire il Programma di installazione di Visual Studio")

     > [!NOTE]
     > È anche possibile trovare il programma di installazione di Visual Studio nella posizione seguente:
     >
     > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

    Prima di continuare, potrebbe essere necessario aggiornare il programma di installazione. In questo caso, seguire i prompt.

1. Nel programma di installazione cercare l'edizione di Visual Studio installata e quindi scegliere **Modifica**.

     ![Aggiornare o modificare Visual Studio](media/vs-2019/vs-installer-modify.png "Aggiornare o modificare Visual Studio 2019")

     > [!IMPORTANT]
     > Se è presente un aggiornamento in sospeso, il pulsante Modifica si trova in una posizione diversa. In questo modo, è possibile modificare Visual Studio senza aggiornarlo, se lo si desidera. Scegliere **altro**e quindi fare clic su **modifica**.
     >
     > ![Aggiornare o modificare Visual Studio](media/vs-2019/modify-update-visual-studio.png "Aggiornare o modificare Visual Studio 2019")

::: moniker-end

## <a name="modify-workloads"></a>Modificare i carichi di lavoro

::: moniker range="vs-2017"

 I [carichi di lavoro](https://visualstudio.microsoft.com/vs/support/selecting-workloads-visual-studio-2017/) contengono le funzionalità necessarie per il linguaggio di programmazione o la piattaforma in uso. Usare i carichi di lavoro per modificare Visual Studio in modo che supporti il lavoro da eseguire quando desiderato.

1. Nella Programma di installazione di Visual Studio scegliere la scheda **carichi di lavoro** e quindi selezionare o deselezionare i carichi di lavoro desiderati.

    ![Finestra di dialogo di installazione di Visual Studio 2017](media/modify-workloads.png "Scegliere un carico di lavoro in Visual Studio 2019")

1. Scegliere se accettare l'opzione predefinita **Installa durante il download** o selezionare l'opzione **Scarica tutto, quindi installa**.

    ![Opzioni di installazione di Visual Studio 2017](media/vs-2019/vs-installer-choose-install-or-download.png "Scegliere di installare durante il download o prima di scaricare e installare in seguito")

    L'opzione "Scarica tutto, quindi installa" è utile se si preferisce scaricare prima tutto il software e quindi installarlo in un secondo momento.

1. Scegliere **Modifica**.

1. Dopo aver installato i nuovi carichi di lavoro, scegliere **Avvia** dal programma di installazione di Visual Studio per aprire Visual Studio.

::: moniker-end

::: moniker range="vs-2019"

 I carichi di lavoro contengono le funzionalità necessarie per il linguaggio di programmazione o la piattaforma in uso. Usare i carichi di lavoro per modificare Visual Studio in modo che supporti il lavoro da eseguire quando desiderato.

1. Nella Programma di installazione di Visual Studio scegliere la scheda carichi di **lavoro** , quindi selezionare o deselezionare i carichi di lavoro desiderati.

    ![Finestra di dialogo di installazione di Visual Studio 2019](media/vs-2019/vs-installer-modify-workloads.png "Scegliere un carico di lavoro in Visual Studio 2019")

1. Scegliere se accettare l'opzione predefinita **Installa durante il download** o selezionare l'opzione **Scarica tutto, quindi installa**.

    ![Opzioni di installazione di Visual Studio 2019](media/vs-2019/vs-installer-choose-install-or-download.png "Scegliere di installare durante il download o prima di scaricare e installare in seguito")

    L'opzione "Scarica tutto, quindi installa" è utile se si preferisce scaricare prima tutto il software e quindi installarlo in un secondo momento.

1. Scegliere **Modifica**.

1. Dopo aver installato i nuovi carichi di lavoro, scegliere **Avvia** dal programma di installazione di Visual Studio per aprire Visual Studio.

::: moniker-end

## <a name="modify-individual-components"></a>Modificare i singoli componenti

Se non si vogliono usare i carichi di lavoro per personalizzare l'installazione di Visual Studio, scegliere la scheda **singoli componenti** nel programma di installazione di Visual Studio, selezionare i componenti desiderati e quindi seguire le istruzioni.

## <a name="modify-language-packs"></a>Modificare i Language Pack

Per impostazione predefinita, il programma di installazione corrisponde alla lingua del sistema operativo quando viene eseguito per la prima volta. Tuttavia, è possibile modificare la lingua quando si desidera. A tale scopo, scegliere la scheda **Language Pack** nella programma di installazione di Visual Studio, selezionare la lingua preferita e quindi seguire le istruzioni.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Vedere anche

* [Elenco degli ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
* [Aggiornare Visual Studio](update-visual-studio.md)
* [Aggiornare un'installazione di rete di Visual Studio](update-a-network-installation-of-visual-studio.md)
* [Aggiornare Visual Studio secondo una baseline di manutenzione](update-servicing-baseline.md)
* [Controllare gli aggiornamenti delle distribuzioni di rete di Visual Studio](controlling-updates-to-visual-studio-deployments.md)
* [Disinstallare Visual Studio](uninstall-visual-studio.md)
