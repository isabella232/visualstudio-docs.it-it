---
title: "Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di File | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e402979dc5b76b8693a4be7a80a3d5d98f889616
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66320667"
---
# <a name="walkthrough-link-a-content-type-to-a-file-name-extension"></a>Procedura dettagliata: Collegare un tipo di contenuto a un'estensione di file
È possibile definire il proprio tipo di contenuto e un collegamento un'estensione di file tramite le estensioni di editor Managed Extensibility Framework (MEF). In alcuni casi, l'estensione è già definito da un servizio di linguaggio. Tuttavia, per usarlo con MEF, è necessario comunque collegarlo a un tipo di contenuto.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, Visual Studio SDK è non installare dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-mef-project"></a>Creare un progetto MEF

1. Creare un progetto c# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Assegnare alla soluzione il nome `ContentTypeTest`.

2. Nel **vsixmanifest** file, andare alla **asset** e impostare il **tipo** campo **MEFComponent**, il **sorgente** campo **un progetto nella soluzione corrente**e la **progetto** campo per il nome del progetto.

## <a name="define-the-content-type"></a>Definire il tipo di contenuto

1. Aggiungere un file di classe e assegnargli il nome `FileAndContentTypes`.

2. Aggiungere riferimenti agli assembly riportati di seguito:

    1. System.ComponentModel.Composition

    2. Microsoft.VisualStudio.Text.Logic

    3. Microsoft.VisualStudio.CoreUtility

3. Aggiungere il codice seguente `using` direttive.

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

5. In questa classe, esportare un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> denominato "nascosta" e dichiarare la definizione di base sia "text".

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

- Per eseguire il mapping di questo tipo di contenuto per un'estensione di file, esportare un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> che ha l'estensione *HID* e il tipo di contenuto "nascosta".

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

## <a name="add-the-content-type-to-an-editor-export"></a>Aggiungere il tipo di contenuto per un'esportazione dell'editor

1. Creare un'estensione dell'editor. Ad esempio, è possibile usare l'estensione di glifo di margine descritto in [procedura dettagliata: Creare un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md).

2. Aggiungere la classe che è definita in questa procedura.

3. Quando si esporta la classe di estensione, aggiungere un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di tipo "nascosta" ad esso.

    ```csharp
    [Export]
    [ContentType("hid")]
    ```

## <a name="see-also"></a>Vedere anche
- [Punti di estensione del servizio e l'editor di linguaggio](../extensibility/language-service-and-editor-extension-points.md)