---
title: Creazione di un'estensione con un modello di elemento dell'editor | Microsoft Docs
description: Informazioni su come usare i modelli di elemento in Visual Studio SDK per creare estensioni dell'editor di base che aggiungono classificatori, aree di strumenti e margini all'editor.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e6264cb35e404d69900094513875fc7b79310a4d
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94973735"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Creare un'estensione con un modello di elemento dell'editor
È possibile usare i modelli di elemento inclusi in Visual Studio SDK per creare estensioni dell'editor di base che aggiungono classificatori, aree di visualizzazione e margini all'editor. I modelli di elemento dell'editor sono disponibili per i progetti Visual C# o VSIX Visual Basic.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Creare un'estensione di classificazione
 Il modello di elemento di classificazione Editor crea un classificatore editor che colora il testo appropriato (in questo caso, tutto) in qualsiasi file di testo.

1. Nella finestra di dialogo **nuovo progetto** espandere **Visual C#** o **Visual Basic** e quindi fare clic su **estensibilità**. Nel riquadro **modelli** selezionare **progetto VSIX**. Nella casella **Nome** digitare `TestClassifier`. Fare clic su **OK**.

2. Nella **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Passare al nodo **estensibilità** di Visual C# e selezionare **classificatore editor**. Lasciare il nome file predefinito (*EditorClassifier1.cs*).

3. Sono disponibili quattro file di codice, come indicato di seguito:

    - *EditorClassifier1.cs* contiene la `EditorClassifier1` classe.

    - *EditorClassifier1ClassificationDefinition.cs* contiene la `EditorClassifier1ClassificationDefinition` classe.

    - *EditorClassifier1Format.cs* contiene la `EditorClassifier1Format`  classe.

    - *EditorClassifier1Provider.cs* contiene la `EditorClassifier1Provider` classe.

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.

     Se si apre un file di testo, tutto il testo viene sottolineato a fronte di uno sfondo viola.

## <a name="create-a-text-relative-adornment-extension"></a>Creare un'estensione per l'area di strumenti relativa al testo
 Il modello di controllo dell'area di testo dell'editor crea un'area di controllo relativa al testo che decora tutte le istanze del carattere di testo "a" utilizzando una casella con un contorno rosso e uno sfondo blu. È relativo al testo perché la casella sovrappone sempre i caratteri "a", anche quando vengono spostati o riformattati.

1. Nella finestra di dialogo **nuovo progetto** espandere **Visual C#** o **Visual Basic** e quindi fare clic su **estensibilità**. Nel riquadro **modelli** selezionare **progetto VSIX**. Nella casella **Nome** digitare `TestAdornment`. Fare clic su **OK**.

2. Nella **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Passare al nodo **estensibilità** di Visual C# e selezionare l'area di **testo dell'editor**. Lasciare il nome file predefinito (*TextAdornment1.cs/vb*).

3. Sono disponibili due file di codice, come indicato di seguito:

    - *TextAdornment1.cs* contiene la `TextAdornment1` classe.

    - *TextAdornment1TextViewCreationListener.cs* contiene la `TextAdornment1TextViewCreationListener` classe.

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si apre un file di testo, tutti i caratteri "a" nel testo vengono delineati in rosso rispetto a uno sfondo blu.

## <a name="create-a-viewport-relative-adornment-extension"></a>Creare un'estensione di area di visualizzazione relativa del viewport
 Il modello di adorning del viewport dell'editor crea un'area di disegno relativa al viewport che aggiunge una casella viola con un contorno rosso all'angolo superiore destro del viewport.

> [!NOTE]
> Il **viewport** è l'area della visualizzazione di testo attualmente visualizzata.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Per creare un'estensione di area di visualizzazione del viewport usando il modello di area di visualizzazione dell'editor

1. Nella finestra di dialogo **nuovo progetto** espandere **Visual C#** o **Visual Basic** e quindi fare clic su **estensibilità**. Nel riquadro **modelli** selezionare **progetto VSIX**. Nella casella **Nome** digitare `ViewportAdornment`. Fare clic su **OK**.

2. Nella **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Passare al nodo **estensibilità** di Visual C# e selezionare l'area di visualizzazione dell' **Editor**. Lasciare il nome file predefinito (*ViewportAdornment1.cs/vb*).

3. Sono disponibili due file di codice, come indicato di seguito:

    - *ViewportAdornment1.cs* contiene la `ViewportAdornment1` classe.

    - *ViewportAdornment1TextViewCreationListener.cs* contiene la `ViewportAdornment1TextViewCreationListener` classe

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si crea un nuovo file di testo, nell'angolo superiore destro del viewport viene visualizzata una casella viola con un contorno rosso.

## <a name="create-a-margin-extension"></a>Creare un'estensione per i margini
 Il modello di margine dell'editor crea un margine verde che viene visualizzato insieme alle parole **Hello World!* sotto la barra di scorrimento orizzontale.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Per creare un'estensione per i margini usando il modello di margine dell'editor

1. Nella finestra di dialogo **nuovo progetto** espandere **Visual C#** o **Visual Basic** e quindi fare clic su **estensibilità**. Nel riquadro **modelli** selezionare **progetto VSIX**. Nella casella **Nome** digitare `MarginExtension`. Fare clic su **OK**.

2. Nella **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto e scegliere **Aggiungi**  >  **nuovo elemento**. Passare al nodo **estensibilità** di Visual C# e selezionare **Editor Margin**. Lasciare il nome file predefinito (EditorMargin1.cs/vb).

3. Sono disponibili due file di codice, come indicato di seguito:

    - *EditorMargin1.cs* contiene la `EditorMargin1` classe.

    - *EditorMargin1Factory.cs* contiene la `EditorMargin1Factory` classe.

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si apre un file di testo, al di sotto della barra di scorrimento orizzontale viene visualizzato un margine verde con le parole **Hello EditorMargin1** .

## <a name="see-also"></a>Vedere anche
- [Punti di estensione Editor e servizio di linguaggio](../extensibility/language-service-and-editor-extension-points.md)
