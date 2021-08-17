---
title: Connessione host al processore di direttiva generato
description: Informazioni su come espandere l'host personalizzato in modo che supporti modelli di testo che chiamano processori di direttiva.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: d60a7bd348bba51009bbab5264fa94d5370ac4246345e283f51eff72eaf3258a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121443867"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>Procedura dettagliata: Connettere un host a un processore di direttiva generato

È possibile scrivere un host personalizzato che elabora modelli di testo. Un host personalizzato di base è illustrato in [Procedura dettagliata: Creazione di un host modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md). È possibile estendere tale host per aggiungere funzioni come la generazione di più file di output.

In questa procedura dettagliata si espande l'host personalizzato in modo che supporti modelli di testo che chiamano processori di direttiva. Quando si definisce un linguaggio specifico di dominio, viene generato un *processore di direttiva* per il modello di dominio. Il processore di direttiva semplifica la scrittura di modelli che accedono al modello, riducendo la necessità di scrivere direttive di assembly e importazione nei modelli.

> [!NOTE]
> Questa procedura dettagliata si basa su [Procedura dettagliata: creazione di un host del modello di testo personalizzato.](../modeling/walkthrough-creating-a-custom-text-template-host.md) Eseguire prima questa procedura dettagliata.

In questa procedura dettagliata sono incluse le attività seguenti:

- Uso [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] di per generare un processore di direttiva basato su un modello di dominio.

- Connessione di un host del modello di testo personalizzato al processore di direttiva generato.

- Test dell'host personalizzato con il processore di direttiva generato.

## <a name="prerequisites"></a>Prerequisiti

Per definire un linguaggio specifico di dominio (Domain-Specific Language, DSL) devono essere installati i componenti seguenti:

| Componente | Collegamento |
|-|-|
| Visual Studio | [http://go.microsoft.com/fwlink/?LinkId=185579](https://visualstudio.microsoft.com/) |
| [!INCLUDE[vssdk_current_short](../modeling/includes/vssdk_current_short_md.md)] | [http://go.microsoft.com/fwlink/?LinkId=185580](/azure/devops/integrate/index) |
| SDK di visualizzazione e modellazione di Visual Studio | |

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

È inoltre necessario che la trasformazione modello di testo personalizzato sia stata creata in [Procedura dettagliata: Creazione di un host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Usare Domain-Specific language tools per generare un processore di direttiva

In questa procedura dettagliata si usa la creazione guidata Domain-Specific Language Designer per creare un linguaggio specifico di dominio per la soluzione DSLMinimalTest.

1. Creare una soluzione del linguaggio specifico di dominio con le caratteristiche seguenti:

   - Nome: DSLMinimalTest

   - Modello di soluzione: Linguaggio minimo

   - Estensione di file: min

   - Nome società: Fabrikam

   Per altre informazioni sulla creazione di una soluzione di linguaggio specifico di dominio, vedere Procedura: Creare una soluzione Domain-Specific [linguaggio.](../modeling/how-to-create-a-domain-specific-language-solution.md)

2. Nel menu **Compila** scegliere **Compila soluzione**.

   > [!IMPORTANT]
   > Questo passaggio genera il processore di direttiva e aggiunge la chiave nel Registro di sistema.

3. Scegliere **Avvia debug** dal menu **Debug**.

    Viene aperta una seconda istanza Visual Studio.

4. Nella build sperimentale, in **Esplora soluzioni** fare doppio clic sul file **sample.min**.

    Il file viene aperto nella finestra di progettazione. Si noti che il modello include due elementi, ExampleElement1 ed ExampleElement2, e un collegamento tra di essi.

5. Chiudere la seconda istanza di Visual Studio.

6. Salvare la soluzione e quindi chiudere l'Domain-Specific Language Designer.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Connessione host del modello di testo personalizzato in un processore di direttiva

Dopo aver generato il processore di direttiva, connettere il processore di direttiva e l'host del modello di testo personalizzato creato in [Procedura dettagliata: Creazione di un host del](../modeling/walkthrough-creating-a-custom-text-template-host.md)modello di testo personalizzato .

1. Aprire la soluzione CustomHost.

2. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

     Verrà **visualizzata la finestra** di dialogo Aggiungi riferimento con la scheda **.NET** visualizzata.

3. Aggiungere i riferimenti seguenti:

    - Microsoft.VisualStudio.Modeling.Sdk.11.0

    - Microsoft.VisualStudio.Modeling.Sdk.Diagrams.11.0

    - Microsoft.VisualStudio.TextTemplating.11.0

    - Microsoft.VisualStudio.TextTemplating.Interfaces.11.0

    - Microsoft.VisualStudio.TextTemplating.Modeling.11.0

    - Microsoft.VisualStudio.TextTemplating.VSHost.11.0

4. Nella parte superiore di Program.cs o Module1.vb aggiungere la riga di codice seguente:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Individuare il codice per la `StandardAssemblyReferences` proprietà e sostituirlo con il codice seguente:

    > [!NOTE]
    > In questo passaggio si aggiungono riferimenti agli assembly richiesti dal processore di direttiva generato che l'host supporterà.

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

6. Individuare il codice per la funzione `ResolveDirectiveProcessor` e sostituirlo con il codice seguente:

    > [!IMPORTANT]
    > Questo codice contiene riferimenti hard coded al nome del processore di direttiva generato a cui si vuole connettersi. È possibile renderlo più generale, nel qual caso cerca tutti i processori di direttiva elencati nel Registro di sistema e prova a trovare una corrispondenza. In tal caso, l'host funzionerà con qualsiasi processore di direttiva generato.

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

7. Scegliere **Salva tutti** dal menu **File**.

8. Nel menu **Compila** scegliere **Compila soluzione**.

## <a name="test-the-custom-host-with-the-directive-processor"></a>Testare l'host personalizzato con il processore di direttiva

Per testare l'host del modello di testo personalizzato, è innanzitutto necessario scrivere un modello di testo che chiama il processore di direttiva generato. Eseguire quindi l'host personalizzato, passarvi il nome del modello di testo e verificare che la direttiva venga elaborata correttamente.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Creare un modello di testo per testare l'host personalizzato

1. Creare un file di testo e assegnare al file il nome `TestTemplateWithDP.tt` . È possibile usare qualsiasi editor di testo, ad esempio Blocco note, per creare il file.

2. Aggiungere quanto segue al file di testo:

    > [!NOTE]
    > Il linguaggio di programmazione del modello di testo non deve corrispondere a quello dell'host personalizzato.

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

3. Nel codice sostituire con il percorso del file Sample.min del linguaggio specifico della progettazione \<YOUR PATH> creato nella prima procedura.

4. Salvare e chiudere il file.

### <a name="test-the-custom-host"></a>Testare l'host personalizzato

1. Aprire una finestra del prompt dei comandi.

2. Digitare il percorso del file eseguibile per l'host personalizzato, ma non premere ancora INVIO.

     Ad esempio, digitare il comando seguente:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Anziché digitare l'indirizzo, è possibile passare al file CustomHost.exe in **Windows Explorer** e quindi trascinare il file nella finestra del prompt dei comandi.

3. Digitare uno spazio.

4. Digitare il percorso del file modello di testo, quindi premere INVIO.

     Ad esempio, digitare il comando seguente:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Anziché digitare l'indirizzo, è possibile passare al file TestTemplateWithDP.txt in **Windows Explorer** e quindi trascinare il file nella finestra del prompt dei comandi.

     L'applicazione host personalizzata viene eseguita e avvia il processo di trasformazione del modello di testo.

5. In **Windows Explorer** passare alla cartella che contiene il file TestTemplateWithDP.txt.

     La cartella contiene anche il file TestTemplateWithDP1.txt.

6. Aprire questo file per vedere i risultati della trasformazione del modello di testo.

     I risultati dell'output di testo generato vengono visualizzati e dovrebbero essere simili ai seguenti:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: creazione di un host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md)
