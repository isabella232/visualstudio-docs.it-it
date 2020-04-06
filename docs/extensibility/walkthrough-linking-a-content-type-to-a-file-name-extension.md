---
title: "Procedura dettagliata: collegamento di un tipo di contenuto a un'estensione di file Documenti Microsoft"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 328be013b5d522938cd7450fc53d4866c632abb3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697074"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di fileWalkthrough: Link a content type to a file name extension
È possibile definire un tipo di contenuto personalizzato e collegarvi un'estensione di file utilizzando le estensioni MEF (Managed Extensibility Framework) dell'editor. In alcuni casi, l'estensione del nome file è già definita da un servizio di linguaggio. Tuttavia, per utilizzarlo con MEF, è comunque necessario collegarlo a un tipo di contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto VSIX di C. (Nella finestra di dialogo **Nuovo progetto,** selezionare **Visual Cè / Extensibility**, quindi **Progetto VSIX**. Denominare `ContentTypeTest`la soluzione .

2. Nel file **source.extension.vsixmanifest** passare alla scheda **Asset** e impostare il campo **Type** su **Microsoft.VisualStudio.MefComponent**, il campo **Source** su **Un progetto nella soluzione corrente**e il campo **Progetto** sul nome del progetto.

## <a name="define-the-content-type"></a>Definire il tipo di contenuto

1. Aggiungere un file di classe e assegnargli il nome `FileAndContentTypes`.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    1. System.ComponentModel.Composition

    2. Microsoft.VisualStudio.Text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. Aggiungere le `using` direttive seguenti.

    ```csharp
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio.Text.Classification;
    using Microsoft.VisualStudio.Utilities;

    ```

4. Dichiarare una classe statica che contiene le definizioni.

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {. . .}
    ```

5. In questa classe, <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> esportare un denominato "hid" e dichiarare la relativa definizione di base come "text".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
        [Export]
        [Name("hid")]
        [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;
    }
    ```

## <a name="link-a-file-name-extension-to-a-content-type"></a>Collegare un'estensione di file a un tipo di contenuto

- Per eseguire il mapping di questo tipo <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> di contenuto a un'estensione di file, esportare un oggetto con estensione *.hid* e il tipo di contenuto "hid".

    ```csharp
    internal static class FileAndContentTypeDefinitions
    {
         [Export]
         [Name("hid")]
         [BaseDefinition("text")]
        internal static ContentTypeDefinition hidingContentTypeDefinition;

         [Export]
         [FileExtension(".hid")]
         [ContentType("hid")]
        internal static FileExtensionToContentTypeDefinition hiddenFileExtensionDefinition;
    }
    ```

## <a name="add-the-content-type-to-an-editor-export"></a>Aggiungere il tipo di contenuto a un editor di esportazione

1. Creare un'estensione dell'editor. Ad esempio, potete usare l'estensione del glifo del margine descritta in [Procedura dettagliata: Creare un glifo](../extensibility/walkthrough-creating-a-margin-glyph.md)di margine.

2. Aggiungere la classe definita in questa procedura.

3. Quando si esporta la classe <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di estensione, aggiungervi un tipo "hid".

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Vedere anche
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
