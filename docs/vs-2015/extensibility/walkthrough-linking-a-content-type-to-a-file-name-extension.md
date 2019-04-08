---
title: "Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione di File | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link content type to file name extension
ms.assetid: 21ee64ce-9afe-4b08-94a0-8389cc4dc67c
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 182fc9a8ca55dfe4fc54d7e40c8c88f5b1c6c77d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58968297"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile definire il proprio tipo di contenuto e un collegamento un'estensione di file con estensioni dell'editor Managed Extensibility Framework (MEF). In alcuni casi, l'estensione è già stato definito da un servizio di linguaggio; Tuttavia, per usarlo con MEF è comunque necessario collegarlo a un tipo di contenuto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1.  Creare un progetto C# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual C# / Extensibility**, quindi **progetto VSIX**.) Assegnare alla soluzione il nome `ContentTypeTest`.  
  
2.  Nel **vsixmanifest** file, andare alla **asset** e impostare il **tipo** campo **MEFComponent**, il **sorgente** campo **un progetto nella soluzione corrente**e la **progetto** campo per il nome del progetto.  
  
## <a name="defining-the-content-type"></a>Definizione del tipo di contenuto  
  
1.  Aggiungere un file di classe e assegnargli il nome `FileAndContentTypes`.  
  
2.  Aggiungere riferimenti agli assembly riportati di seguito:  
  
    1.  System.ComponentModel.Composition  
  
    2.  Microsoft.VisualStudio.Text.Logic  
  
    3.  Microsoft.VisualStudio.CoreUtility  
  
3.  Aggiungere il codice seguente `using` direttive.  
  
    ```csharp  
    using System.ComponentModel.Composition;  
    using Microsoft.VisualStudio.Text.Classification;  
    using Microsoft.VisualStudio.Utilities;  
  
    ```  
  
4.  Dichiarare una classe statica che contiene le definizioni.  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {. . .}  
    ```  
  
5.  In questa classe, esportare un <xref:Microsoft.VisualStudio.Utilities.ContentTypeDefinition> denominato "nascosta" e dichiarare la definizione di base sia "text".  
  
    ```csharp  
    internal static class FileAndContentTypeDefinitions  
    {  
        [Export]  
        [Name("hid")]  
        [BaseDefinition("text")]  
        internal static ContentTypeDefinition hidingContentTypeDefinition;  
    }  
    ```  
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Collegamento di un'estensione di File a un tipo di contenuto  
  
-   Per eseguire il mapping di questo tipo di contenuto per un'estensione di file, esportare un <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> che ha l'estensione "HID" e il tipo di contenuto "nascosta".  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Aggiungere il tipo di contenuto per un'esportazione dell'Editor  
  
1.  Creare un'estensione dell'editor. Ad esempio, è possibile usare l'estensione di glifo di margine descritto in [procedura dettagliata: Creazione di un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2.  Aggiungere la classe che è definita in questa procedura.  
  
3.  Quando si esporta la classe di estensione, aggiungere un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di tipo "nascosta" ad esso.  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
