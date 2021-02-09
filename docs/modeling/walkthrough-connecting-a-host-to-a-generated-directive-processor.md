---
title: Connetti host al processore di direttiva generato
description: Informazioni su come espandere l'host personalizzato in modo che supporti i modelli di testo che chiamano i processori di direttiva.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- walkthroughs [text templates], connecting host to processor
- text templates, custom directive hosts
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.workload:
- multiple
dev_langs:
- CSharp
- VB
ms.openlocfilehash: a815718f099b024708b86658e10fc0e85c087b4c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99924127"
---
# <a name="walkthrough-connect-a-host-to-a-generated-directive-processor"></a>Procedura dettagliata: Connettere un host a un processore di direttiva generato

È possibile scrivere un host personalizzato che elabora i modelli di testo. Un host personalizzato di base viene illustrato in [procedura dettagliata: creazione di un host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md). È possibile estendere tale host per aggiungere funzioni quali la generazione di più file di output.

In questa procedura dettagliata si espande l'host personalizzato in modo che supporti i modelli di testo che chiamano i processori di direttiva. Quando si definisce un linguaggio specifico di dominio, viene generato un *processore di direttiva* per il modello di dominio. Il processore di direttiva rende più semplice per gli utenti scrivere modelli che accedono al modello, riducendo la necessità di scrivere direttive assembly e Import nei modelli.

> [!NOTE]
> Questa procedura dettagliata si basa su [procedura dettagliata: creazione di un host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md). Eseguire prima questa procedura dettagliata.

In questa procedura dettagliata sono incluse le attività seguenti:

- Utilizzo [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] di per generare un processore di direttiva basato su un modello di dominio.

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

Inoltre, è necessario che la trasformazione del modello di testo personalizzato sia stata creata in [procedura dettagliata: creazione di un host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md).

## <a name="use-domain-specific-language-tools-to-generate-a-directive-processor"></a>Usare gli strumenti del linguaggio Domain-Specific per generare un processore di direttiva

In questa procedura dettagliata viene utilizzata la creazione guidata di Domain-Specific linguaggio per creare un linguaggio specifico di dominio per la soluzione DSLMinimalTest.

1. Creare una soluzione di linguaggio specifico di dominio con le caratteristiche seguenti:

   - Nome: DSLMinimalTest

   - Modello di soluzione: linguaggio minimo

   - Estensione di file: min

   - Nome della società: fabrikam

   Per altre informazioni sulla creazione di una soluzione di linguaggio specifico di dominio, vedere [procedura: creare una soluzione di linguaggio Domain-Specific](../modeling/how-to-create-a-domain-specific-language-solution.md).

2. Nel menu **Compila** scegliere **Compila soluzione**.

   > [!IMPORTANT]
   > Questo passaggio genera il processore di direttiva e ne aggiunge la chiave nel registro di sistema.

3. Scegliere **Avvia debug** dal menu **Debug**.

    Viene aperta una seconda istanza di Visual Studio.

4. Nella build sperimentale, in **Esplora soluzioni**, fare doppio clic sul file **Sample. min**.

    Il file verrà aperto nella finestra di progettazione. Si noti che il modello ha due elementi, ExampleElement1 e ExampleElement2, e un collegamento tra di essi.

5. Chiudere la seconda istanza di Visual Studio.

6. Salvare la soluzione, quindi chiudere la finestra di progettazione del linguaggio Domain-Specific.

## <a name="connect-a-custom-text-template-host-to-a-directive-processor"></a>Connettere un host del modello di testo personalizzato a un processore di direttiva

Dopo aver generato il processore di direttiva, connettere il processore di direttiva e l'host del modello di testo personalizzato creato in [procedura dettagliata: creazione di un host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md).

1. Aprire la soluzione CustomHost.

2. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

     Verrà visualizzata la finestra di dialogo **Aggiungi riferimento** con la scheda **.NET** visualizzata.

3. Aggiungere i riferimenti seguenti:

    - Microsoft. VisualStudio. Modeling. Sdk. 11.0

    - Microsoft. VisualStudio. Modeling. Sdk. Diagrams. 11.0

    - Microsoft. VisualStudio. TextTemplating. 11.0

    - Microsoft. VisualStudio. TextTemplating. Interfaces. 11.0

    - Microsoft. VisualStudio. TextTemplating. Modeling. 11.0

    - Microsoft. VisualStudio. TextTemplating. VSHost. 11.0

4. Nella parte superiore di Program.cs o Module1. vb aggiungere la riga di codice seguente:

    ```csharp
    using Microsoft.Win32;
    ```

    ```vb
    Imports Microsoft.Win32
    ```

5. Individuare il codice per la proprietà `StandardAssemblyReferences` e sostituirlo con il codice seguente:

    > [!NOTE]
    > In questo passaggio si aggiungono riferimenti agli assembly richiesti dal processore di direttiva generato che verrà supportato dall'host.

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
    > Questo codice contiene riferimenti hardcoded al nome del processore di direttiva generato a cui si desidera connettersi. È possibile rendere questa operazione più generale, nel qual caso Cerca tutti i processori di direttiva elencati nel registro di sistema e tenta di trovare una corrispondenza. In tal caso, l'host funzionerebbe con qualsiasi processore di direttiva generato.

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

Per testare l'host del modello di testo personalizzato, è prima necessario scrivere un modello di testo che chiama il processore di direttiva generato. Quindi si esegue l'host personalizzato, lo si passa al nome del modello di testo e si verifica che la direttiva venga elaborata correttamente.

### <a name="create-a-text-template-to-test-the-custom-host"></a>Creare un modello di testo per testare l'host personalizzato

1. Creare un file di testo e denominarlo `TestTemplateWithDP.tt` . Per creare il file, è possibile usare qualsiasi editor di testo, ad esempio Blocco note.

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

3. Nel codice sostituire \<YOUR PATH> con il percorso del file Sample. min dalla lingua specifica della progettazione creata nella prima procedura.

4. Salvare e chiudere il file.

### <a name="test-the-custom-host"></a>Testare l'host personalizzato

1. Aprire una finestra del prompt dei comandi.

2. Digitare il percorso del file eseguibile per l'host personalizzato, ma non premere ancora INVIO.

     Ad esempio, digitare il comando seguente:

     `<YOUR PATH>CustomHost\bin\Debug\CustomHost.exe`

    > [!NOTE]
    > Anziché digitare l'indirizzo, è possibile passare al file CustomHost.exe in **Esplora risorse**, quindi trascinare il file nella finestra del prompt dei comandi.

3. Digitare uno spazio.

4. Digitare il percorso del file modello di testo, quindi premere INVIO.

     Ad esempio, digitare il comando seguente:

     `<YOUR PATH>TestTemplateWithDP.txt`

    > [!NOTE]
    > Anziché digitare l'indirizzo, è possibile passare al file TestTemplateWithDP.txt in **Esplora risorse**, quindi trascinare il file nella finestra del prompt dei comandi.

     L'applicazione host personalizzata viene eseguita e avvia il processo di trasformazione del modello di testo.

5. In **Esplora risorse** passare alla cartella che contiene il file TestTemplateWithDP.txt.

     La cartella contiene anche il file TestTemplateWithDP1.txt.

6. Aprire questo file per vedere i risultati della trasformazione del modello di testo.

     Verranno visualizzati i risultati dell'output di testo generato e dovrebbe essere simile al seguente:

    ```
    Text Template Host Test

    Box: ExampleElement1
    Linked to: ExampleElement2

    Box: ExampleElement2
    Linked from: ExampleElement1
    ```

## <a name="see-also"></a>Vedi anche

- [Procedura dettagliata: creazione di un host del modello di testo personalizzato](../modeling/walkthrough-creating-a-custom-text-template-host.md)
