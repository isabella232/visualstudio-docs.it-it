---
title: 'Procedura dettagliata: Connessione di un Host a un processore di direttiva generato'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: a84b24dff387e0a93058c07e9f6d7b6cfe503d49
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55935589"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>Procedura dettagliata: Connettere un Host a un processore di direttiva generato

È possibile scrivere il proprio host che elabora i modelli di testo. Un host personalizzato basic viene illustrato in [procedura dettagliata: Creazione di un Host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md). È possibile estendere tale host per aggiungere le funzioni, ad esempio la generazione di più file di output.

In questa procedura dettagliata, si espande l'host personalizzato, in modo che supporti i modelli di testo che chiamano processori di direttiva. Quando si definisce un linguaggio specifico di dominio, viene generato un *processore di direttiva* per il modello di dominio. Il processore di direttiva rende più semplice per gli utenti di scrivere modelli di accedere al modello, riducendo la necessità di scrivere assembly e importare le direttive nei modelli.

> [!NOTE]
> Questa procedura dettagliata si basa su [procedura dettagliata: Creazione di un Host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md). Eseguire innanzitutto tale procedura dettagliata.

In questa procedura dettagliata sono incluse le attività seguenti:

- Usando [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] per generare un processore di direttiva che si basa su un modello di dominio.

- La connessione a un host del modello di testo personalizzato per il processore di direttiva generato.

- Test dell'host personalizzato con il processore di direttiva generato.

## <a name="prerequisites"></a>Prerequisiti

Per definire un linguaggio specifico di dominio (Domain-Specific Language, DSL) devono essere installati i componenti seguenti:


| | |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](http://go.microsoft.com/fwlink/?LinkId=185579) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](http://go.microsoft.com/fwlink/?LinkId=185580) |
| SDK di visualizzazione e modellazione di Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

Inoltre, è necessario disporre di trasformazione del modello testo personalizzato creata in [procedura dettagliata: Creazione di un Host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Usare gli strumenti Domain-Specific Language per generare un processore di direttiva

In questa procedura dettagliata, è utilizzare la procedura guidata finestra di progettazione di linguaggio specifico di dominio per creare un linguaggio specifico di dominio per la soluzione DSLMinimalTest.

1. Creare una soluzione di linguaggio specifico di dominio che ha le caratteristiche seguenti:

   -   Nome: DSLMinimalTest

   -   Modello di soluzione: Linguaggio minimo

   -   Estensione di file: min

   -   Nome della società: Fabrikam

   Per altre informazioni sulla creazione di una soluzione domain-specific language, vedere [come: Creare una soluzione per un linguaggio specifico di dominio](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. Scegliere **Compila soluzione** dal menu **Compila**.

   > [!IMPORTANT]
   > Questo passaggio genera il processore di direttiva e aggiunge la chiave per lo nel Registro di sistema.

3. Scegliere **Avvia debug** dal menu **Debug**.

    Si apre una seconda istanza di Visual Studio.

4. Nella build sperimentale, nella **Esplora soluzioni**, fare doppio clic sul file **sample.min**.

    Il file viene aperto nella finestra di progettazione. Si noti che il modello a dispone di due elementi, ExampleElement1 ed ExampleElement2 e un collegamento tra di essi.

5. Chiudere la seconda istanza di Visual Studio.

6. Salvare la soluzione e quindi chiudere la finestra di progettazione di linguaggio specifico di dominio.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Connettersi a un Host del modello di testo personalizzato a un processore di direttiva

Dopo aver generato il processore di direttiva, si connette il processore di direttiva e l'host del modello di testo personalizzato creato nel [procedura dettagliata: Creazione di un Host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md).

1.  Aprire la soluzione CustomHost.

2.  Scegliere **Aggiungi riferimento** dal menu **Progetto**.

     Il **Aggiungi riferimento** verrà visualizzata la finestra di dialogo con la **.NET** visualizzata la scheda.

3.  Aggiungere i riferimenti seguenti:

    -   Microsoft.VisualStudio.Modeling.Sdk.11.0

    -   Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    -   Microsoft.VisualStudio.TextTemplating.11.0

    -   Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    -   Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    -   Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4.  Nella parte superiore del file Program.cs o Module1.vb, aggiungere la riga di codice seguente:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5.  Individuare il codice per la proprietà `StandardAssemblyReferences`e sostituirlo con il codice seguente:

    > [!NOTE]
    > In questo passaggio aggiungere riferimenti agli assembly richiesti dal processore di direttiva generato che supporterà l'host.

    ```csharp
    //the host can provide standard assembly references
    //the engine will use these references when compiling and
    //executing the generated transformation class
    //--------------------------------------------------------------
    public IList<string> StandardAssemblyReferences
    {
        get
        {
            return new string[]
            {
                //if this host searches standard paths and the GAC
                //we can specify the assembly name like this:
                //"System"
                //since this host only resolves assemblies from the
                //fully qualified path and name of the assembly
                //this is a quick way to get the code to give us the
                //fully qualified path and name of the System assembly
                //---------------------------------------------------------
                typeof(System.Uri).Assembly.Location,
                            typeof(System.Uri).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.ModelElement).Assembly.Location,
                typeof(Microsoft.VisualStudio.Modeling.Diagrams.BinaryLinkShape).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ITextTemplating).Assembly.Location,
                typeof(Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation).Assembly.Location

            };
        }
    }
    ```

6.  Individuare il codice per la funzione `ResolveDirectiveProcessor`e sostituirlo con il codice seguente:

    > [!IMPORTANT]
    > Questo codice contiene riferimenti a livello di codice per il nome del processore di direttiva generato a cui si desidera connettersi. È possibile apportare facilmente questo più generali, nel qual caso la ricerca di tutti i processori di direttiva elencati nel Registro di sistema e tenta di trovare una corrispondenza. In tal caso, l'host funzionerà con qualsiasi processore di direttiva generato.

    ```csharp
    //the engine calls this method based on the directives the user has
            //specified it in the text template
            //this method can be called 0, 1, or more times
            //---------------------------------------------------------------------
            public Type ResolveDirectiveProcessor(string processorName)
            {
                //check the processor name, and if it is the name of the processor the
                //host wants to support, return the type of the processor
                //---------------------------------------------------------------------
                if (string.Compare(processorName, "DSLMinimalTestDirectiveProcessor", StringComparison.InvariantCultureIgnoreCase) == 0)
                {
                    try
                    {
                        string keyName = @"Software\Microsoft\VisualStudio\10.0Exp_Config\TextTemplating\DirectiveProcessors\DSLMinimalTestDirectiveProcessor";
                        using (RegistryKey specificKey = Registry.CurrentUser.OpenSubKey(keyName))
                        {
                            if (specificKey != null)
                            {
                                List<string> names = new List<String>(specificKey.GetValueNames());
                                string classValue = specificKey.GetValue("Class") as string;
                                if (!string.IsNullOrEmpty(classValue))
                                {
                                    string loadValue = string.Empty;
                                    System.Reflection.Assembly processorAssembly = null;
                                    if (names.Contains("Assembly"))
                                    {
                                        loadValue = specificKey.GetValue("Assembly") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //the assembly must be installed in the GAC
                                            processorAssembly = System.Reflection.Assembly.Load(loadValue);
                                        }
                                    }
                                    else if (names.Contains("CodeBase"))
                                    {
                                        loadValue = specificKey.GetValue("CodeBase") as string;
                                        if (!string.IsNullOrEmpty(loadValue))
                                        {
                                            //loading local assembly
                                            processorAssembly = System.Reflection.Assembly.LoadFrom(loadValue);
                                        }
                                    }
                                    if (processorAssembly == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    Type processorType = processorAssembly.GetType(classValue);
                                    if (processorType == null)
                                    {
                                        throw new Exception("Directive Processor not found");
                                    }
                                    return processorType;
                                }
                            }
                        }
                    }
                    catch (Exception e)
                    {
                        //if the directive processor can not be found, throw an error
                        throw new Exception("Directive Processor not found");
                    }
                }

                //if the directive processor is not one this host wants to support
                throw new Exception("Directive Processor not supported");
            }
    ```

7.  Nel menu **File** fare clic su **Salva tutto**.

8.  Scegliere **Compila soluzione** dal menu **Compila**.

## <a name="test-the-custom-host-with-the-directive-processor"></a>Testare l'Host con il processore di direttiva personalizzato

Per testare l'host del modello di testo personalizzato, è innanzitutto necessario scrivere un modello di testo che chiama il processore di direttiva generato. Quindi si esegue l'host personalizzato, passare ad esso il nome del modello di testo e verificare che la direttiva viene elaborata correttamente.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Creare un modello di testo per testare l'host personalizzato

1.  Creare un file di testo e denominarlo `TestTemplateWithDP.tt`. È possibile usare qualsiasi editor di testo, ad esempio Blocco note, per creare il file.

2.  Aggiungere quanto segue al file di testo:

    > [!NOTE]
    > Il linguaggio di programmazione del modello di testo non dovrà corrispondere a quello dell'host personalizzato.

    ```csharp
    Text Template Host Test

    <#@ template debug="true" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>
    <# //this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>
    <# //uncomment this line to test that the host allows the engine to set the extension #>
    <# //@ output extension=".htm" #>

    <# //uncomment this line if you want to see the generated transformation class #>
    <# //System.Diagnostics.Debugger.Break(); #>
    <# //this code uses the results of the examplemodel directive #>
    <#
        foreach ( ExampleElement box in this.ExampleModel.Elements )
        {
            WriteLine("Box: {0}", box.Name);

            foreach (ExampleElement linkedTo in box.Targets)
            {
                WriteLine("Linked to: {0}", linkedTo.Name);
            }

            foreach (ExampleElement linkedFrom in box.Sources)
            {
                WriteLine("Linked from: {0}", linkedFrom.Name);
            }

            WriteLine("");
        }
    #>
    ```

    ```vb
    Text Template Host Test

    <#@ template debug="true" language="VB" inherits="Microsoft.VisualStudio.TextTemplating.VSHost.ModelingTextTransformation" #>

    <# 'this is the call to the examplemodel directive in the generated directive processor #>
    <#@ DSLMinimalTest processor="DSLMinimalTestDirectiveProcessor" requires="fileName='<Your Path>\Sample.min'" provides="ExampleModel=ExampleModel" #>

    <# 'Uncomment this line to test that the host allows the engine to set the extension. #>
    <# '@ output extension=".htm" #>

    <# 'Uncomment this line if you want to see the generated transformation class. #>
    <# 'System.Diagnostics.Debugger.Break() #>

    <# 'this code uses the results of the examplemodel directive #>

    <#
       For Each box as ExampleElement In Me.ExampleModel.Elements

           WriteLine("Box: {0}", box.Name)

            For Each LinkedTo as ExampleElement In box.Targets
                WriteLine("Linked to: {0}", LinkedTo.Name)
            Next

            For Each LinkedFrom as ExampleElement In box.Sources
                WriteLine("Linked from: {0}", LinkedFrom.Name)
            Next

            WriteLine("")

       Next
    #>
    ```

3.  Nel codice, sostituire \<YOUR PATH > con il percorso del file Sample.min dal linguaggio specifico di progettazione creata nella prima procedura.

4.  Salvare e chiudere il file.

### <a name="test-the-custom-host"></a>Testare l'host personalizzato

1.  Aprire una finestra del prompt dei comandi.

2.  Digitare il percorso del file eseguibile per l'host personalizzato, ma non premere ancora INVIO.

     Digitare ad esempio:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Anziché digitare l'indirizzo, è possibile passare al file CustomHost.exe nelle **Windows Explorer**e quindi trascinare il file nella finestra del prompt dei comandi.

3.  Digitare uno spazio.

4.  Digitare il percorso del file modello di testo, quindi premere INVIO.

     Digitare ad esempio:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Anziché digitare l'indirizzo, è possibile passare al file TestTemplateWithDP.txt nelle **Windows Explorer**e quindi trascinare il file nella finestra del prompt dei comandi.

     L'applicazione host personalizzata viene eseguita e viene avviato il processo di trasformazione di modello di testo.

5.  Nelle **Windows Explorer**, passare alla cartella che contiene il file TestTemplateWithDP.txt.

     La cartella contiene inoltre il file TestTemplateWithDP1.txt.

6.  Aprire questo file per vedere i risultati della trasformazione del modello di testo.

     I risultati di output di testo generato viene visualizzata e sarà simile al seguente:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Creazione di un Host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md)
