---
title: Attività iniziali con il modello Project VSIX | Microsoft Docs
description: Informazioni su come usare il modello di Project VSIX per creare un'estensione o creare un pacchetto di un'estensione esistente per la distribuzione.
ms.custom: SEO-VS-2020
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d73294c35e71e8684be2f4fbeca98e517385eedd
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122087106"
---
# <a name="get-started-with-the-vsix-project-template"></a>Introduzione al modello di Project VSIX

È possibile usare il modello di Project VSIX per creare un'estensione o creare un pacchetto di un'estensione esistente per la distribuzione. Il modello di Project VSIX ha versioni Visual Basic e Visual C# e viene installato come parte di Visual Studio SDK.

 Il modello di Project VSIX è costituito semplicemente da un file *source.extension.vsixmanifest,* che contiene informazioni sull'estensione e sugli asset in esso disponibili.

 Per trovare il modello di progetto VSIX, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK.](../extensibility/visual-studio-sdk.md)

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Distribuire un modello Project personalizzato usando il modello di Project VSIX

 La procedura seguente illustra come usare il progetto VSIX per creare un pacchetto di un modello di progetto che è possibile condividere con altri sviluppatori o caricare in Visual Studio Gallery.

1. Creare un modello di progetto.

    1. Aprire il progetto da cui creare un modello. Questo progetto può essere di qualsiasi tipo.

    2. Nel menu **Progetto** scegliere **Esporta modello**. Completare i passaggi della procedura guidata.

         Un *.zip* file viene creato in *%USERPROFILE%\Documenti\Visual Studio {version}\My Exported \\ Templates*.

2. Creare un progetto VSIX vuoto.

     Selezionare **File** > **New** (Nuovo)  > **Project** (Progetto). Nella casella di ricerca digitare "vsix" e selezionare la versione **C#** o **Visual Basic** di **VSIX Project**.

3. Aggiungere il file *.zip* al progetto. Impostarne **la proprietà Copia nella directory di** output su `Copy Always` .

4. In **Esplora soluzioni** fare doppio clic sul file *source.extension.vsixmanifest* per aprirlo in Progettazione manifesto **VSIX** e quindi apportare le modifiche seguenti:

    - Impostare il **campo Product Name (Nome** **prodotto) su My Project Template (Modello personalizzato).**

    - Impostare il **campo PRODUCT ID (ID** **prodotto) su MyProjectTemplate - 1**.

    - Impostare il **campo Autore** su **Fabrikam.**

    - Impostare il **campo Descrizione** su **Modello di progetto.**

    - Nella **sezione Assets** aggiungere un tipo **Microsoft.VisualStudio.ProjectTemplate** e impostarne il percorso sul nome *.zip* file.

5. Salvare e chiudere il file *source.extension.vsixmanifest.*

6. Compilare il progetto.

7. Nella directory di output fare doppio clic sul file *con estensione vsix.*

8. Verrà visualizzata la finestra di messaggio Programma di installazione **VSIX.** Seguire le istruzioni per installare l'estensione.

9. Chiudere e riaprire Visual Studio.

::: moniker range="vs-2017"

10. Selezionare **Estensioni e aggiornamenti** (dal menu **Strumenti)** e selezionare la **categoria** Modelli. Una delle estensioni disponibili deve essere **My Project Template.**

::: moniker-end

::: moniker range=">=vs-2019"

10. Selezionare **Gestisci estensioni** (dal menu **Estensioni)** e selezionare la **categoria** Modelli. Una delle estensioni disponibili deve essere **My Project Template.**

::: moniker-end

11. Il nuovo modello di progetto viene visualizzato nella **finestra Project** nuovo progetto nella stessa posizione del modello di progetto originale. Ad esempio, se è stato creato un modello denominato **console VB** da un'applicazione console **Visual Basic,** la console di  VB viene visualizzata nello stesso riquadro del modello Applicazione console Visual Basic.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Per specificare il percorso del modello nella finestra di dialogo Project nuovo modello

1. Le cartelle dei modelli si trovano nelle directory *{Visual Studio Installation Path}\Common7\IDE\ProjectTemplates* e *{Visual Studio Installation Path}\Common7\IDE\ItemTemplates.* I nomi delle sezioni di primo livello nella finestra di **dialogo Project** non corrispondono esattamente ai nomi delle cartelle modello. In caso di differenze, usare il nome della cartella del modello.

    Modificare *l'estensione di* file *vsix.zip* e quindi aprire il file.

2. Creare una nuova cartella con lo stesso nome della sezione della finestra di **dialogo Project** in cui verrà visualizzato il modello.

3. Se il modello deve essere visualizzato in una sottosezione, creare una sottocartella con lo stesso nome.

4. Spostare il modello *.zip* file nella nuova cartella.

5. Modificare *l'estensione.zip* in *.vsix.*

6. Aprire il manifesto VSIX.

7. Nel manifesto VSIX aggiornare il percorso **dell'asset** del modello in modo che punti alla radice dell'albero di directory che contiene il file modello. Ad esempio, se il modello si trova in *\CSharp\Windows*, il riferimento deve puntare a *\CSharp*.
