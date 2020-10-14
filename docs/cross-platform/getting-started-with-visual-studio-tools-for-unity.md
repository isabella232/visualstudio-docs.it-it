---
title: Introduzione a Visual Studio Tools per Unity | Microsoft Docs
description: Inizia a usare Visual Studio Tools per Unity. Installare Visual Studio, configurare Unity per l'uso con Visual Studio e ottenere informazioni sul supporto per le versioni precedenti.
ms.custom: ''
ms.date: 05/11/2020
ms.technology: vs-unity-tools
ms.topic: how-to
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: indiesaudi
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 223458a448a4b32c3e9480f7189d5dc636ce8375
ms.sourcegitcommit: 01c1b040b12d9d43e3e8ccadee20d6282154faad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/14/2020
ms.locfileid: "92039451"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Introduzione a Visual Studio Tools per Unity

## <a name="install-visual-studio"></a>Installare Visual Studio

### <a name="unity-bundled-installation"></a>Installazione di Unity in bundle

A partire da Unity 2018.1, Visual Studio è l'editor di script C# predefinito per Unity ed è incluso in Unity Download Assistant e nello strumento di installazione di Unity Hub.

- Scaricare Unity da [store.unity.com](https://store.unity.com/).

Durante l'installazione, assicurarsi che Visual Studio sia selezionato nell'elenco dei componenti da installare con Unity:

#### <a name="unity-hub"></a>Unity Hub

:::moniker range="vs-2017"
![Installazione di Unity Hub](media/vs-2017/vstu-unity-hub.png)
:::moniker-end
:::moniker range=">=vs-2019"
![Installazione di Unity Hub](media/vs-2019/vstu-unity-hub.png)
:::moniker-end

:::moniker range="vs-2017"

#### <a name="unity-download-assistant"></a>Unity Download Assistant

![Installazione di Unity Download Assistant](media/vs-2017/vstu-download-assistant.png)

La versione di Visual Studio disponibile con l'installazione di Unity potrebbe non essere la più recente. Se viene richiesto di installare Visual Studio 2017, è consigliabile installare manualmente una versione più recente di Visual Studio.
:::moniker-end

### <a name="manual-installation"></a>Installazione manuale

Se Visual Studio è già installato o si preferisce installare manualmente, eseguire il programma di installazione di Visual Studio.

1. [Scaricare il programma di installazione di Visual Studio](../install/install-visual-studio.md), oppure aprirlo se è già installato.

1. Fare clic su **Modifica** (se già installato) o **Installa** (per le nuove installazioni) per la versione desiderata di Visual Studio.

1. Nella scheda **Carichi di lavoro**, scorrere fino alla sezione **Dispositivi mobili e giochi** e selezionare il carico di lavoro **Sviluppo di giochi con Unity**.

   :::moniker range="vs-2017"
   ![Carico di lavoro Unity](media/vs-2017/vstu-unity-workload.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Carico di lavoro Unity](media/vs-2019/vstu-unity-workload.png)
   :::moniker-end

1. Fare clic su **Modifica** (se già installato) o su **Installa** (per le nuove installazioni) nell'angolo inferiore destro della finestra del programma di installazione.

#### <a name="check-for-updates-to-visual-studio"></a>Controllare la disponibilità di aggiornamenti per Visual Studio

Si consiglia di verificare la disponibilità di aggiornamenti all'interno di Visual Studio per assicurarsi di avere accesso agli strumenti e alle funzionalità più recenti. Il progetto Unity non verrà interrotta.

- [Aggiornare Visual Studio](../install/update-visual-studio.md)

## <a name="configure-unity-for-use-with-visual-studio"></a>Configurare Unity per l'uso con Visual Studio

A partire da Unity 2018.1, Visual Studio deve essere l'editor di script esterno predefinito in Unity. È possibile confermare questa impostazione o modificare l'editor di script esterno a una versione specifica di Visual Studio:

1. Selezionare **Preferences** dal menu **Edit**.

   :::moniker range="vs-2017"
   ![Selezionare Preferences](media/vs-2017/vstu-unity-preferences.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Selezionare Preferences](media/vs-2019/vstu-unity-preferences.png)
   :::moniker-end

2. Nella finestra di dialogo Preferences selezionare la scheda **External Tools**.

3. Dall'elenco a discesa **External Script Editor** scegliere Visual Studio, se elencato, altrimenti selezionare **Browse**.

   :::moniker range="vs-2017"
   ![Selezionare Visual Studio](media/vs-2017/vstu-unity-external-tools.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Selezionare Visual Studio](media/vs-2019/vstu-unity-external-tools.png)
   :::moniker-end

4. Se è stato selezionato **Browse**, aprire la directory **Common7/IDE** all'interno della directory di installazione di Visual Studio e selezionare **devenv.exe**. Fare quindi clic su **Apri**.

   :::moniker range="vs-2017"
   ![Selezionare Open](media/vs-2017/vstu-browse-for-application.png)
   :::moniker-end
   :::moniker range=">=vs-2019"
   ![Selezionare Open](media/vs-2019/vstu-browse-for-application.png)
   :::moniker-end

5. Dopo aver selezionato Visual Studio nell'elenco **External Script Editor**, verificare che la casella di controllo **Editor Attaching** sia selezionata.

6. Chiudere la finestra di dialogo **Preferences** (Preferenze) per completare il processo di configurazione.

## <a name="support-for-older-versions"></a>Supporto per versioni precedenti

Scaricare e installare Visual Studio Tools per Unity da Visual Studio Marketplace. È necessario installare il pacchetto corretto per la versione di Visual Studio usata.

- Per Visual Studio 2015 Community, Visual Studio 2015 Professional o Enterprise di Visual Studio 2015:

   [Scaricare Visual Studio 2015 Tools per Unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools per Unity richiede Unity 5.2 e versioni successive e una versione di Visual Studio che supporti le estensioni, come Visual Studio Community, Professional, Premium o Enterprise. Per verificare che Visual Studio Tools per Unity sia abilitato nella versione di Unity installata, selezionare **About Unity (Informazioni su Unity)** dalla menu della **Guida in linea** e cercare il testo "Microsoft Visual Studio Tools for Unity enabled" nella parte inferiore sinistra della finestra di dialogo.
> ![About Unity](media/vs-2019/vstu-about-unity.png)

## <a name="next-steps"></a>Passaggi successivi

 Per informazioni sull'uso e sul debug di un progetto Unity in Visual Studio, vedere [Visual Studio Tools per Unity](../cross-platform/using-visual-studio-tools-for-unity.md).
