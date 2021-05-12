---
title: Introduzione a Visual Studio Tools per Unity | Microsoft Docs
description: Informazioni su come installare e configurare Visual Studio per lo sviluppo di Unity.
ms.custom: ''
ms.date: 01/27/2021
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
ms.openlocfilehash: 791f25b61c86f0115c225d505bdb1edb07869961
ms.sourcegitcommit: 69256dc47489853dc66a037f5b0c1275977540c0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/12/2021
ms.locfileid: "109782608"
---
# <a name="get-started-with-visual-studio-and-unity"></a>Introduzione a Visual Studio e Unity

> [!NOTE]
> Questa guida presuppone che Unity sia già stato installato usando il programma Unity Hub. Se non si ha esperienza con Unity, è consigliabile visitare Unity Learn e completare prima il percorso di apprendimento [di Unity Essentials.](https://learn.unity.com/pathway/unity-essentials)

## <a name="install-unity-support-for-visual-studio"></a>Installare il supporto di Unity per Visual Studio

Visual Studio Tools per Unity è un'estensione gratuita che fornisce supporto per la scrittura e il debug di C# e altro ancora. Per un [elenco completo delle estensioni incluse,](./visual-studio-tools-for-unity.md) vedere la panoramica di Strumenti per Unity.

:::zone pivot="windows"

> [!NOTE]
> Questa guida all'installazione è Visual Studio. Se si usa Visual Studio Code, visitare la documentazione [di Unity Development con VS Code .](https://code.visualstudio.com/docs/other/unity)

1. [Scaricare il Visual Studio o](/visualstudio/install/install-visual-studio.md)eseguirlo se è già installato.
2. Fare clic su **Modifica** (se già installato) o **Installa** (per le nuove installazioni) per la versione desiderata di Visual Studio.
3. Nella scheda **Carichi di lavoro** scorrere fino alla sezione **Giochi** e selezionare il carico di lavoro Sviluppo di giochi **con Unity.**

    ![Casella del carico di lavoro Sviluppo di giochi con Unity nel programma di installazione](../media/vs/unity-workload.png)

:::zone-end
:::zone pivot="macos"

> [!NOTE]
> Questa guida all'installazione è Visual Studio per Mac. Se si usa Visual Studio Code, visitare la documentazione [di Unity Development con VS Code .](https://code.visualstudio.com/docs/other/unity)

Tools for Unity è incluso nell'installazione di Visual Studio per Mac e non sono necessari passaggi di installazione separati. È possibile verificarlo nel menu Visual Studio per Mac > **estensioni > game development.** **Visual Studio per Mac Tools for Unity** deve essere abilitato.

![Visualizzazione di Gestione estensioni che mostra Visual Studio per Mac strumenti per Unity abilitati](../media/vsm/unity-workload.png)

:::zone-end

## <a name="check-for-updates"></a>Verificare gli aggiornamenti

È consigliabile mantenere aggiornati Visual Studio e Visual Studio per Mac in modo da avere le correzioni di bug, le funzionalità e il supporto di Unity più recenti. Questa operazione non richiede un aggiornamento delle versioni di Unity.

:::zone pivot="windows"

1. Fare clic **sul > menu Controlla aggiornamenti** .

    ![Menu Controlla aggiornamenti in Visual Studio 2019](../media/vs/check-for-updates.png)

2. Se è disponibile un aggiornamento, il Programma di installazione di Visual Studio visualizza una nuova versione. Fare clic sul pulsante **Aggiorna**.

:::zone-end
:::zone pivot="macos"

1. Fare clic **Visual Studio per Mac > menu Controlla aggiornamenti per aprire la** finestra Visual Studio di dialogo **Aggiorna.**
2. Se è disponibile un aggiornamento, fare clic sul **pulsante** Installa.

:::zone-end

## <a name="configure-unity-to-use-visual-studio"></a>Configurare Unity per l'uso Visual Studio

Per impostazione predefinita, Unity deve essere già configurato per usare Visual Studio o Visual Studio per Mac come editor di script. È possibile confermarlo o modificare l'editor di script esterno in una versione specifica di Visual Studio dall'editor di Unity.

:::zone pivot="windows"

1. Nell'editor di Unity selezionare il **menu > Preferenze.**
2. Selezionare la **scheda Strumenti** esterni a sinistra.
3. L'elenco a **discesa External Script Editor (Editor** script esterno) consente di scegliere diverse installazioni di Visual Studio. È anche possibile fare clic **su Sfoglia...** nell'elenco a discesa per aggiungere una versione non in elenco.

    ![Menu delle preferenze Strumenti esterni nell'editor di Unity in Windows](../media/vs/preferences-external-tools.png)

4. Se è stato selezionato **Browse**, aprire la directory **Common7/IDE** all'interno della directory di installazione di Visual Studio e selezionare **devenv.exe**. Fare quindi clic su **Apri**.
5. Dopo aver selezionato Visual Studio nell'elenco **External Script Editor**, verificare che la casella di controllo **Editor Attaching** sia selezionata.
6. Chiudere la finestra di dialogo **Preferences** (Preferenze) per completare il processo di configurazione.

:::zone-end
:::zone pivot="macos"

1. Nell'editor di Unity selezionare unity **> menu Preferences (Preferenze).**
2. Selezionare la **scheda Strumenti** esterni a sinistra.
3. L'elenco a **discesa External Script Editor (Editor** script esterno) consente di scegliere diverse installazioni di Visual Studio. È anche possibile fare clic **su Sfoglia...** nell'elenco a discesa per aggiungere una versione non in elenco.

    ![Menu delle preferenze Strumenti esterni nell'editor di Unity in macOS](../media/vsm/preferences-external-tools.png)

4. Chiudere la finestra di dialogo **Preferences** (Preferenze) per completare il processo di configurazione.

:::zone-end

## <a name="next-steps"></a>Passaggi successivi

 Per informazioni su come usare ed eseguire il debug del progetto Unity in Visual Studio, vedere [Uso di Visual Studio Tools per Unity](using-visual-studio-tools-for-unity.md).
