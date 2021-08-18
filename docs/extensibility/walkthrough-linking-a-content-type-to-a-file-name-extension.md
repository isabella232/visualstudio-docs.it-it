---
title: Collegare un tipo di contenuto a un'estensione di file
description: Informazioni su come collegare un tipo di contenuto personalizzato a un'estensione di file usando l'editor Managed Extensibility Framework in questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: d49c7241d952270a7ca394e445ef777189a39b9a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122078531"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file
È possibile definire un tipo di contenuto personalizzato e collegarvi un'estensione di file usando l'editor Managed Extensibility Framework (MEF). In alcuni casi, l'estensione del nome file è già definita da un servizio di linguaggio. Tuttavia, per usarlo con MEF, è comunque necessario collegarlo a un tipo di contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto VSIX C#. Nella finestra **di dialogo Project** nuova versione selezionare Visual **C# /Extensibility**, quindi **VSIX Project**. Assegnare alla soluzione il nome `ContentTypeTest` .

2. Nel  file **source.extension.vsixmanifest** passare alla scheda Asset **e** impostare il campo **Tipo** su **Microsoft.VisualStudio.MefComponent**, il campo Origine su **Un** progetto nella soluzione corrente e il campo **Project** sul nome del progetto.

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

5. In questa classe esportare un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> oggetto denominato "hid" e dichiarare la relativa definizione di base come "text".

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

- Per eseguire il mapping di questo tipo di contenuto a un'estensione di file, esportare un oggetto con estensione hid e il tipo di contenuto <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> "hid". 

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

## <a name="add-the-content-type-to-an-editor-export"></a>Aggiungere il tipo di contenuto a un'esportazione dell'editor

1. Creare un'estensione dell'editor. Ad esempio, è possibile usare l'estensione del glifo del margine descritta in [Procedura dettagliata: Creare un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Aggiungere la classe definita in questa procedura.

3. Quando si esporta la classe di estensione, aggiungervi un di tipo <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> "hid".

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Vedi anche
- [Punti di estensione del servizio di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
