---
title: Creazione di un'estensione con un modello di elemento dell'editor Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7ac19d99bf75c79ad011bfd0d5a56ecf3880b100
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739499"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Creare un'estensione con un modello di elemento dell'editorCreate an extension with an editor item template
È possibile usare i modelli di elemento inclusi in Visual Studio SDK per creare estensioni di base dell'editor che aggiungono classificatori, aree di controllo e margini all'editor. I modelli di elemento dell'editor sono disponibili per i progetti VSIX di Visual Co o Visual Basic.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It is included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-classifier-extension"></a>Creare un'estensione classificatoreCreate a classifier extension
 Il modello di elemento Classificatore editor crea un classificatore di editor che colora il testo appropriato (in questo caso, tutto) in qualsiasi file di testo.

1. Nella finestra di dialogo **Nuovo progetto** , espandere **Visual C,** Visual **Basic** e quindi fare clic su **estensibilità**. Nel riquadro **Modelli** selezionare **Progetto VSIX**. Nella casella **Nome** digitare `TestClassifier`. Fare clic su **OK**.

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Andare al nodo **Extensibility** di Visual C, quindi selezionare **Classificatore editor**. Lasciare il nome file predefinito (*EditorClassifier1.cs*).

3. Esistono quattro file di codice, come indicato di seguito:There are four code files, as follows:

    - *EditorClassifier1.cs* contiene `EditorClassifier1` la classe.

    - *EditorClassifier1ClassificationDefinition.cs* contiene `EditorClassifier1ClassificationDefinition` la classe.

    - *EditorClassifier1Format.cs* contiene `EditorClassifier1Format` la classe.

    - *EditorClassifier1Provider.cs* contiene `EditorClassifier1Provider` la classe.

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.The experimental instance of Visual Studio appears.

     Se si apre un file di testo, tutto il testo viene sottolineato su uno sfondo viola.

## <a name="create-a-text-relative-adornment-extension"></a>Creare un'estensione dell'area di controllo relativa al testoCreate a text-relative adornment extension
 Il modello Editor Text Adornment crea un'area di controllo relativa al testo che decora tutte le istanze del carattere di testo 'a' utilizzando una casella con un contorno rosso e uno sfondo blu. È relativo al testo perché la casella si sovrappone sempre ai caratteri 'a', anche quando vengono spostati o riformattati.

1. Nella finestra di dialogo **Nuovo progetto** , espandere **Visual C,** Visual **Basic** e quindi fare clic su **estensibilità**. Nel riquadro **Modelli** selezionare **Progetto VSIX**. Nella casella **Nome** digitare `TestAdornment`. Fare clic su **OK**.

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Andare al nodo **Extensibility** di Visual C, quindi selezionare **Editor Text Adornment**. Lasciare il nome file predefinito (*TextAdornment1.cs/vb*).

3. Esistono due file di codice, come indicato di seguito:There are two code files, as follows:

    - *TextAdornment1.cs* contiene `TextAdornment1` la classe.

    - *TextAdornment1TextViewCreationListener.cs* contiene `TextAdornment1TextViewCreationListener` la classe.

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si apre un file di testo, tutti i caratteri 'a' nel testo vengono evidenziati in rosso su uno sfondo blu.

## <a name="create-a-viewport-relative-adornment-extension"></a>Creare un'estensione dell'area di controllo relativa alla finestraCreate a viewport-relative adornment extension
 Il modello AreaViewport Adornment crea un'area di controllo relativa alla finestra che aggiunge una casella viola con un contorno rosso nell'angolo superiore destro della finestra.

> [!NOTE]
> La **finestra** è l'area della visualizzazione di testo attualmente visualizzata.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Per creare un'estensione dell'area di controllo della finestra utilizzando il modello Area area di visualizzazione area di visualizzazione

1. Nella finestra di dialogo **Nuovo progetto** , espandere **Visual C,** Visual **Basic** e quindi fare clic su **estensibilità**. Nel riquadro **Modelli** selezionare **Progetto VSIX**. Nella casella **Nome** digitare `ViewportAdornment`. Fare clic su **OK**.

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Andare al nodo **Extensibility** di Visual C, quindi selezionare **Editor Viewport Adornment**. Lasciare il nome file predefinito (*ViewportAdornment1.cs/vb*).

3. Esistono due file di codice, come indicato di seguito:There are two code files, as follows:

    - *ViewportAdornment1.cs* contiene `ViewportAdornment1` la classe.

    - *ViewportAdornment1TextViewCreationListener.cs* contiene `ViewportAdornment1TextViewCreationListener` la classe

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si crea un nuovo file di testo, nell'angolo superiore destro della finestra viene visualizzata una casella viola con un contorno rosso.

## <a name="create-a-margin-extension"></a>Creare un'estensione di margine
 Il modello Margine editor crea un margine verde che viene visualizzato insieme alle parole*Hello world!* sotto la barra di scorrimento orizzontale.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Per creare un'estensione margine utilizzando il modello Margine editor

1. Nella finestra di dialogo **Nuovo progetto** , espandere **Visual C,** Visual **Basic** e quindi fare clic su **estensibilità**. Nel riquadro **Modelli** selezionare **Progetto VSIX**. Nella casella **Nome** digitare `MarginExtension`. Fare clic su **OK**.

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse sul nodo del progetto e **scegliere Aggiungi** > **nuovo elemento**. Andare al nodo **Extensibility** di Visual C, quindi selezionare **Margine editor**. Lasciare il nome file predefinito (EditorMargin1.cs/vb).

3. Esistono due file di codice, come indicato di seguito:There are two code files, as follows:

    - *EditorMargin1.cs* contiene `EditorMargin1` la classe.

    - *EditorMargin1Factory.cs* contiene `EditorMargin1Factory` la classe.

4. Compilare questo progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si apre un file di testo, sotto la barra di scorrimento orizzontale viene visualizzato un margine verde con le parole **Hello EditorMargin1.**

## <a name="see-also"></a>Vedere anche
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
