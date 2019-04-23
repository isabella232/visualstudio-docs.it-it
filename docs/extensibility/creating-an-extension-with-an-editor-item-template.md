---
title: Creazione di un'estensione con un modello di elemento dell'Editor | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: fa3b993b-ab95-47fa-a38b-b788f3a5b2d8
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2e87429c38d5b456eca08daa6675edcb0bd3f056
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60079811"
---
# <a name="create-an-extension-with-an-editor-item-template"></a>Creare un'estensione con un modello di elemento dell'editor
È possibile usare i modelli di elementi inclusi in Visual Studio SDK per creare estensioni di editor di base di classificatori, le aree di controllo e i margini all'editor. I modelli di elemento dell'editor sono disponibili per i progetti Visual c# o Visual Basic VSIX.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-classifier-extension"></a>Creare un'estensione di classificazione
 Il modello di elemento di classificatore Editor Crea un classificatore editor che colora il testo appropriato (in questo caso, tutto) in qualsiasi file di testo.

1. Nel **nuovo progetto** finestra di dialogo espandere **Visual c#** oppure **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** riquadro, selezionare **progetto VSIX**. Nella casella **Nome** digitare `TestClassifier`. Fare clic su **OK**.

2. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** > **nuovo elemento**. Passare a Visual c# **estendibilità** nodo e selezionare **classificatore Editor**. Lasciare il nome file predefinito (*EditorClassifier1.cs*).

3. Esistono quattro file di codice, come indicato di seguito:

    - *EditorClassifier1.cs* contiene il `EditorClassifier1` classe.

    - *EditorClassifier1ClassificationDefinition.cs* contiene il `EditorClassifier1ClassificationDefinition` classe.

    - *EditorClassifier1Format.cs* contiene il `EditorClassifier1Format` classe.

    - *EditorClassifier1Provider.cs* contiene il `EditorClassifier1Provider` classe.

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale di Visual Studio.

     Se si apre un file di testo, tutto il testo è sottolineato su uno sfondo scuro.

## <a name="create-a-text-relative-adornment-extension"></a>Creare un'estensione dell'area di controllo relativo al testo
 Il modello di area di controllo Text Editor crea un'area di controllo di testo relativa che decora tutte le istanze dei caratteri del testo "a" tramite una finestra che ha un bordo rosso e uno sfondo blu. È relativo al testo perché la casella sempre le sovrimpressioni 'a' caratteri, anche quando vengono spostati o riformattati.

1. Nel **nuovo progetto** finestra di dialogo espandere **Visual c#** oppure **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** riquadro, selezionare **progetto VSIX**. Nella casella **Nome** digitare `TestAdornment`. Fare clic su **OK**.

2. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** > **nuovo elemento**. Passare a Visual c# **estendibilità** nodo e selezionare **Editor di testo Adornment**. Lasciare il nome file predefinito (*TextAdornment1.cs/vb*).

3. Sono presenti due file di codice, come indicato di seguito:

    - *TextAdornment1.cs* contiene il `TextAdornment1` classe.

    - *TextAdornment1TextViewCreationListener.cs* contiene il `TextAdornment1TextViewCreationListener` classe.

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si apre un file di testo, tutti i "a" caratteri del testo sono evidenziati in rosso su uno sfondo blu.

## <a name="create-a-viewport-relative-adornment-extension"></a>Creare un'estensione dell'area di controllo relativo al viewport
 Il modello di area di controllo del riquadro di visualizzazione dell'Editor crea un'area di controllo relativo al riquadro di visualizzazione che consente di aggiungere una casella scuro con un bordo rosso nell'angolo superiore destro del riquadro di visualizzazione.

> [!NOTE]
>  Il **viewport** è l'area di visualizzazione di testo che è attualmente visualizzata.

### <a name="to-create-a-viewport-adornment-extension-by-using-the-editor-viewport-adornment-template"></a>Per creare un'estensione dell'area di controllo del riquadro di visualizzazione utilizzando il modello di area di controllo del riquadro di visualizzazione dell'Editor

1. Nel **nuovo progetto** finestra di dialogo espandere **Visual c#** oppure **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** riquadro, selezionare **progetto VSIX**. Nella casella **Nome** digitare `ViewportAdornment`. Fare clic su **OK**.

2. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** > **nuovo elemento**. Passare a Visual c# **estendibilità** nodo e selezionare **dell'area di controllo del riquadro di visualizzazione dell'Editor**. Lasciare il nome file predefinito (*ViewportAdornment1.cs/vb*).

3. Sono presenti due file di codice, come indicato di seguito:

    - *ViewportAdornment1.cs* contiene il `ViewportAdornment1` classe.

    - *ViewportAdornment1TextViewCreationListener.cs* contiene il `ViewportAdornment1TextViewCreationListener` classe

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si crea un nuovo file di testo, viene visualizzata una finestra scuro con un bordo rosso nell'angolo in alto a destra del riquadro di visualizzazione.

## <a name="create-a-margin-extension"></a>Creare un'estensione di margine
 Il modello di margine dell'Editor Crea un margine verde che verrà visualizzata insieme alle parole **Hello world!* sotto la barra di scorrimento orizzontale.

### <a name="to-create-a-margin-extension-by-using-the-editor-margin-template"></a>Per creare un'estensione di margine usando il modello di margine dell'Editor

1. Nel **nuovo progetto** finestra di dialogo espandere **Visual c#** oppure **Visual Basic** e quindi fare clic su **estendibilità**. Nel **modelli** riquadro, selezionare **progetto VSIX**. Nella casella **Nome** digitare `MarginExtension`. Fare clic su **OK**.

2. Nel **Esplora soluzioni**, fare doppio clic sul nodo del progetto e selezionare **Add** > **nuovo elemento**. Passare a Visual c# **estendibilità** nodo e selezionare **margine dell'Editor**. Lasciare il nome file predefinito (EditorMargin1.cs/vb).

3. Sono presenti due file di codice, come indicato di seguito:

    - *EditorMargin1.cs* contiene il `EditorMargin1` classe.

    - *EditorMargin1Factory.cs* contiene il `EditorMargin1Factory` classe.

4. Compilare il progetto e avviare il debug. Viene visualizzata l'istanza sperimentale. Se si apre un file di testo, un margine verde con le parole **Hello EditorMargin1** viene visualizzato sotto la barra di scorrimento orizzontale.

## <a name="see-also"></a>Vedere anche
- [Punti di estensione del servizio e l'editor di linguaggio](../extensibility/language-service-and-editor-extension-points.md)
