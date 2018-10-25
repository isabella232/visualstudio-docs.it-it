---
title: Introduzione a Visual Studio Tools per Unity | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology: vs-unity-tools
ms.topic: conceptual
ms.assetid: 66b5b4eb-13b5-4071-98d2-87fafa4598a8
author: conceptdev
ms.author: crdun
manager: crdun
ms.workload:
- unity
ms.openlocfilehash: 9d924ee92258e348d5ffee1551fcde7707d711cf
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49855209"
---
# <a name="get-started-with-visual-studio-tools-for-unity"></a>Introduzione a Visual Studio Tools per Unity

## <a name="install-visual-studio"></a>Installare Visual Studio

### <a name="unity-bundled-installation"></a>Installazione di Unity in bundle

A partire da Unity 2018.1, Visual Studio è l'editor di script C# predefinito per Unity ed è incluso in Unity Download Assistant e nello strumento di installazione di Unity Hub.

- Scaricare Unity da [store.unity.com](https://store.unity.com/).

Durante l'installazione, assicurarsi che Visual Studio sia selezionato nell'elenco dei componenti da installare con Unity:

#### <a name="unity-hub"></a>Unity Hub

![Installazione di Unity Hub](media/vstu_unity-hub.png)

#### <a name="unity-download-assistant"></a>Unity Download Assistant

![Installazione di Unity Download Assistant](media/vstu_download-assistant.png)

#### <a name="check-for-updates-to-visual-studio"></a>Controllare la disponibilità di aggiornamenti per Visual Studio

La versione di Visual Studio disponibile con l'installazione di Unity potrebbe non essere la più recente. È consigliabile verificare la disponibilità di aggiornamenti per assicurarsi di avere accesso agli strumenti e alle funzionalità più recenti.

- [Aggiornare Visual Studio](../install/update-visual-studio.md)

### <a name="manual-installation"></a>Installazione manuale

Se si dispone già di Visual Studio 2017 installato, o se si preferisce l'installazione manuale, eseguire il programma di installazione di Visual Studio.

1. [Scaricare il programma di installazione di Visual Studio](/visualstudio/install/install-visual-studio), oppure aprirlo se è già installato.

1. Fare clic su **Modifica** (se già installato) o **Installa** (per le nuove installazioni) per la versione desiderata di Visual Studio.

1. Nella scheda **Carichi di lavoro**, scorrere fino alla sezione **Dispositivi mobili e giochi** e selezionare il carico di lavoro **Sviluppo di giochi con Unity**.

    ![Carico di lavoro Unity](media/vstu_unity-workload.png)

1. Fare clic su **Modifica** (se già installato) o su **Installa** (per le nuove installazioni) nell'angolo inferiore destro della finestra del programma di installazione.

## <a name="configure-unity-for-use-with-visual-studio"></a>Configurare Unity per l'uso con Visual Studio

A partire da Unity 2018.1, Visual Studio deve essere l'editor di script esterno predefinito in Unity. È possibile confermare questa impostazione o modificare l'editor di script esterno a una versione specifica di Visual Studio:

1. Selezionare **Preferences** dal menu **Edit**.

   ![Selezionare Preferences](media/vstu_unity-preferences.png)

2. Nella finestra di dialogo Preferences selezionare la scheda **External Tools**.

3. Dall'elenco a discesa **External Script Editor** scegliere Visual Studio, se elencato, altrimenti selezionare **Browse**.

   ![Selezionare Visual Studio](media/vstu_unity-external-tools.png)

4. Se è stato selezionato **Browse**, aprire la directory **Common7/IDE** all'interno della directory di installazione di Visual Studio e selezionare **devenv.exe**. Fare clic su **Open**.

   ![Selezionare Open](media/vstu_browse-for-application.png)

5. Dopo aver selezionato Visual Studio nell'elenco **External Script Editor**, verificare che la casella di controllo **Editor Attaching** sia selezionata.

6. Chiudere la finestra di dialogo **Preferences** (Preferenze) per completare il processo di configurazione.

## <a name="support-for-older-versions"></a>Supporto per versioni precedenti

 Scaricare e installare Visual Studio Tools per Unity da Visual Studio Marketplace. È necessario installare il pacchetto corretto per la versione di Visual Studio usata.

- Per Visual Studio 2015 Community, Visual Studio 2015 Professional o Enterprise di Visual Studio 2015:

   [Scaricare Visual Studio 2015 Tools per Unity](https://marketplace.visualstudio.com/items?itemName=SebastienLebreton.VisualStudio2015ToolsforUnity)

> [!NOTE]
> Visual Studio Tools per Unity richiede Unity 5.2 e versioni successive e una versione di Visual Studio che supporti le estensioni, come Visual Studio Community, Professional, Premium o Enterprise. Per verificare che Visual Studio Tools per Unity sia abilitato nella versione di Unity installata, selezionare **About Unity (Informazioni su Unity)** dalla menu della **Guida in linea** e cercare il testo "Microsoft Visual Studio Tools for Unity enabled" nella parte inferiore sinistra della finestra di dialogo.
> ![About Unity](media/vstu_about-unity.png)

## <a name="next-steps"></a>Passaggi successivi

 Per informazioni sull'uso e sul debug di un progetto Unity in Visual Studio, vedere [Visual Studio Tools per Unity](../cross-platform/using-visual-studio-tools-for-unity.md).
