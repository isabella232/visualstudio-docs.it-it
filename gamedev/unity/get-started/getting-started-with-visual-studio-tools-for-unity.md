---
title: Introduzione a Visual Studio Tools per Unity | Microsoft Docs
description: Informazioni su come installare e configurare Visual Studio per lo sviluppo di Unity.
ms.custom: ''
ms.date: 07/13/2020
ms.technology: vs-unity-tools
ms.prod: visual-studio-dev16
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: therealjohn
ms.author: johmil
manager: crdun
ms.workload:
- unity
zone_pivot_groups: platform
ms.openlocfilehash: 1f8cbe1629aab6a177a46888fe25cf8e3565d91d
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903753"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Introduzione a Visual Studio e Unity

> [!NOTE]
> Questa guida presuppone che sia già stato installato Unity tramite il programma Hub Unity. Se non si ha familiarità con Unity, è consigliabile visitare Unity Learning e completare l' [esercitazione Introduzione con Unity](https://learn.unity.com/course/getting-started-with-unity) .

## <a name="install-unity-support-for-visual-studio"></a>Installare il supporto Unity per Visual Studio

Visual Studio Tools per Unity è un'estensione gratuita che fornisce supporto per la scrittura e il debug di C# e altro ancora. Per un elenco completo delle estensioni incluse nelle estensioni, vedere la [Panoramica di Tools for Unity](./visual-studio-tools-for-unity.md) .

:::zone pivot="windows"

> [!NOTE]
> Questa guida all'installazione è relativa a Visual Studio. Se si usa Visual Studio Code, vedere la [documentazione relativa allo sviluppo Unity con vs code](https://code.visualstudio.com/docs/other/unity).

1. [Scaricare il programma di installazione di Visual Studio](/visualstudio/docs/install/install-visual-studio.md)oppure eseguirlo se è già installato.
2. Fare clic su **Modifica** (se già installato) o **Installa** (per le nuove installazioni) per la versione desiderata di Visual Studio.
3. Nella scheda **carichi di lavoro** scorrere fino alla sezione **Gaming** e selezionare il carico di lavoro **sviluppo di giochi con Unity** .

    ![Casella del carico di lavoro sviluppo di giochi con Unity nel programma di installazione](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Questa guida all'installazione è per Visual Studio per Mac. Se si usa Visual Studio Code, vedere la [documentazione relativa allo sviluppo Unity con vs code](https://code.visualstudio.com/docs/other/unity).

Tools per Unity è incluso nell'installazione di Visual Studio per Mac e non sono necessari passaggi di installazione distinti. È possibile verificarlo nel menu **Visual Studio per Mac > Extensions > Game Development** . È necessario abilitare **gli strumenti di Visual Studio per Mac per Unity** .

![Visualizzazione di gestione estensioni che Mostra gli strumenti di Visual Studio per Mac per Unity abilitata](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Verificare gli aggiornamenti

È consigliabile mantenere Visual Studio e Visual Studio per Mac aggiornati in modo da ottenere le correzioni di bug, le funzionalità e il supporto Unity più recenti. Non è necessario un aggiornamento delle versioni di Unity.

:::zone pivot="windows"

1. Fare clic sul menu della **guida > Controlla aggiornamenti** .

    ![Menu Verifica disponibilità aggiornamenti in Visual Studio 2019](../media/vs/check-for-updates.png)

2. Se è disponibile un aggiornamento, il Programma di installazione di Visual Studio visualizzerà una nuova versione. Fare clic sul pulsante **Aggiorna**.

:::zone-end
:::zone pivot="macos"

1. Fare clic sul menu **Visual Studio per Mac > Controlla aggiornamenti...** per aprire la finestra di dialogo di **aggiornamento di Visual Studio** .
2. Se è disponibile un aggiornamento, fare clic sul pulsante **Installa** .

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Configurare Unity per l'uso di Visual Studio

Per impostazione predefinita, Unity deve essere già configurato per l'uso di Visual Studio o Visual Studio per Mac come editor di script. È possibile confermare questa operazione o modificare l'editor di script esterno in una versione specifica di Visual Studio dall'editor di Unity.

:::zone pivot="windows"

1. Nell'editor di Unity selezionare il menu **Modifica preferenze >** .
2. Selezionare la scheda **strumenti esterni** sulla sinistra.
3. L'elenco a discesa **editor di script esterno** fornisce un modo per scegliere installazioni diverse di Visual Studio. È anche possibile fare clic su **Sfoglia...** nell'elenco a discesa per aggiungere una versione non in elenco.

    ![Menu di preferenza strumenti esterni nell'editor di Unity in Windows](../media/vs/preferences-external-tools.png)

4. Se è stato selezionato **Browse**, aprire la directory **Common7/IDE** all'interno della directory di installazione di Visual Studio e selezionare **devenv.exe**. Quindi, fare clic su **Apri**.
5. Dopo aver selezionato Visual Studio nell'elenco **External Script Editor**, verificare che la casella di controllo **Editor Attaching** sia selezionata.
6. Chiudere la finestra di dialogo **Preferences** (Preferenze) per completare il processo di configurazione.

:::zone-end
:::zone pivot="macos"

1. Nell'editor di Unity selezionare il menu **unity > Preferences** .
2. Selezionare la scheda **strumenti esterni** sulla sinistra.
3. L'elenco a discesa **editor di script esterno** fornisce un modo per scegliere installazioni diverse di Visual Studio. È anche possibile fare clic su **Sfoglia...** nell'elenco a discesa per aggiungere una versione non in elenco.

    ![Menu di preferenza strumenti esterni nell'editor di Unity in macOS](../media/vsm/preferences-external-tools.png)

4. Chiudere la finestra di dialogo **Preferences** (Preferenze) per completare il processo di configurazione.

:::zone-end

## <a name="next-steps"></a>Passaggi successivi

 Per informazioni su come usare ed eseguire il debug del progetto Unity in Visual Studio, vedere [uso di Visual Studio Tools per Unity](using-visual-studio-tools-for-unity.md).
