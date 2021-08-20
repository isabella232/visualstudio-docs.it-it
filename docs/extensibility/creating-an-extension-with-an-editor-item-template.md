---
title: Creazione di un'estensione con un modello di elemento dell'editor | Microsoft Docs
description: Informazioni su come usare i modelli di elemento in Visual Studio SDK per creare estensioni dell'editor di base che aggiungono classificatori, aree di controllo e margini all'editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 120497d5329122dd5dfb4f8afd659cd518eba9f8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122111957"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Creare un'estensione con un modello di elemento dell'editor
È possibile usare i modelli di elemento inclusi in Visual Studio SDK per creare estensioni dell'editor di base che aggiungono classificatori, aree di controllo e margini all'editor. I modelli di elemento dell'editor sono disponibili per i progetti Visual C# o Visual Basic VSIX.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-classifier-extension"></a>Creare un'estensione del classificatore
 Il modello di elemento Editor Classifier crea un classificatore dell'editor che colora il testo appropriato (in questo caso tutto) in qualsiasi file di testo.

1. Nella finestra **di dialogo Nuovo Project** espandere Visual **C#** o **Visual Basic** e quindi fare clic su **Estendibilità**. Nel riquadro **Modelli** selezionare **VSIX Project**. Nella casella **Nome** digitare `TestClassifier`. Fare clic su **OK**.

2. Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento**. Passare al nodo **estendibilità** di Visual C# e selezionare **Classificatore editor**. Lasciare il nome file predefinito (*EditorClassifier1.cs*).

3. Sono disponibili quattro file di codice, come indicato di seguito:

    - *EditorClassifier1.cs* contiene la `EditorClassifier1` classe .

    - *EditorClassifier1ClassificationDefinition.cs* contiene la `EditorClassifier1ClassificationDefinition` classe .

    - *EditorClassifier1Format.cs* contiene la `EditorClassifier1Format`  classe .

    - *EditorClassifier1Provider.cs* contiene la `EditorClassifier1Provider` classe .

4. Compilare il progetto e avviare il debug. Viene visualizzata l'Visual Studio sperimentale di .

     Se si apre un file di testo, tutto il testo viene sottolineato su uno sfondo violaceo.

## <a name="create-a-text-relative-adornment-extension"></a>Creare un'estensione dell'area di controllo relativa al testo
 Il modello Area di controllo testo dell'editor crea un'area di controllo relativa al testo che decora tutte le istanze del carattere di testo "a" usando una casella con un contorno rosso e uno sfondo blu. È relativo al testo perché la casella sovrappone sempre i caratteri "a", anche quando vengono spostati o riformattati.

1. Nella finestra **di dialogo Nuovo Project** espandere Visual **C#** o **Visual Basic** e quindi fare clic su **Estendibilità**. Nel riquadro **Modelli** selezionare **VSIX Project**. Nella casella **Nome** digitare `TestAdornment`. Fare clic su **OK**.

2. Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento**. Passare al nodo  Estendibilità di Visual C# e selezionare Area di **controllo testo editor**. Lasciare il nome file predefinito (*TextAdornment1.cs/vb*).

3. Esistono due file di codice, come indicato di seguito:

    - *TextAdornment1.cs* contiene la `TextAdornment1` classe .

    - *TextAdornment1TextViewCreationListener.cs* contiene la `TextAdornment1TextViewCreationListener` classe .

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si apre un file di testo, tutti i caratteri "a" nel testo vengono delineati in rosso su uno sfondo blu.

## <a name="create-a-viewport-relative-adornment-extension"></a>Creare un'estensione dell'area di controllo relativa al viewport
 Il modello Adornment editor Viewport crea un'area di controllo relativa al viewport che aggiunge una casella viola con un contorno rosso nell'angolo superiore destro del riquadro di visualizzazione.

> [!NOTE]
> Il **viewport** è l'area della visualizzazione di testo attualmente visualizzata.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Per creare un'estensione dell'area di controllo del viewport usando il modello Area di controllo del viewport dell'editor

1. Nella finestra **di dialogo Nuovo Project** espandere Visual **C#** o **Visual Basic** e quindi fare clic su **Estendibilità**. Nel riquadro **Modelli** selezionare **VSIX Project**. Nella casella **Nome** digitare `ViewportAdornment`. Fare clic su **OK**.

2. Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento**. Passare al nodo **Extensibility** di Visual C# e selezionare **Editor Viewport Adornment (Adornment riquadro di visualizzazione editor).** Lasciare il nome file predefinito (*ViewportAdornment1.cs/vb*).

3. Esistono due file di codice, come indicato di seguito:

    - *ViewportAdornment1.cs* contiene la `ViewportAdornment1` classe .

    - *ViewportAdornment1TextViewCreationListener.cs* contiene la `ViewportAdornment1TextViewCreationListener` classe

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si crea un nuovo file di testo, nell'angolo superiore destro del viewport viene visualizzata una casella viola con un contorno rosso.

## <a name="create-a-margin-extension"></a>Creare un'estensione del margine
 Il modello Margine editor crea un margine verde che viene visualizzato insieme alle parole **Hello world!* sotto la barra di scorrimento orizzontale.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Per creare un'estensione del margine usando il modello Margine editor

1. Nella finestra **di dialogo Nuovo Project** espandere Visual **C#** o **Visual Basic** e quindi fare clic su **Estendibilità**. Nel riquadro **Modelli** selezionare **VSIX Project**. Nella casella **Nome** digitare `MarginExtension`. Fare clic su **OK**.

2. Nella finestra **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi**  >  **nuovo elemento**. Passare al nodo **estendibilità** di Visual C# e selezionare **Margine editor**. Lasciare il nome file predefinito (EditorMargin1.cs/vb).

3. Esistono due file di codice, come indicato di seguito:

    - *EditorMargin1.cs* contiene la `EditorMargin1` classe .

    - *EditorMargin1Factory.cs* contiene la `EditorMargin1Factory` classe .

4. Compilare questo progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si apre un file di testo, sotto la barra di scorrimento orizzontale viene visualizzato un margine verde con le parole **Hello EditorMargin1.**

## <a name="see-also"></a>Vedi anche
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
