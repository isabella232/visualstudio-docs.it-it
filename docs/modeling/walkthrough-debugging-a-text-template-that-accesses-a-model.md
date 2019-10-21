---
title: 'Procedura dettagliata: debug di un modello di testo che accede a un modello'
ms.date: 11/04/2016
ms.topic: conceptual
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 344a9331ed63d2da27379770305905ecf5edee77
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666963"
---
# <a name="walkthrough-debugging-a-text-template-that-accesses-a-model"></a>Procedura dettagliata: debug di un modello di testo che accede a un modello
Quando si modificano o si aggiungono modelli di testo in una soluzione di linguaggio specifico di dominio, è possibile che vengano generati errori quando il motore trasforma il modello nel codice sorgente o quando compila il codice generato. Nella procedura dettagliata riportata di seguito vengono illustrate alcune delle operazioni che è possibile eseguire per eseguire il debug di un modello di testo.

> [!NOTE]
> Per ulteriori informazioni sui modelli di testo in generale, vedere [generazione di codice e modelli di testo T4](../modeling/code-generation-and-t4-text-templates.md). Per ulteriori informazioni sul debug di modelli di testo, vedere [procedura dettagliata: debug di un modello di testo](debugging-a-t4-text-template.md).

## <a name="creating-a-domain-specific-language-solution"></a>Creazione di una soluzione Domain-Specific Language
 In questa procedura viene creata una soluzione di linguaggio specifico di dominio con le caratteristiche seguenti:

- Nome: DebuggingTestLanguage

- Modello di soluzione: linguaggio minimo

- Estensione di file:. ddd

- Nome della società: fabrikam

  Per altre informazioni sulla creazione di una soluzione di linguaggio specifico di dominio, vedere [procedura: creare una soluzione Domain-Specific Language](../modeling/how-to-create-a-domain-specific-language-solution.md).

## <a name="creating-a-text-template"></a>Creazione di un modello di testo
 Aggiungere un modello di testo alla soluzione.

#### <a name="to-create-a-text-template"></a>Per creare un modello di testo

1. Compilare la soluzione e iniziare a eseguirla nel debugger. Scegliere **Ricompila soluzione**dal menu **Compila** , quindi scegliere **Avvia debug**dal menu **debug** . Una nuova istanza di Visual Studio apre il progetto di debug.

2. Aggiungere un file di testo denominato `DebugTest.tt` al progetto di debug.

3. Verificare che la proprietà **strumento personalizzato** di DebugTest.tt sia impostata su `TextTemplatingFileGenerator`.

## <a name="debugging-directives-that-access-a-model-from-a-text-template"></a>Direttive di debug che accedono a un modello da un modello di testo
 Prima di poter accedere a un modello dalle istruzioni e dalle espressioni in un modello di testo, è prima necessario chiamare un processore di direttiva generato. La chiamata del processore di direttiva generato rende le classi del modello disponibili per il codice del modello di testo come proprietà. Per altre informazioni, vedere [accesso ai modelli da modelli di testo](../modeling/accessing-models-from-text-templates.md).

 Nelle procedure seguenti si eseguirà il debug di un nome di direttiva errato e di un nome di proprietà non corretto.

#### <a name="to-debug-an-incorrect-directive-name"></a>Per eseguire il debug di un nome di direttiva errato

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

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su DebugTest.TT, quindi scegliere **Esegui strumento personalizzato**.

     Nella finestra **Elenco errori** viene visualizzato questo errore:

     **Il processore denominato ' DebuggingTestLanguageDirectiveProcessor ' non supporta la direttiva denominata ' modelRoot '. La trasformazione non verrà eseguita.**

     In questo caso, la chiamata alla direttiva contiene un nome di direttiva errato. È stato specificato `modelRoot` come nome della direttiva, ma è `DebuggingTestLanguage` il nome della direttiva corretto.

3. Fare doppio clic sull'errore nella finestra **Elenco errori** per passare al codice.

4. Per correggere il codice, modificare il nome della direttiva in `DebuggingTestLanguage`.

     La modifica è evidenziata.

    ```csharp
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

    ```vb
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=ExampleModel" #>
    ```

5. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su DebugTest.TT, quindi scegliere **Esegui strumento personalizzato**.

     A questo punto il sistema trasforma il modello di testo e genera il file di output corrispondente. Non vengono visualizzati errori nella finestra **Elenco errori** .

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

2. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su DebugTest.TT, quindi scegliere **Esegui strumento personalizzato**.

     Viene visualizzata la finestra **Elenco errori** e viene visualizzato uno degli errori seguenti:

     (C#)

     **Compilazione della trasformazione: Microsoft. VisualStudio. TextTemplating \<GUID >. GeneratedTextTransformation ' non contiene una definizione per ' ExampleModel '**

     (Visual Basic)

     **Compilazione della trasformazione:' ExampleModel ' non è un membro di ' Microsoft. VisualStudio. TextTemplating \<GUID >. GeneratedTextTransformation ".**

     In questo caso, il codice del modello di testo contiene un nome di proprietà non corretto. È stato specificato `ExampleModel` come nome della proprietà, ma il nome della proprietà corretto è `LibraryModel`. È possibile trovare il nome di proprietà corretto nel parametro fornisce, come illustrato nel codice seguente:

    ```
    <#@ DebuggingTestLanguage processor="DebuggingTestLanguageDirectiveProcessor" requires="fileName='Sample.ddd'" provides="ExampleModel=LibraryModel" #>
    ```

3. Fare doppio clic sull'errore nella finestra Elenco errori per passare al codice.

4. Per correggere il codice, modificare il nome della proprietà in `LibraryModel` nel codice del modello di testo.

     Le modifiche vengono evidenziate.

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

5. In **Esplora soluzioni**fare clic con il pulsante destro del mouse su DebugTest.TT, quindi scegliere **Esegui strumento personalizzato**.

     A questo punto il sistema trasforma il modello di testo e genera il file di output corrispondente. Non vengono visualizzati errori nella finestra **Elenco errori** .