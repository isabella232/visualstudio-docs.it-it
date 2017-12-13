---
title: Visual Studio Tools per Unity - Procedura dettagliata di Azure - Preparazione | Microsoft Docs
ms.custom: 
ms.date: 10/19/2017
ms.reviewer: crdun
ms.suite: 
ms.technology: tgt-pltfrm-cross-plat
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: B921C2AC-B5D6-4B24-918E-511F83D57275
author: dantogno
ms.author: v-davian
manager: crdun
ms.openlocfilehash: 92f85e39d0f643e896457cae48ab10aa0446dfcd
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="prepare-the-development-environment"></a>Preparare l'ambiente di sviluppo

Per usare di Azure Mobile Client SDK in Unity è necessario soddisfare alcuni requisiti.

## <a name="download-and-install-unity-2017"></a>Scaricare e installare Unity 2017

È necessario usare Unity 2017.1 o versione successiva. La procedura dettagliata funziona con tutti i piani di Unity, incluso il piano Personal gratuito. Scaricare Unity dal sito Web all'indirizzo https://store.unity.com/.

## <a name="download-and-install-visual-studio-2017"></a>Scaricare e installare Visual Studio 2017

La procedura dettagliata richiede Visual Studio 2017 15.3 o versione successiva, con il carico di lavoro Sviluppo di giochi con Unity. La procedura dettagliata funziona con tutte le edizioni di Visual Studio 2017, inclusa l'edizione Community gratuita.

1. Scaricare Visual Studio 2017 dal sito Web all'indirizzo https://www.visualstudio.com/.

2. Installare Visual Studio 2017 e assicurarsi che il carico di lavoro **Sviluppo di giochi con Unity** sia abilitato.

 ![Selezionare il carico di lavoro Unity](media/vstu_azure-prepare-dev-environment-image0.png)

 > [!NOTE]
 > Se Visual Studio 2017 è già installato, è possibile visualizzare e modificare i carichi di lavoro tramite l'esecuzione del programma di installazione di Visual Studio.

## <a name="create-a-new-3d-unity-project"></a>Creare un nuovo progetto Unity 3D

Avviare Unity e creare un nuovo progetto 3D.

![Creare un nuovo progetto Unity](media/vstu_azure-prepare-dev-environment-image1.png)

## <a name="set-the-script-editor-to-visual-studio-preview-2017"></a>Impostare l'editor di script su Visual Studio Preview 2017

È possibile che Visual Studio 2017 sia già impostato come editor di script esterno di Unity, ma è importante assicurarsi che sia selezionata la versione 15.3 Preview.

1. Dal menu **Edit** (Modifica) di Unity scegliere **Edit > Preferences...** (Modifica > Preferenze...).

  ![Aprire il menu Preferences (Preferenze)](media/vstu_azure-prepare-dev-environment-image1.2.png)

2. Quando viene visualizzata la finestra Preferences (Preferenze) di Unity, selezionare la scheda **External Tools** (Strumenti esterni) sul lato sinistro.

3. Nel menu a discesa **External Script Editor** (Editor di script esterno) selezionare **Visual Studio 2017**.

  ![Impostare l'editor di script esterno](media/vstu_azure-prepare-dev-environment-image3.png)

## <a name="change-the-unity-scripting-runtime-to-net-46"></a>Modificare il runtime di scripting di Unity in .NET 4.6
Perché la procedura dettagliata possa usare Azure Mobile Client SDK e le relative dipendenze, è necessario .NET 4.6.

1. Dal menu **File** di Unity scegliere **File > Build Settings...** (File > Impostazioni di compilazione...).

  ![Aprire le impostazioni di compilazione](media/vstu_azure-prepare-dev-environment-image4.png)

2. Fare clic sul pulsante **Player Settings...**  (Impostazioni del giocatore...).

  ![Aprire le impostazioni del giocatore](media/vstu_azure-prepare-dev-environment-image5.png)

3. Le impostazioni del giocatore vengono visualizzate all'interno della finestra Inspector (Controllo) di Unity. Sotto l'intestazione **Configuration** (Configurazione) fare clic sull'elenco a discesa **Scripting Runtime Version** (Versione runtime di scripting) e selezionare **Experimental (.NET 4.6 Equivalent)** (Sperimentale (equivalente a .NET 4.6)). Verrà visualizzata una finestra di dialogo con le richiesta di riavviare Unity. Selezionare **Restart** (Riavvia).

  ![Selezionare .NET 4.6](media/vstu_azure-prepare-dev-environment-image6.png)

## <a name="add-a-reference-to-systemnethttpdll"></a>Aggiungere un riferimento a System.Net.Http.dll

Il runtime di scripting equivalente a .NET 4.6 di Unity consente di usare il pacchetto System.Net.Http, richiesto da Azure Mobile Client SDK. Il file DLL è incluso in Unity. Per usarlo, tuttavia, è necessario aggiungere un riferimento a questo file.

1. Nella finestra Project (Progetto) dell'editor di Unity **fare clic con il pulsante destro del mouse** sulla cartella **Assets** e selezionare **Mostra in Esplora risorse**.

  ![Visualizzare la cartella Assets in Esplora risorse](media/vstu_azure-prepare-dev-environment-image7.png)

2. Nella finestra di Esplora risorse visualizzata fare doppio clic sulla directory **Assets** per aprirla.

3. All'interno della directory Assets **fare clic con il pulsante destro del mouse** e selezionare **Nuovo > Documento di testo**.

4. Aprire il nuovo documento di testo in un editor di testo e aggiungere la riga:`-r:System.Net.Http.dll`

5. Salvare il documento e chiuderlo.

4. Rinominare il nuovo documento di testo in "**mcs.rsp**" e assicurarsi di eliminare l'estensione txt.

  * Se le estensioni dei file sono nascoste, è necessario modificare le opzioni di visualizzazione della cartella per visualizzarle.
  * Aprire il menu Start e digitare "opzioni cartella" per la ricerca. Selezionare "**Opzioni Esplora file**".
  * Selezionare la scheda **Visualizzazione** e nelle impostazioni avanzate assicurarsi che la casella di controllo "**Nascondi estensioni per i tipi di file conosciuti**" sia deselezionata.

    ![Visualizzare la cartella Assets in Esplora risorse](media/vstu_azure-prepare-dev-environment-image8.png)

Al termine di questa procedura è presente un file denominato **mcs.rsp** con la riga `r:System.Net.Http.dll` nella directory **Assets** radice del progetto Unity.

>[!NOTE]
> La funzionalità di riferimento richiede Visual Studio Tools per Unity 3.3 o versione successiva, già presente nel carico di lavoro Visual Studio 15.3+ Unity. Se questo passaggio non riesce, assicurarsi che sia installata la versione corretta di Visual Studio Tools per Unity.

## <a name="add-the-newtonsoftjson-nuget-package-to-your-project"></a>Aggiungere il pacchetto NuGet Newtonsoft.Json al progetto

Azure Mobile Client SDK richiede il pacchetto Newtonsoft.Json. Unity tuttavia non supporta NuGet. Se si apre un progetto Unity in Visual Studio e si aggiunge un pacchetto con NuGet, Unity lo cancella alla successiva apertura del progetto nell'editor di Unity. È tuttavia possibile aggiungere pacchetti NuGet a un progetto Unity manualmente.

1. Nella directory Assets del progetto Unity creare una nuova cartella denominata "**NuGet Packages**" (Pacchetti NuGet). Questo vale solo per le organizzazioni.

2. Passare al sito Web all'indirizzo https://www.nuget.org/packages/Newtonsoft.Json/ e fare clic sul pulsante **Manual Download** (Download manuale). Scaricare il file con estensione nupkg.

  ![Visualizzare la cartella Assets in Esplora risorse](media/vstu_azure-prepare-dev-environment-image9.png)

3. Individuare il file appena scaricato e modificarne l'estensione da nupkg a **zip**. In questo modo è possibile visualizzare ed estrarre i file inclusi in modo analogo a qualsiasi altro file zip.

4. Aprire o estrarre la directory del file zip e passare a **\lib\net45**.

5. Copiare il file **Newtonsoft.Json.dll** nella directory **Assets\NuGet Packages** del progetto Unity.

## <a name="add-the-azure-mobile-client-sdk-nuget-package-to-your-project"></a>Aggiungere il pacchetto NuGet di Azure Mobile Client SDK al progetto

Azure Mobile Client SDK contiene alcune funzioni che semplificano la lettura e la scrittura nelle tabelle semplici di Azure.

1. Passare al sito Web all'indirizzo https://www.nuget.org/packages/Microsoft.Azure.Mobile.Client/ e fare clic sul pulsante **Manual Download** (Download manuale). Scaricare il file con estensione nupkg.

2. Individuare il file appena scaricato e modificarne l'estensione da nupkg a **zip**. In questo modo è possibile visualizzare ed estrarre i file inclusi in modo analogo a qualsiasi altro file zip.

3. Aprire o estrarre la directory del file zip e passare a **\lib\net45**.

4. Copiare il file **Microsoft.Azure.Mobile.Client.dll** nella directory **Assets\NuGet Packages** del progetto Unity.

>[!WARNING]
> Al termine di questa procedura, assicurarsi di riavviare Unity e Visual Studio. In caso contrario, IntelliSense potrebbe non riconoscere i pacchetti appena aggiunti.

## <a name="conclusion"></a>Conclusione

Dopo l'esecuzione di questi passaggi, il progetto Unity è configurato per l'uso di Azure Mobile Client SDK. Per testare l'ambiente di sviluppo, è possibile creare un nuovo script C# nel progetto Unity, aprirlo in Visual Studio e digitare le istruzioni using seguenti nella parte superiore:
```
using System.Net.Http;
using Newtonsoft.Json;
using Microsoft.WindowsAzure.MobileServices;
```

Se IntelliSense rileva queste istruzioni using, la configurazione è stata completata correttamente. In caso di errori o se IntelliSense non riconosce questi pacchetti, provare a riavviare Unity e Visual Studio. Se il problema persiste, rivedere i passaggi precedenti.

## <a name="next-step"></a>Passaggio successivo

* [Creare classi di modelli di dati](visual-studio-tools-for-unity-azure-data.md)
