---
title: "Procedura dettagliata: collegamento di un tipo di contenuto a un'estensione di file | Microsoft Docs"
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
ms.openlocfilehash: beae9d0526cb9f2f294f2267a8da52d3ce3d8c08
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202004"
---
# <a name="walkthrough-linking-a-content-type-to-a-file-name-extension"></a>Procedura dettagliata: collegamento di un tipo di contenuto a un'estensione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile definire un tipo di contenuto personalizzato e collegarvi un'estensione di file usando le estensioni dell'editor Managed Extensibility Framework (MEF). In alcuni casi, l'estensione del nome file è già stata definita da un servizio di linguaggio. Tuttavia, per usarlo con MEF è comunque necessario collegarlo a un tipo di contenuto.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-mef-project"></a>Creazione di un progetto MEF  
  
1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `ContentTypeTest` .  
  
2. Nel file **source. Extension. vsixmanifest** passare alla scheda **Asset** e impostare il campo **tipo** su **Microsoft. VisualStudio. MefComponent**, il campo di **origine** su **un progetto nella soluzione corrente**e il campo **progetto** sul nome del progetto.  
  
## <a name="defining-the-content-type"></a>Definizione del tipo di contenuto  
  
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
  
## <a name="linking-a-file-name-extension-to-a-content-type"></a>Collegamento di un'estensione del nome di file a un tipo di contenuto  
  
- Per eseguire il mapping di questo tipo di contenuto a un'estensione di file, esportare un oggetto <xref:Microsoft.VisualStudio.Utilities.FileExtensionToContentTypeDefinition> con l'estensione ". HID" e il tipo di contenuto "HID".  
  
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
  
## <a name="adding-the-content-type-to-an-editor-export"></a>Aggiunta del tipo di contenuto a un'esportazione dell'editor  
  
1. Creare un'estensione dell'editor. Ad esempio, è possibile usare l'estensione del glifo dei margini descritta in [procedura dettagliata: creazione di un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md).  
  
2. Aggiungere la classe definita in questa procedura.  
  
3. Quando si esporta la classe Extension, aggiungerne una <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di tipo "HID".  
  
    ```csharp  
    [Export]  
    [ContentType("hid")]  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Punti di estensione dei servizi di linguaggio e dell'editor](../extensibility/language-service-and-editor-extension-points.md)
