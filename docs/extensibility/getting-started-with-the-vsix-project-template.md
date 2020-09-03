---
title: Introduzione con il modello di progetto VSIX | Microsoft Docs
ms.date: 3/16/2019
ms.topic: how-to
helpviewer_keywords:
- Visual Studio SDK, VSIX project template
ms.assetid: 89fac33e-9380-4723-9b45-048a6e16f0ed
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 18ca9672b22120718f63638d8668812d0e42e41f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85905876"
---
# <a name="get-started-with-the-vsix-project-template"></a>Introduzione al modello di progetto VSIX

È possibile usare il modello di progetto VSIX per creare un'estensione o per comprimere un'estensione esistente per la distribuzione. Il modello di progetto VSIX ha versioni sia Visual Basic che Visual C# e viene installato come parte di Visual Studio SDK.

 Il modello di progetto VSIX è costituito solo da un file *source. Extension. vsixmanifest* , che contiene informazioni sull'estensione e sugli asset che fornisce.

 Per trovare il modello di progetto VSIX, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="deploy-a-custom-project-template-using-the-vsix-project-template"></a>Distribuire un modello di progetto personalizzato usando il modello di progetto VSIX

 I passaggi seguenti illustrano come usare il progetto VSIX per creare un pacchetto di un modello di progetto che è possibile condividere con altri sviluppatori o caricare in Visual Studio Gallery.

1. Creare un modello di progetto.

    1. Aprire il progetto da cui creare un modello. Questo progetto può essere di qualsiasi tipo di progetto.

    2. Nel menu **Progetto** scegliere**Esporta modello**. Completare i passaggi della procedura guidata.

         Viene creato un file con *estensione zip* nei *modelli \\ esportati%UserProfile%\My Documenti\Visual Studio {Version} \My*.

2. Creare un progetto VSIX vuoto.

     Selezionare **File** > **New** (Nuovo)  > **Project** (Progetto). Nella casella di ricerca digitare "VSIX" e selezionare la versione **C#** o **Visual Basic** del **progetto VSIX**.

3. Aggiungere il file *zip* al progetto. Impostare la proprietà **copia nella directory di output** su `Copy Always` .

4. In **Esplora soluzioni**fare doppio clic sul file *source. Extension. vsixmanifest* per aprirlo nella finestra di **progettazione del manifesto VSIX**, quindi apportare le modifiche seguenti:

    - Impostare il campo **Product Name** sul **modello di progetto**.

    - Impostare il campo **ID prodotto** su **MyProjectTemplate-1**.

    - Impostare il campo **autore** su **Fabrikam**.

    - Impostare il campo **Description** sul **modello di progetto**.

    - Nella sezione **Asset** aggiungere un tipo **Microsoft. VisualStudio. ProjectTemplate** e impostare il relativo percorso sul nome del file con *estensione zip* .

5. Salvare e chiudere il file *source. Extension. vsixmanifest* .

6. Compilare il progetto.

7. Nella directory di output fare doppio clic sul file *VSIX* .

8. Viene visualizzata una finestra di messaggio del **programma di installazione VSIX** . Seguire le istruzioni per installare l'estensione.

9. Chiudere e riaprire Visual Studio.

::: moniker range="vs-2017"

10. Selezionare **estensioni e aggiornamenti** (dal menu **strumenti** ) e selezionare la categoria **modelli** . Una delle estensioni disponibili dovrebbe essere il **modello di progetto**.

::: moniker-end

::: moniker range=">=vs-2019"

10. Selezionare **Gestisci estensioni** (dal menu **estensioni** ) e selezionare la categoria **modelli** . Una delle estensioni disponibili dovrebbe essere il **modello di progetto**.

::: moniker-end

11. Il nuovo modello di progetto verrà visualizzato nella finestra di dialogo **nuovo progetto** nella stessa posizione del modello di progetto originale. Se, ad esempio, è stato creato un modello denominato **console VB** da un'applicazione console Visual Basic, la **console VB** viene visualizzata nello stesso riquadro del modello **applicazione console** Visual Basic.

### <a name="to-specify-the-location-of-the-template-in-the-new-project-dialog-box"></a>Per specificare il percorso del modello nella finestra di dialogo nuovo progetto

1. Le cartelle dei modelli si trovano nelle directory *{percorso di installazione di Visual Studio} \Common7\IDE\ProjectTemplates* e *{percorso di installazione di Visual Studio} \Common7\IDE\ItemTemplates* . I nomi delle sezioni di primo livello nella finestra di dialogo **nuovo progetto** non corrispondono esattamente ai nomi delle cartelle dei modelli. Dove si differenziano, usare il nome della cartella del modello.

    Modificare l'estensione del file *VSIX* in *zip*, quindi aprire il file.

2. Creare una nuova cartella con lo stesso nome della sezione della finestra di dialogo **nuovo progetto** in cui deve essere visualizzato il modello.

3. Se il modello deve essere visualizzato in una sottosezione, creare una sottocartella con lo stesso nome.

4. Spostare il file con *estensione zip* del modello nella nuova cartella.

5. Modificare l'estensione *zip* in *. vsix*.

6. Aprire il manifesto VSIX.

7. Nel manifesto VSIX aggiornare il percorso dell' **Asset** del modello in modo che punti alla radice dell'albero di directory che contiene il file modello. Se, ad esempio, il modello è in *\CSharp\Windows*, il riferimento deve puntare a *\CSharp*.
