---
title: Collegare un tipo di contenuto a un'estensione del nome file
description: Per informazioni su come collegare il proprio tipo di contenuto a un'estensione di file, usare l'editor Managed Extensibility Framework estensioni in questa procedura dettagliata.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 990f10fe82b9230c12ba13d736750f2f644c3ee5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105078448"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Procedura dettagliata: collegare un tipo di contenuto a un'estensione di file
È possibile definire un tipo di contenuto personalizzato e collegarvi un'estensione di file usando le estensioni dell'editor Managed Extensibility Framework (MEF). In alcuni casi, l'estensione del nome file è già definita da un servizio di linguaggio. Tuttavia, per usarlo con MEF, è comunque necessario collegarlo a un tipo di contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `ContentTypeTest` .

2. Nel file **source. Extension. vsixmanifest** passare alla scheda **Asset** e impostare il campo **tipo** su **Microsoft. VisualStudio. MefComponent**, il campo di **origine** su **un progetto nella soluzione corrente** e il campo **progetto** sul nome del progetto.

## <a name="define-the-content-type"></a>Definire il tipo di contenuto

1. Aggiungere un file di classe e assegnargli il nome `FileAndContentTypes`.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    1. System.ComponentModel.Composition

    2. Microsoft. VisualStudio. Text. Logic

    3. Microsoft. VisualStudio. CoreUtility

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

5. In questa classe esportare un oggetto <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> denominato "HID" e dichiarare la relativa definizione di base come "testo".

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

- Per eseguire il mapping di questo tipo di contenuto a un'estensione del nome di file, esportare un oggetto <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> con estensione *HID* e il tipo di contenuto "HID".

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

1. Creare un'estensione dell'editor. Ad esempio, è possibile usare l'estensione del glifo dei margini descritta in [procedura dettagliata: creare un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Aggiungere la classe definita in questa procedura.

3. Quando si esporta la classe Extension, aggiungerne una <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di tipo "HID".

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Vedi anche
- [Punti di estensione Editor e servizio di linguaggio](../extensibility/language-service-and-editor-extension-points.md)
