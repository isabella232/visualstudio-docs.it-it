---
title: "Procedura dettagliata: Creazione di un'attività inline | Microsoft Docs"
description: Illustrare la creazione MSBuild'attività inline nel file di progetto, senza dover creare un assembly separato per ospitare l'attività.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tutorial
- MSBuild, tasks
ms.assetid: 438194cb-668c-41a9-a7e2-c118d14c1ea7
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: e91ba93007cb721d8045ff1253ae39796b227124
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108161"
---
# <a name="walkthrough-create-an-inline-task"></a>Procedura dettagliata: Creare un'attività inline

Le attività MSBuild vengono in genere create tramite la compilazione di una classe che implementa l'interfaccia <xref:Microsoft.Build.Framework.ITask>. A partire dalla versione 4 di .NET Framework è possibile creare attività inline nel file di progetto. Non è necessario creare un assembly separato per ospitare l'attività. Per altre informazioni, vedere [Attività inline](../msbuild/msbuild-inline-tasks.md).

 Questa procedura dettagliata mostra come creare ed eseguire le attività inline seguenti:

- Un'attività priva di parametri di input o di output.

- Un'attività che presenta un solo parametro di input e nessun parametro di output.

- Un'attività che presenta due parametri di input e un parametro di output che restituisce una proprietà MSBuild.

- Un'attività che presenta due parametri di input e un parametro di output che restituisce un elemento MSBuild.

Per creare ed eseguire le attività, usare Visual Studio e la **finestra del prompt dei comandi di Visual Studio** nel modo seguente:

1. Creare un file di progetto MSBuild tramite Visual Studio.

2. Modificare il file di progetto in Visual Studio per creare l'attività inline.

3. Usare la **finestra del prompt dei comandi** per compilare il progetto ed esaminare i risultati.

## <a name="create-and-modify-an-msbuild-project"></a>Creare e modificare un progetto MSBuild

 Il sistema dei progetti di Visual Studio si basa su MSBuild. È pertanto possibile creare un file di progetto di compilazione usando Visual Studio. In questa sezione si crea un file di progetto Visual C#. In alternativa, è possibile creare un file di progetto di Visual Basic. Nel contesto di questa esercitazione, le differenze tra i due file di progetto sono trascurabili.

#### <a name="to-create-and-modify-a-project-file"></a>Per creare e modificare un file di progetto

1. In Visual Studio creare un nuovo progetto usando il modello Applicazione **Form Windows** C#. Nella casella **Nome** digitare `InlineTasks`. In **Percorso** digitare un percorso per la soluzione, ad esempio *D:\\*. Verificare che l'opzione **Crea directory per soluzione** sia selezionata, che l'opzione **Aggiungi al controllo del codice sorgente** sia deselezionata e che **Nome soluzione** sia **InlineTasks**.

3. Scegliere **OK** per creare il file di progetto.

3. In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul nodo del progetto **InlineTasks** e quindi **scegliere Scarica** Project .

4. Fare nuovamente clic con il pulsante destro del mouse sul nodo di progetto e quindi scegliere **Modifica InlineTasks.csproj**.

     Il file di progetto verrà visualizzato nell'editor del codice.

## <a name="add-a-basic-hello-task"></a>Aggiungere un'attività di base denominata Hello

 A questo punto, aggiungere al file di progetto un'attività di base che visualizza il messaggio "Hello, world!". Aggiungere anche una destinazione TestBuild predefinita per richiamare l'attività.

#### <a name="to-add-a-basic-hello-task"></a>Per aggiungere un'attività di base denominata Hello

1. Nel nodo `Project` radice modificare l'attributo `DefaultTargets` in `TestBuild`. Il nodo `Project` risultante sarà simile all'esempio seguente:

   ```xml
   <Project ToolsVersion="4.0" DefaultTargets="TestBuild" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   ```

2. Aggiungere la destinazione e l'attività inline seguenti al file di progetto subito prima del tag `</Project>`.

   ```xml
   <UsingTask TaskName="Hello" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup />
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, "Hello, world!");
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Hello />
   </Target>
   ```

3. Salvare il file di progetto.

   Questo codice crea un'attività inline denominata Hello senza parametri, riferimenti `Using` o direttive. L'attività Hello contiene un'unica riga di codice. Tale riga visualizza un messaggio di saluto nel dispositivo di registrazione predefinito, in genere la finestra della console.

### <a name="run-the-hello-task"></a>Eseguire l'attività Hello

 Eseguire MSBuild tramite la **finestra del prompt dei comandi** per costruire l'attività Hello ed elaborare la destinazione TestBuild che la richiama.

##### <a name="to-run-the-hello-task"></a>Per eseguire l'attività Hello

1. Fare clic su **Start**, scegliere **Tutti i programmi,**, quindi individuare la cartella **Strumenti di Visual Studio** e infine fare clic su **Prompt dei comandi di Visual Studio**.

2. Nella finestra **del prompt dei** comandi individuare la cartella che contiene il file di progetto, in questo caso *D:\InlineTasks\InlineTasks \\*.

3. Digitare **msbuild** senza opzioni di comando e quindi premere **INVIO.** Per impostazione predefinita, compila il file *InlineTasks.csproj* ed elabora la destinazione predefinita TestBuild, che richiama l'attività Hello.

4. Esaminare l'output nella **finestra del prompt dei comandi**. Dovrebbe essere visualizzata questa riga:

    `Hello, world!`

   > [!NOTE]
   > Se questa riga non viene visualizzata, salvare nuovamente il file di progetto e quindi eseguire l'attività Hello.

   Alternando l'editor del codice e la **finestra del prompt dei comandi**, è possibile modificare il file di progetto e visualizzare velocemente i risultati.

## <a name="define-the-echo-task"></a>Definire l'attività Echo

 Creare un'attività inline che accetta un parametro stringa e visualizza la stringa nel dispositivo di registrazione predefinito.

#### <a name="to-define-the-echo-task"></a>Per definire l'attività Echo

1. Nell'editor del codice sostituire l'attività Hello e la destinazione TestBuild tramite il codice seguente.

   ```xml
   <UsingTask TaskName="Echo" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Text Required="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         Log.LogMessage(MessageImportance.High, Text);
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Echo Text="Greetings!" />
   </Target>
   ```

2. Nella finestra **del prompt dei comandi** digitare **msbuild** senza opzioni di comando e quindi premere **INVIO.** Per impostazione predefinita, viene elaborata la destinazione predefinita TestBuild che richiama l'attività Echo.

3. Esaminare l'output nella **finestra del prompt dei comandi**. Dovrebbe essere visualizzata questa riga:

    `Greetings!`

   Questo codice definisce un'attività inline denominata Echo che presenta un unico parametro di input obbligatorio denominato Text. Per impostazione predefinita, i parametri sono di tipo System.String. Il valore del parametro Text viene impostato quando la destinazione TestBuild richiama l'attività Echo.

## <a name="define-the-adder-task"></a>Definire l'attività Adder

 Creare un'attività inline che aggiunge due parametri Integer e ne genera la somma come proprietà MSBuild.

#### <a name="to-define-the-adder-task"></a>Per definire l'attività Adder

1. Nell'editor del codice sostituire l'attività Echo e la destinazione TestBuild usando il codice seguente.

   ```xml
   <UsingTask TaskName="Adder" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <A ParameterType="System.Int32" Required="true" />
       <B ParameterType="System.Int32" Required="true" />
       <C ParameterType="System.Int32" Output="true" />
     </ParameterGroup>
     <Task>
       <Code Type="Fragment" Language="cs">
         C = A + B;
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <Adder A="4" B="5">
       <Output PropertyName="Sum" TaskParameter="C" />
     </Adder>
     <Message Text="The sum is $(Sum)" Importance="High" />
   </Target>
   ```

2. Nella finestra **del prompt dei comandi** digitare **msbuild** senza opzioni di comando e quindi premere **INVIO.** Per impostazione predefinita, viene elaborata la destinazione predefinita TestBuild che richiama l'attività Echo.

3. Esaminare l'output nella **finestra del prompt dei comandi**. Dovrebbe essere visualizzata questa riga:

    `The sum is 9`

   Questo codice definisce un'attività inline denominata Adder che presenta due parametri di input Integer obbligatori, A e B, e un parametro di output Integer, C. L'attività Adder aggiunge i due parametri di input e restituisce la somma nel parametro di output. La somma viene generata come proprietà MSBuild denominata `Sum`. I valori dei parametri di input vengono impostati quando la destinazione TestBuild richiama l'attività Adder.

## <a name="define-the-regx-task"></a>Definire l'attività RegX

 Creare un'attività inline che accetta un gruppo di elementi e un'espressione regolare e restituisce un elenco di tutti gli elementi il cui contenuto di file corrisponde all'espressione.

#### <a name="to-define-the-regx-task"></a>Per definire l'attività RegX

1. Nell'editor del codice sostituire l'attività Adder e la destinazione TestBuild tramite il codice seguente.

   ```xml
   <UsingTask TaskName="RegX" TaskFactory="CodeTaskFactory" AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.v4.0.dll" >
     <ParameterGroup>
       <Expression Required="true" />
       <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
       <Result ParameterType="Microsoft.Build.Framework.ITaskItem[]" Output="true" />
     </ParameterGroup>
     <Task>
       <Using Namespace="System.Text.RegularExpressions"/>
       <Code Type="Fragment" Language="cs">
   <![CDATA[
         if (Files.Length > 0)
         {
           Result = new TaskItem[Files.Length];
           for (int i = 0; i < Files.Length; i++)
           {
             ITaskItem item = Files[i];
             string path = item.GetMetadata("FullPath");
             using(StreamReader rdr = File.OpenText(path))
             {
               if (Regex.Match(rdr.ReadToEnd(), Expression).Success)
               {
                 Result[i] = new TaskItem(item.ItemSpec);
               }
             }
           }
         }
   ]]>
       </Code>
     </Task>
   </UsingTask>
   <Target Name="TestBuild">
     <RegX Expression="public|protected" Files="@(Compile)">
       <Output ItemName="MatchedFiles" TaskParameter="Result" />
     </RegX>
     <Message Text="Input files: @(Compile)" Importance="High" />
     <Message Text="Matched files: @(MatchedFiles)" Importance="High" />
   </Target>
   ```

2. Nella finestra **del prompt dei comandi** digitare **msbuild** senza opzioni di comando e quindi premere **INVIO.** Per impostazione predefinita, viene elaborata la destinazione predefinita TestBuild che richiama l'attività RegX.

3. Esaminare l'output nella **finestra del prompt dei comandi**. Dovrebbero essere visualizzate queste righe:

   ```
   Input files: Form1.cs;Form1.Designer.cs;Program.cs;Properties\AssemblyInfo.cs;Properties\Resources.Designer.cs;Properties\Settings.Designer.cs
   ```

   ```
   Matched files: Form1.cs;Form1.Designer.cs;Properties\Settings.Designer.cs
   ```

   Questo codice definisce un'attività inline denominata RegX che presenta i tre parametri seguenti:

- `Expression` è un parametro stringa di input obbligatorio il cui valore è l'espressione regolare rispetto a cui verificare la corrispondenza. In questo esempio, la verifica viene eseguita rispetto alle parole "public" e "protected".

- `Files` è un parametro di input obbligatorio di tipo elenco di elementi e il cui valore è un elenco di file in cui verificare la corrispondenza. In questo esempio `Files` viene impostato sull'elemento `Compile` che elenca i file di origine del progetto.

- `Result` è un parametro di output il cui valore è l'elenco dei file con un contenuto corrispondente all'espressione regolare.

  I valori dei parametri di input vengono impostati quando la destinazione TestBuild richiama l'attività RegX. L'attività RegX legge tutti i file e restituisce l'elenco di quelli che corrispondono all'espressione regolare. Questo elenco viene restituito tramite il parametro di output `Result`, che viene generato come elemento MSBuild denominato `MatchedFiles`.

### <a name="handle-reserved-characters"></a>Gestire caratteri riservati

 Il parser di MSBuild elabora le attività inline come codice XML. I caratteri con significato riservato in XML, ad esempio " ", vengono rilevati e gestiti come se fossero XML e non nel codice \<" and "> sorgente .NET. Per includere i caratteri riservati nelle espressioni di codice, ad esempio `Files.Length > 0`, scrivere l'elemento `Code` in modo che il relativo contenuto si trovi in un'espressione CDATA, come indicato di seguito:

 ```xml
<Code Type="Fragment" Language="cs">
  <![CDATA[

  if (Files.Length > 0)
  {
      // Your code goes here.
  }
  ]]>
</Code>
```

## <a name="see-also"></a>Vedi anche

- [Attività inline](../msbuild/msbuild-inline-tasks.md)
- [Attività](../msbuild/msbuild-tasks.md)
- [Server di destinazione](../msbuild/msbuild-targets.md)
