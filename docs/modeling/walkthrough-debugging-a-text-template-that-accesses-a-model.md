---
title: 'Procedura dettagliata: Eseguire il debug di modelli di testo che accedono a un modello'
description: Fornisce informazioni su come eseguire il debug di un modello di testo che accede a un modello.
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: 71c6d4d31144ecbb4873bf39300d4f8756cfe5ab
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122033876"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Procedura dettagliata: debug di un modello di testo che accede a un modello
Quando si modificano o si aggiungono modelli di testo in una soluzione di linguaggio specifico di dominio, è possibile che si otterrà un errore quando il motore trasforma il modello in codice sorgente o quando compila il codice generato. La procedura dettagliata seguente illustra alcune delle operazioni che è possibile eseguire per eseguire il debug di un modello di testo.

> [!NOTE]
> Per altre informazioni sui modelli di testo in generale, vedere [Generazione di codice e modelli di testo T4.](../modeling/code-generation-and-t4-text-templates.md) Per altre informazioni sul debug dei modelli di testo, vedere [Procedura dettagliata: debug di un modello di testo.](debugging-a-t4-text-template.md)

## <a name="creating-a-domain-specific-language-solution"></a>Creazione di una Domain-Specific linguaggio di programmazione
 In questa procedura viene creata una soluzione di linguaggio specifico di dominio con le caratteristiche seguenti:

- Nome: DebuggingTestLanguage

- Modello di soluzione: Linguaggio minimo

- Estensione di file: DDD

- Nome società: Fabrikam

  Per altre informazioni sulla creazione di una soluzione di linguaggio specifico di dominio, vedere [Procedura: Creare una soluzione Domain-Specific linguaggio.](../modeling/how-to-create-a-domain-specific-language-solution.md)

## <a name="creating-a-text-template"></a>Creazione di un modello di testo
 Aggiungere un modello di testo alla soluzione.

#### <a name="to-create-a-text-template"></a>Per creare un modello di testo

1. Compilare la soluzione e avviarla nel debugger. Scegliere **Ricompila** soluzione **dal** menu Compila e quindi scegliere Avvia debug dal **menu** **Debug.** Una nuova istanza di Visual Studio apre il progetto Debug.

2. Aggiungere un file di testo `DebugTest.tt` denominato al progetto debug.

3. Assicurarsi che la **proprietà Strumento personalizzato** di DebugTest.tt sia impostata su `TextTemplatingFileGenerator` .

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Direttive di debug che accedono a un modello da un modello di testo
 Prima di poter accedere a un modello dalle istruzioni e dalle espressioni in un modello di testo, è necessario chiamare un processore di direttiva generato. La chiamata al processore di direttiva generato rende le classi nel modello disponibili per il codice del modello di testo come proprietà. Per altre informazioni, vedere [Accesso ai modelli da modelli di testo.](../modeling/accessing-models-from-text-templates.md)

 Nelle procedure seguenti si eseguirà il debug di un nome di direttiva non corretto e di un nome di proprietà non corretto.

#### <a name="to-debug-an-incorrect-directive-name"></a>Per eseguire il debug di un nome di direttiva non corretto

1. Sostituire il codice in DebugTest.tt con il codice seguente:

    > [!NOTE]
    > Il codice contiene un errore. Si sta introducendo l'errore per eseguirne il debug.

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

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse DebugTest.tt e quindi scegliere **Esegui strumento personalizzato.**

     Nella **finestra Elenco** errori viene visualizzato questo errore:

     **Il processore denominato 'DebuggingTestLanguageDirectiveProcessor' non supporta la direttiva denominata 'modelRoot'. La trasformazione non verrà eseguita.**

     In questo caso, la chiamata di direttiva contiene un nome di direttiva non corretto. È stato specificato `modelRoot` come nome della direttiva , ma il nome di direttiva corretto è `DebuggingTestLanguage` .

3. Fare doppio clic sull'errore nella **finestra Elenco** errori per passare al codice.

4. Per correggere il codice, modificare il nome della direttiva in `DebuggingTestLanguage` .

     La modifica è evidenziata.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. In **Esplora soluzioni** fare clic con il pulsante destro del mouse DebugTest.tt e quindi scegliere **Esegui strumento personalizzato.**

     Ora il sistema trasforma il modello di testo e genera il file di output corrispondente. Nella finestra Elenco errori non verranno **visualizzati** errori.

#### <a name="to-debug-an-incorrect-property-name"></a>Per eseguire il debug di un nome di proprietà non corretto

1. Sostituire il codice in DebugTest.tt con il codice seguente:

    > [!NOTE]
    > Il codice contiene un errore. Si sta introducendo l'errore per eseguirne il debug.

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

2. In **Esplora soluzioni** fare clic con il pulsante destro del mouse DebugTest.tt e quindi scegliere **Esegui strumento personalizzato.**

     Verrà **visualizzata la** finestra Elenco errori con uno degli errori seguenti:

     (C#)

     **Trasformazione compilazione: Microsoft.VisualStudio.TextTemplating \<GUID> . GeneratedTextTransformation' non contiene una definizione per 'ExampleModel'**

     (Visual Basic)

     **Trasformazione di compilazione: 'ExampleModel' non è un membro di 'Microsoft.VisualStudio.TextTemplating. \<GUID> GeneratedTextTransformation'.**

     In questo caso, il codice del modello di testo contiene un nome di proprietà non corretto. È stato specificato `ExampleModel` come nome della proprietà, ma il nome corretto della proprietà è `LibraryModel` . È possibile trovare il nome corretto della proprietà nel parametro provides, come illustrato nel codice seguente:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Fare doppio clic sull'errore nella finestra Elenco errori per passare al codice.

4. Per correggere il codice, modificare il nome della proprietà `LibraryModel` in nel codice del modello di testo.

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

5. In **Esplora soluzioni** fare clic con il pulsante destro del mouse DebugTest.tt e quindi scegliere **Esegui strumento personalizzato.**

     Ora il sistema trasforma il modello di testo e genera il file di output corrispondente. Nella finestra Elenco errori non verranno **visualizzati** errori.
