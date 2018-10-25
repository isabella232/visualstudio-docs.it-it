---
title: 'Procedura dettagliata: Debug di un modello di testo che accede a un modello | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: af46a7fe-6b98-4d3d-b816-0bbf8e81e220
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: ca80111415c869543297ed24707ae27f0490f07b
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924889"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Procedura dettagliata: debug di un modello di testo che accede a un modello
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando si modificano o si aggiungono i modelli di testo in una soluzione di linguaggio specifico di dominio, è possibile ricevere errori quando il motore di trasformazione del modello al codice sorgente oppure durante la compilazione del codice generato. La procedura riportata di seguito vengono illustrate alcune delle operazioni che è possibile eseguire per eseguire il debug di un modello di testo.  
  
> [!NOTE]
>  Per altre informazioni sul testo modelli in generale, vedere [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md). Per altre informazioni sul debug di modelli di testo, vedere [procedura dettagliata: debug di un modello di testo](http://msdn.microsoft.com/library/5c3fd3b7-c110-4e86-a22f-d5756be6b94f).  
  
## <a name="creating-a-domain-specific-language-solution"></a>Creazione di una soluzione Domain-Specific Language  
 In questa procedura, si crea una soluzione di linguaggio specifico di dominio che ha le caratteristiche seguenti:  
  
- Nome: DebuggingTestLanguage  
  
- Modello di soluzione: linguaggio minimo  
  
- Estensione di file:. ddd  
  
- Nome della società: Fabrikam  
  
  Per altre informazioni sulla creazione di una soluzione domain-specific language, vedere [procedura: creare una soluzione di linguaggio specifico di dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).  
  
## <a name="creating-a-text-template"></a>Creazione di un modello di testo  
 Aggiungere un modello di testo alla soluzione.  
  
#### <a name="to-create-a-text-template"></a>Per creare un modello di testo  
  
1.  Compilare la soluzione e avviarne l'esecuzione nel debugger. (Nel **compilare** menu, fare clic su **Ricompila soluzione**e quindi sul **Debug** dal menu fare clic su **Avvia debug**.) Una nuova istanza di Visual Studio apre il progetto di debug.  
  
2.  Aggiungere un file di testo denominato `DebugTest.tt` al progetto di debug.  
  
3.  Assicurarsi che il **Custom Tool** di DebugTest.tt è impostata su `TextTemplatingFileGenerator`.  
  
## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Le direttive che accedono a un modello da un modello di testo di debug  
 Prima di un modello è possibile accedere dalle istruzioni e le espressioni in un modello di testo, è necessario chiamare un processore di direttiva generato. La chiamata al processore di direttiva generato rende le classi nel modello disponibile al codice del modello di testo come proprietà. Per altre informazioni, vedere [l'accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md).  
  
 Nelle procedure seguenti, si eseguirà il debug di un nome di direttiva non corretto e un nome di proprietà non è corretta.  
  
#### <a name="to-debug-an-incorrect-directive-name"></a>Eseguire il debug di un nome di direttiva non corretto  
  
1.  Sostituire il codice in DebugTest.tt con il codice seguente:  
  
    > [!NOTE]
    >  Il codice contiene un errore. L'errore che è stato introdotto per eseguirne il debug.  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ modelRoot processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  Nelle **Esplora soluzioni**, fare doppio clic su DebugTest.tt e quindi fare clic su **Esegui strumento personalizzato**.  
  
     Il **elenco errori** finestra viene visualizzato questo errore:  
  
     **Il processore denominato 'DebuggingTestLanguageDirectiveProcessor' non supporta la direttiva denominata 'dell'elemento modelRoot'. La trasformazione non verrà eseguita.**  
  
     In questo caso, la chiamata di direttiva contiene un nome di direttiva non corretto. È stato specificato `modelRoot` come il nome della direttiva, ma il nome della direttiva corretto `DebuggingTestLanguage`.  
  
3.  Fare doppio clic su errore nel **elenco errori** finestra per passare al codice.  
  
4.  Per correggere il codice, modificare il nome della direttiva da `DebuggingTestLanguage`.  
  
     La modifica viene evidenziata.  
  
    ```csharp  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
    ```vb  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>  
    ```  
  
5.  Nelle **Esplora soluzioni**, fare doppio clic su DebugTest.tt e quindi fare clic su **Esegui strumento personalizzato**.  
  
     A questo punto il sistema consente di trasformare il modello di testo e genera il corrispondente file di output. Gli eventuali errori in non verrà visualizzato il **elenco errori** finestra.  
  
#### <a name="to-debug-an-incorrect-property-name"></a>Eseguire il debug di un nome di proprietà non è corretta  
  
1.  Sostituire il codice in DebugTest.tt con il codice seguente:  
  
    > [!NOTE]
    >  Il codice contiene un errore. L'errore che è stato introdotto per eseguirne il debug.  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.ExampleModel #>  
    <#  
    foreach (ExampleElement element in this.ExampleModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.ExampleModel #>  
    <#  
    For Each element as ExampleElement in Me.ExampleModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
2.  Nel **Esplora soluzioni**, fare doppio clic su DebugTest.tt e quindi fare clic su **Esegui strumento personalizzato**.  
  
     Il **elenco errori** finestra viene visualizzato uno di questi errori:  
  
     (C#)  
  
     **Compilazione della trasformazione: Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation' non contiene una definizione per 'ExampleModel'**  
  
     (Visual Basic)  
  
     **Compilazione della trasformazione: 'ExampleModel' non è un membro di ' Microsoft.VisualStudio.TextTemplating\<GUID >. GeneratedTextTransformation'.**  
  
     In questo caso, il codice del modello di testo contiene un nome di proprietà non è corretta. È stato specificato `ExampleModel` sotto il nome della proprietà, ma la proprietà corretta è nome `LibraryModel`. È possibile trovare il nome della proprietà corretta nel fornisce parametro, come illustrato nel codice seguente:  
  
    ```  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
    ```  
  
3.  Fare doppio clic su errore nella finestra Elenco errori per passare al codice.  
  
4.  Per correggere il codice, modificare il nome della proprietà `LibraryModel` nel codice del modello di testo.  
  
     Le modifiche sono evidenziate.  
  
    ```csharp  
    <#@ template language="C#" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= this.LibraryModel #>  
    <#  
    foreach (ExampleElement element in this.LibraryModel.Elements)   
    {   
    #>   
        Element: <#= element.Name #>  
    <#   
    }  
    #>  
    ```  
  
    ```vb  
    <#@ template language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation"#>  
    <#@ output extension=".txt" #>  
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>  
  
    Model: <#= Me.LibraryModel #>  
    <#  
    For Each element as ExampleElement in Me.LibraryModel.Elements  
    #>   
        Element: <#= element.Name #>  
    <#   
    Next  
    #>  
    ```  
  
5.  Nelle **Esplora soluzioni**, fare doppio clic su DebugTest.tt e quindi fare clic su **Esegui strumento personalizzato**.  
  
     A questo punto il sistema consente di trasformare il modello di testo e genera il corrispondente file di output. Gli eventuali errori in non verrà visualizzato il **elenco errori** finestra.



