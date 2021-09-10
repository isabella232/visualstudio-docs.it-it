---
title: Uso di Visual Studio per Mac Tools per Unity
description: Questa guida spiega come usare l'estensione di Visual Studio per Mac Tools per Unity
author: therealjohn
ms.author: johmil
ms.date: 07/17/2017
ms.assetid: 83FDD7A3-5D16-4B4B-9080-078E3FB5C623
ms.openlocfilehash: d4df59273db1fab8492b36e87e48e0e770072f17
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123961881"
---
# <a name="using-visual-studio-for-mac-tools-for-unity"></a>Uso di Visual Studio per Mac Tools per Unity

Questa sezione illustra come usare le funzionalità per l'integrazione e la produttività di Visual Studio per Mac Tools per Unity e come usare il debugger di Visual Studio per Mac per lo sviluppo di Unity.

## <a name="opening-unity-scripts-in-visual-studio-for-mac"></a>Apertura di script Unity in Visual Studio per Mac

Dopo che Visual Studio per Mac è [impostato come editor di script esterno per Unity](setup-vsmac-tools-unity.md#configure-unity-for-use-with-visual-studio-for-mac), l'apertura di qualsiasi script dall'editor di Unity causa automaticamente l'avvio o il passaggio a Visual Studio per Mac, dove viene aperto lo script scelto.

In alternativa, Visual Studio per Mac può essere aperto senza aprire alcuno script nell'editor standard selezionando **Open C# Project (Apri progetto C#)** dal menu **Assets** in Unity.

![Open C# project (Apri progetto C#)](media/using-vsmac-tools-unity-image1.png)

## <a name="unity-documentation-access"></a>Accesso della documentazione di Unity

Visual Studio per Mac Tools per Unity include un collegamento per accedere alla documentazione dell'API Unity. Per accedere alla documentazione dell'API Unity da Visual Studio per Mac, posizionare il cursore sull'API Unity per cui si desiderano informazioni e premere **command ⌘ + ‘**.

## <a name="intellisense-for-unity-messages"></a>IntelliSense per messaggi di Unity
Il motore Unity trasmette i messaggi agli script MonoBehaviour, consentendo agli sviluppatori di scrivere codice che reagisce a messaggi come OnMouseDown, OnTriggerEnter e così via. Poiché non si tratta di metodi virtuali nella classe MonoBehaviour di base, alcuni ID, ad esempio MonoDevelop, non dispongono della funzionalità di completamento del codice per i messaggi Unity.

Tuttavia, Visual Studio per Mac Tools per Unity estende la propria funzionalità IntelliSense ai messaggi Unity. Ciò semplifica l'implementazione di messaggi Unity negli script MonoBehaviour e assiste nell'apprendimento dell'API Unity. Per usare IntelliSense per i messaggi Unity:

1. Posizionare il cursore su una nuova riga nel corpo di una classe che deriva da MonoBehaviour.

2. Iniziare digitando il nome di un messaggio Unity, ad esempio `OnTriggerEnter`.

3. Dopo che le lettere "**ont**" sono state digitate, viene visualizzato un elenco di suggerimenti di IntelliSense.

   ![Using IntelliSense](media/using-vsmac-tools-unity-image2.png)

4. La selezione nell'elenco può essere modificata in tre modi:

   * Con le frecce **su** e **giù**.

   * Facendo clic con il mouse sull'elemento desiderato.

   * Continuando a digitare il nome dell'elemento desiderato.

5. IntelliSense può inserire il messaggio di Unity selezionato, includendo gli eventuali parametri necessari:

   * Premendo **Tab**.

   * Premendo **Return**.

   * Facendo doppio clic sull'elemento selezionato.

   ![Inserire un messaggio Unity da IntelliSense](media/using-vsmac-tools-unity-image3.png)

## <a name="adding-new-unity-files-and-folders"></a>Aggiunta di nuovi file e cartelle di Unity

Sebbene sia sempre possibile aggiungere nuovi file a un progetto Unity nell'editor di Unity, Visual Studio per Mac consente di creare agevolmente nuovi script, shader e cartelle di Unity dall'interno di Visual Studio.

### <a name="add-a-new-c-monobehaviour-script"></a>Aggiungere un nuovo script C# MonoBehaviour

Per aggiungere un nuovo script C# MonoBehaviour, **fare clic con il pulsante destro del mouse sulla cartella Assets** o su una delle relative sottodirectory nel riquadro Soluzione e selezionare **Aggiungi > Nuovo MonoBehaviour**.

![Aggiungere un nuovo MonoBehaviour](media/using-vsmac-tools-unity-image4.png)

### <a name="add-a-new-unity-shader"></a>Aggiungere un nuovo shader Unity

Per aggiungere un nuovo shader Unity, fare clic con il pulsante destro del mouse sulla cartella **Assets** o su una sottodirectory nel riquadro della soluzione e scegliere Aggiungi > **Nuovo shader**.

### <a name="add-a-new-folder"></a>Aggiungere una nuova cartella

Per aggiungere una nuova cartella, **fare clic con il pulsante destro del mouse sulla cartella Assets** o su una sottodirectory nel riquadro Soluzione e selezionare **Aggiungi > Nuova cartella**.

Queste aggiunte vengono riflesse nella finestra del progetto dell'editor di Unity.

### <a name="to-rename-a-file-or-folder"></a>Per rinominare un file o una cartella
**Fare clic con il pulsante destro del mouse** sull'elemento da rinominare nel riquadro Soluzione e selezionare **Rinomina...**.

> [!NOTE]
> Se è presente un nuovo progetto Unity senza script e la cartella Assets non viene visualizzata nel riquadro Soluzione in Visual Studio per Mac, aggiungere uno script C# iniziale nell'editor di Unity.

## <a name="unity-debugging"></a>Debug di Unity

È possibile eseguire il debug dei progetti Unity con Visual Studio per Mac.

### <a name="start-debugging"></a>Consente di iniziare il debug

Per avviare il debug:

1. Connettere Visual Studio a Unity facendo clic sul pulsante **Riproduci** o digitare **Command + Return**, oppure **F5**.

   ![Fare clic su Riproduci in Visual Studio](media/using-vsmac-tools-unity-image5.png)

2. Passare a Unity e fare clic sul pulsante **Riproduci** per eseguire il gioco nell'editor.

   ![Fare clic su Riproduci in Unity](media/using-vsmac-tools-unity-image6.png)

3. Quando il gioco è in esecuzione nell'editor di Unity mentre è connesso a Visual Studio, qualsiasi punto di interruzione incontrato causa la sospensione dell'esecuzione del gioco e la visualizzazione della riga di codice dove il gioco ha incontrato il punto di interruzione in Visual Studio per Mac.

### <a name="stop-debugging"></a>Arrestare l'esecuzione del debug

Per arrestare il debug:

1. Fare clic sul pulsante **Interrompi** in Visual Studio per Mac oppure premere **Maiusc + Command + Return**.

   ![Fare clic su Interrompi in Visual Studio](media/using-vsmac-tools-unity-image7.png)

Per ulteriori informazioni sul debug in Visual Studio per Mac, vedere [Uso del debugger](debugging.md).
