---
title: 'Procedura dettagliata: Personalizzazione della visualizzazione testo | Microsoft Docs'
description: Informazioni su come personalizzare una visualizzazione di testo modificando una delle diverse proprietà nella mappa in formato editor usando questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - customizing the view
ms.assetid: 32d32ac8-22ff-4de7-af69-bd46ec4ad9bf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 493d11fe5c024631bc333a0bea6bd834f54eefccac9e97d24c4d22d16f2de60f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400478"
---
# <a name="walkthrough-customize-the-text-view"></a>Procedura dettagliata: Personalizzare la visualizzazione testo
È possibile personalizzare una visualizzazione di testo modificando una delle proprietà seguenti nella mappa in formato editor:

- Margine indicatore

- Cursore di inserimento

- Sovrascrivi il caret

- Testo selezionato

- Testo selezionato inattivo(ovvero testo selezionato che ha perso lo stato attivo)

- Spazio vuoto visibile

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto VSIX C#. Nella finestra **di dialogo Nuovo Project** selezionare Visual **C# /Extensibility** e quindi **VSIX Project**. Assegnare alla soluzione il nome `ViewPropertyTest` .

2. Aggiungere un modello di elemento Editor Classifier al progetto. Per altre informazioni, vedere [Creare un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Eliminare i file di classe esistenti.

## <a name="define-the-content-type"></a>Definire il tipo di contenuto

1. Aggiungere un file di classe e assegnargli il nome `ViewPropertyModifier`.

2. Aggiungere le direttive `using` seguenti:

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet1":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet1":::

3. Dichiarare una classe denominata `TestViewCreationListener` che eredita da <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener> . Esportare questa classe con gli attributi seguenti:

   - <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> per specificare il tipo di contenuto a cui si applica questo listener.

   - <xref:Microsoft.VisualStudio.Text.Editor.TextViewRoleAttribute> per specificare il ruolo di questo listener.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet2":::

4. In questa classe importare <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMapService> .

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet3":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet3":::

## <a name="change-the-view-properties"></a>Modificare le proprietà della vista

1. Impostare il metodo <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> in modo che le proprietà della vista siano modificate all'apertura della vista. Per apportare la modifica, trovare prima l'elemento corrispondente <xref:System.Windows.ResourceDictionary> all'aspetto della visualizzazione che si vuole trovare. Modificare quindi la proprietà appropriata nel dizionario risorse e impostare le proprietà. Eseguire il batch delle chiamate al metodo chiamando il metodo prima di impostare le proprietà e quindi dopo <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.SetProperties%2A> <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.BeginBatchUpdate%2A> aver impostato le <xref:Microsoft.VisualStudio.Text.Classification.IEditorFormatMap.EndBatchUpdate%2A> proprietà.

    :::code language="csharp" source="../snippets/csharp/VS_Snippets_VSSDK/vssdkviewpropertytest/cs/viewpropertymodifier.cs" id="Snippet4":::
    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VSSDK/vssdkviewpropertytest/vb/viewpropertymodifier.vb" id="Snippet4":::

## <a name="build-and-test-the-code"></a>Compilare e testare il codice

1. Compilare la soluzione.

     Quando si esegue questo progetto nel debugger, viene avviata una seconda istanza di Visual Studio.

2. Creare un file di testo e digitare alcune parole.

    - Il cursore di inserimento deve essere magenta e il cursore di sovrascrittura deve essere turchese.

    - Il margine dell'indicatore (a sinistra della visualizzazione testo) deve essere verde chiaro.

3. Selezionare il testo digitato. Il colore del testo selezionato deve essere rosa chiaro.

4. Mentre il testo è selezionato, fare clic in un punto qualsiasi all'esterno della finestra di testo. Il colore del testo selezionato deve essere rosa scuro.

5. Attivare lo spazio vuoto visibile. Scegliere Avanzate **dal** menu Modifica e **quindi** fare clic su Visualizza **spazio vuoto**. Digitare alcune schede nel testo. Devono essere visualizzate le frecce rosse che rappresentano le schede.

## <a name="see-also"></a>Vedi anche
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
