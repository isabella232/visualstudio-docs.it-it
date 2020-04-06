---
title: Introduzione al modello di progetto VSIX Documenti Microsoft
ms.date: 3/16/2019
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 773e9e6891599cd9672888d0521e94891e0d9f41
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711238"
---
# <a name="get-started-with-the-vsix-project-template"></a>Introduzione al modello di progetto VSIXGet started with the VSIX Project template

È possibile usare il modello di progetto VSIX per creare un'estensione o per creare un pacchetto di un'estensione esistente per la distribuzione. Il modello di progetto VSIX dispone di entrambe le versioni di Visual Basic e Visual C, e viene installato come parte di Visual Studio SDK.

 Il modello di progetto VSIX è costituito solo da un file *source.extension.vsixmanifest,* che contiene informazioni sull'estensione e le risorse fornite.

 Per trovare il modello di progetto VSIX, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Distribuire un modello di progetto personalizzato usando il modello di progetto VSIXDeploy a Custom Project Template using the VSIX Project template

 The following steps show how to use the VSIX project to package a project template that you can share with other developers or upload to the Visual Studio Gallery.

1. Creare un modello di progetto.

    1. Aprire il progetto da cui creare un modello. Questo progetto può essere di qualsiasi tipo di progetto.

    2. Nel menu **Progetto** scegliere**Esporta modello**. Completare i passaggi della procedura guidata.

         Un file *con estensione zip* viene creato in *%USERPROFILE% .\\*

2. Creare un progetto VSIX vuoto.

     Selezionare **File** > **nuovo** > **progetto**. Nella casella di ricerca, digitare "vsix" e selezionare la versione **c'è** o **Visual Basic** del **progetto VSIX**.

3. Aggiungere il file *.zip* al progetto. Impostare la relativa proprietà `Copy Always`Copia nella directory di **output** su .

4. In **Esplora soluzioni**fare doppio clic sul file *source.extension.vsixmanifest* per aprirlo in **Progettazione manifesto VSIX**, quindi apportare le modifiche seguenti:

    - Impostare il campo **Nome prodotto** su Modello **di progetto**personale .

    - Impostare il campo **ID prodotto** su **MyProjectTemplate - 1**.

    - Impostare il campo **Autore su** **Fabrikam**.

    - Impostare il campo **Descrizione** su Modello di **progetto**personale .

    - Nella sezione **Assets** aggiungere un tipo **Microsoft.VisualStudio.ProjectTemplate** e impostarne il percorso sul nome del file *con estensione zip.*

5. Salvare e chiudere il file *source.extension.vsixmanifest.*

6. Compilare il progetto.

7. Nella directory di output fare doppio clic sul file *VSIX.*

8. Viene visualizzata una finestra di messaggio **del programma di installazione VSIX.** Seguire le istruzioni per installare l'estensione.

9. Chiudere e riaprire Visual Studio.

::: moniker range="vs-2017"

10. Selezionare **Estensioni e aggiornamenti** (dal menu **Strumenti)** e selezionare la categoria **Modelli.** Una delle estensioni disponibili deve essere **My Project Template**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Selezionare **Gestisci estensioni** (nel menu **Estensioni)** e selezionare la categoria **Modelli.** Una delle estensioni disponibili deve essere **My Project Template**.

::: moniker-end

11. Il nuovo modello di progetto viene visualizzato nella finestra di dialogo **Nuovo progetto** nella stessa posizione del modello di progetto originale. Ad esempio, se è stato creato un modello denominato **Console VB** da un'applicazione console di Visual Basic, **Console VB** viene visualizzato nello stesso riquadro del modello Applicazione **console** di Visual Basic.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Per specificare il percorso del modello nella finestra di dialogo Nuovo progetto

1. Le cartelle dei modelli si trovano nelle directory , Percorso di installazione di *Visual Studio, Common7, IDE, ProjectTemplates* e Percorso di installazione di *Visual Studio.* I nomi delle sezioni di primo livello nella finestra di dialogo **Nuovo progetto** non corrispondono esattamente ai nomi delle cartelle dei modelli. In caso di differenze, utilizzare il nome della cartella del modello.

    Modificare l'estensione del file *VSIX* *in .zip*, quindi aprire il file.

2. Creare una nuova cartella con lo stesso nome della sezione della finestra di dialogo **Nuovo progetto** in cui dovrebbe essere visualizzato il modello.

3. Se il modello deve essere visualizzato in una sottosezione, creare una sottocartella con lo stesso nome.

4. Spostare il file *.zip* del modello nella nuova cartella.

5. Modificare l'estensione *.zip* in *.vsix*.

6. Aprire il manifesto VSIX.

7. Nel manifesto VSIX aggiornare il percorso **Asset** del modello in modo che punti alla radice dell'albero di directory che contiene il file di modello. Se, ad esempio, il modello si trova in *,* il riferimento deve puntare a *.*
