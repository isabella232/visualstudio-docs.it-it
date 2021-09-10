---
title: Impostare Visual Studio per Mac Tools per Unity
description: Configurazione e installazione degli strumenti Unity per l'uso in Visual Studio per Mac
author: therealjohn
ms.author: johmil
ms.date: 05/25/2018
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.topic: how-to
ms.openlocfilehash: f423b77f8464b05b81be2ff7cdb08a2d8b007e0d
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123961875"
---
# <a name="set-up-visual-studio-for-mac-tools-for-unity"></a>Impostare Visual Studio per Mac Tools per Unity

Questa sezione illustra come iniziare a usare Visual Studio per Mac Tools per Unity.

## <a name="install-visual-studio-for-mac"></a>Installare Visual Studio per Mac

### <a name="unity-bundled-installation"></a>Installazione di Unity in bundle

A partire da Unity 2018.1, Visual Studio per Mac è l'IDE C# predefinito per Unity ed è incluso in Unity Download Assistant e nello strumento di installazione di Unity Hub. Scaricare Unity da [store.unity.com](https://store.unity.com/).

Durante l'installazione, assicurarsi che Visual Studio per Mac sia selezionato nell'elenco dei componenti da installare con Unity:

#### <a name="unity-hub"></a>Unity Hub

![Installazione di Unity Hub](media/setup-vsmac-tools-unity-image7.png)

#### <a name="unity-download-assistant"></a>Unity Download Assistant

![Installazione di Unity Download Assistant](media/setup-vsmac-tools-unity-image8.png)

#### <a name="check-for-updates-to-visual-studio-for-mac"></a>Controllare la disponibilità di aggiornamenti per Visual Studio per Mac

La versione di Visual Studio per Mac disponibile con l'installazione di Unity potrebbe non essere la più recente. È consigliabile verificare la disponibilità di aggiornamenti per assicurarsi di avere accesso agli strumenti e alle funzionalità più recenti.

* [Aggiornamento di Visual Studio per Mac](update.md)

### <a name="manual-installation"></a>Installazione manuale

Se si ha già Unity 5.6.1 o versione successiva, ma non si ha Visual Studio per Mac, è possibile installare Visual Studio per Mac manualmente. Tutte le edizioni di Visual Studio per Mac sono in bundle con Visual Studio per Mac Tools per Unity, inclusa l'edizione gratuita Community:

* Scaricare Visual Studio per Mac da [visualstudio.microsoft.com](https://visualstudio.microsoft.com/).
* Visual Studio per Mac Tools per Unity viene installato automaticamente durante il processo di installazione.
* Per ulteriore assistenza nell'installazione, seguire la procedura riportata nella [Guida all'installazione](./installation.md?view=vsmac-2017&preserve-view=true).

> [!NOTE]
> Visual Studio per Mac Tools per Unity richiede Unity 5.6.1 o versione successiva. Per verificare che Visual Studio Tools per Unity sia abilitato nella versione di Unity installata, selezionare **About Unity (Informazioni su Unity)** dal menu di Unity e cercare il testo "Microsoft Visual Studio Tools for Unity enabled (Microsoft Visual Studio Tools for Unity enabled)" nella parte inferiore sinistra della finestra di dialogo.
>
> ![About Unity](media/setup-vsmac-tools-unity-image3.png)

## <a name="confirm-that-the-visual-studio-for-mac-tools-for-unity-extension-is-enabled"></a>Verificare che l'estensione di Visual Studio per Mac Tools per Unity sia abilitata

L'estensione di Visual Studio per Mac Tools per Unity dovrebbe essere abilitata per impostazione predefinita, tuttavia è possibile verificarlo e controllare il numero della versione installata:

1. Dal menu di Visual Studio scegliere **Estensioni...**.

   ![Selezionare le estensioni](media/setup-vsmac-tools-unity-image1.png)

2. Espandere la sezione Sviluppo di giochi e confermare la voce Visual Studio per Mac Tools per Unity.

   ![Visualizzare la voce di Unity](media/setup-vsmac-tools-unity-image2.png)

## <a name="configure-unity-for-use-with-visual-studio-for-mac"></a>Configurare Unity per l'uso con Visual Studio per Mac

A partire da Unity 2018.1, Visual Studio deve essere l'editor di script esterno predefinito in Unity. È possibile confermare questa impostazione o modificare l'editor di script esterno in Visual Studio:

1. Selezionare **Preferences...** dal menu di Unity.

   ![Selezionare Preferences](media/setup-vsmac-tools-unity-image4.png)

2. Nella finestra di dialogo Preferences selezionare la scheda **External Tools**.

3. Dall'elenco a discesa External Script Editor scegliere **Visual Studio**, se elencato, altrimenti selezionare **Browse... (Sfoglia...)**.

   ![Selezionare Visual Studio](media/setup-vsmac-tools-unity-image5.png)

4. Se si è selezionato **Browse...**, spostarsi sulla directory Applications e selezionare Visual Studio, quindi fare clic su **Open**.

   ![Selezionare Open](media/setup-vsmac-tools-unity-image6.png)

5. Dopo aver selezionato Visual Studio nell'elenco **External Script Editor**, chiudere la finestra di dialogo Preferences per completare il processo di configurazione.