---
title: Attività inline di MSBuild con RoslynCodeTaskFactory | Microsoft Docs
description: Informazioni su MSBuild RoslynCodeTaskFactory, che usa i compilatori Roslyn multipiattaforma per generare assembly di attività in memoria da usare come attività inline.
ms.custom: SEO-VS-2020
ms.date: 09/21/2017
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, tasks
ms.assetid: e72e6506-4a11-4edf-ae8d-cfb5a3b9d8a0
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: a926dbfd746978d1e37e772ddee3eb2ec07d08ae
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122068865"
---
# <a name="msbuild-inline-tasks-with-roslyncodetaskfactory"></a>Attività inline di MSBuild con RoslynCodeTaskFactory

Analogamente all'attività [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md), l'attività RoslynCodeTaskFactory usa i compilatori Roslyn multipiattaforma per generare assembly di attività in memoria da usare come attività inline.  Le attività RoslynCodeTaskFactory, destinate a .NET Standard, possono funzionare nei runtime di .NET Framework e .NET Core, nonché in altre piattaforme quali Linux e Mac OS.

>[!NOTE]
>RoslynCodeTaskFactory è disponibile solo in MSBuild 15.8 e versioni successive. MSBuild versioni successive Visual Studio, quindi RoslynCodeTaskFactory è disponibile in Visual Studio 2017 versione 15.8 e successive.

## <a name="the-structure-of-an-inline-task-with-roslyncodetaskfactory"></a>Struttura di un'attività inline con RoslynCodeTaskFactory

 Le attività inline RoslynCodeTaskFactory vengono dichiarate nello stesso modo delle attività [CodeTaskFactory](../msbuild/msbuild-inline-tasks.md). L'unica differenza è che le prime sono destinate a .NET Standard.  L'attività inline e l'elemento `UsingTask` che la contiene sono generalmente inclusi in un file con estensione *targets* e all'occorrenza vengono importati in altri file di progetto. Di seguito è riportata un'attività inline di base. Si noti che non esegue alcuna operazione.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task does nothing. -->
  <UsingTask
    TaskName="DoNothing"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="" />
      <Using Namespace="" />
      <Code Type="Fragment" Language="cs">
      </Code>
    </Task>
  </UsingTask>
</Project>
```

 L'elemento `UsingTask` nell'esempio ha tre attributi che descrivono l'attività e la factory dell'attività inline che la compila.

- L'attributo `TaskName` assegna un nome all'attività, in questo caso `DoNothing`.

- L'attributo `TaskFactory` assegna un nome alla classe che implementa la factory dell'attività inline.

- L'attributo `AssemblyFile` assegna la posizione della factory dell'attività inline. In alternativa, è possibile usare l'attributo `AssemblyName` per specificare il nome completo della classe factory dell'attività inline, che in genere si trova nella Global Assembly Cache (GAC).

Gli elementi rimanenti dell'attività `DoNothing` sono vuoti e vengono specificati per illustrare l'ordine e la struttura di un'attività inline. Un esempio più concreto è riportato più avanti in questo argomento.

- L'elemento `ParameterGroup` è facoltativo. Se specificato, consente di dichiarare i parametri per l'attività. Per altre informazioni sui parametri di input e output, vedere [Parametri di input e output](#input-and-output-parameters) più avanti in questo argomento.

- L'elemento `Task` descrive e contiene il codice sorgente dell'attività.

- L'elemento `Reference` specifica i riferimenti agli assembly .NET usati nel codice. Equivale all'aggiunta di un riferimento a un progetto in Visual Studio. L'attributo `Include` specifica il percorso dell'assembly di riferimento.

- L'elemento `Using` indica gli spazi dei nomi a cui si vuole accedere. Ricorda l'istruzione `Using` in Visual C#. L'attributo `Namespace` specifica lo spazio dei nomi da includere.

Gli elementi `Reference` e `Using` sono indipendenti dal linguaggio di programmazione. Le attività inline possono essere scritte in uno dei linguaggi .NET CodeDOM supportati, ad esempio Visual Basic, Visual C#.

> [!NOTE]
> Gli elementi contenuti in `Task` sono specifici della factory dell'attività, in questo caso la factory dell'attività del codice.

### <a name="code-element"></a>Elemento del codice

L'ultimo elemento figlio visualizzato all'interno dell'elemento `Task` è l'elemento `Code`. L'elemento `Code` contiene o individua il codice che deve essere compilato in un'attività. Ciò che si inserisce nell'elemento `Code` dipende da come si vuole scrivere l'attività.

L'attributo `Language` specifica il linguaggio di programmazione in cui è scritto il codice. I valori accettabili sono `cs` per C#, `vb` per Visual Basic.

L'attributo `Type` specifica il tipo di codice rilevato nell'elemento `Code`.

- Se il valore di `Type` è `Class`, l'elemento `Code` contiene il codice per una classe che deriva dall'interfaccia <xref:Microsoft.Build.Framework.ITask>.

- Se il valore di `Type` è `Method`, il codice definisce un override del metodo `Execute` dell'interfaccia <xref:Microsoft.Build.Framework.ITask>.

- Se il valore di `Type` è `Fragment`, il codice definisce il contenuto del metodo `Execute` ma non la firma o l'istruzione `return`.

Il codice in genere è visualizzato tra un indicatore `<![CDATA[` e un indicatore `]]>`. Poiché il codice si trova in una sezione CDATA, non è necessario preoccuparsi dell'escape dei caratteri riservati, ad esempio " \<" or "> ".

In alternativa, è possibile usare l'attributo `Source` dell'elemento `Code` per specificare il percorso di un file che contiene il codice per l'attività. Il codice nel file di origine deve essere del tipo specificato dall'attributo `Type`. Se l'attributo `Source` è presente, il valore predefinito di `Type` è `Class`. Se `Source` non è presente, il valore predefinito è `Fragment`.

> [!NOTE]
> Quando si definisce la classe dell'attività nel file di origine il nome della classe deve concordare con l'attributo `TaskName` dell'elemento [UsingTask](../msbuild/usingtask-element-msbuild.md) corrispondente.

## <a name="hello-world"></a>Hello World

 Di seguito è riportata un'attività inline più efficiente con RoslynCodeTaskFactory. L'attività HelloWorld visualizza "Hello, world!" nel dispositivo di registrazione degli errori predefinito, in genere la console del sistema o la finestra **Output** di Visual Studio. L'elemento `Reference` dell'esempio è incluso solo ai fini della spiegazione.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <!-- This simple inline task displays "Hello, world!" -->
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="RoslynCodeTaskFactory"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll" >
    <ParameterGroup />
    <Task>
      <Reference Include="System.Xml"/>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
<![CDATA[
// Display "Hello, world!"
Log.LogError("Hello, world!");
]]>
      </Code>
    </Task>
  </UsingTask>
</Project>
```

È possibile salvare l'attività HelloWorld in un file denominato *HelloWorld.targets* e richiamarla da un progetto come indicato di seguito.

```xml
<Project ToolsVersion="15.0" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
  <Import Project="HelloWorld.targets" />
  <Target Name="Hello">
    <HelloWorld />
  </Target>
</Project>
```

## <a name="input-and-output-parameters"></a>Parametri di input e output

 I parametri dell'attività inline sono elementi figlio di un elemento `ParameterGroup`. Ogni parametro accetta il nome dell'elemento che lo definisce. Il codice seguente definisce il parametro `Text`.

```xml
<ParameterGroup>
    <Text />
</ParameterGroup>
```

I parametri possono avere uno o più degli attributi seguenti:

- `Required` è un attributo facoltativo che è `false` per impostazione predefinita. Se `true`, il parametro è obbligatorio e deve avere un valore assegnato prima di chiamare l'attività.

- `ParameterType` è un attributo facoltativo che è `System.String` per impostazione predefinita. Può essere impostato su qualsiasi tipo completo che sia un elemento o un valore che può essere convertito in e da una stringa usando System.Convert.ChangeType. In altre parole, qualsiasi tipo che può essere passato a e da un'attività esterna.

- `Output` è un attributo facoltativo che è `false` per impostazione predefinita. Se `true`, il parametro deve avere un valore assegnato prima della restituzione da parte del metodo Execute.

Ad esempio,

```xml
<ParameterGroup>
    <Expression Required="true" />
    <Files ParameterType="Microsoft.Build.Framework.ITaskItem[]" Required="true" />
    <Tally ParameterType="System.Int32" Output="true" />
</ParameterGroup>
```

definisce questi tre parametri:

- `Expression` è un parametro di input obbligatorio del tipo System.String.

- `Files` è un parametro di input obbligatorio dell'elenco di elementi.

- `Tally` è un parametro di output del tipo System.Int32.

Se l'elemento `Code` ha come attributo `Type``Fragment` o `Method`, le proprietà vengono create automaticamente per ogni parametro.  In RoslynCodeTaskFactory, se l'elemento ha l'attributo , non è necessario specificare , perché viene dedotto dal codice sorgente (si tratta di una differenza rispetto `Code` `Type` a `Class` `ParameterGroup` `CodeTaskFactory` ). In caso contrario, le proprietà devono essere dichiarate in modo esplicito nel codice sorgente dell'attività e devono corrispondere esattamente alle relative definizioni di parametro.

## <a name="example"></a>Esempio

 L'attività inline seguente registra alcuni messaggi e restituisce una stringa.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="MySample"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Parameter1 ParameterType="System.String" Required="true" />
            <Parameter2 ParameterType="System.String" />
            <Parameter3 ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
              <![CDATA[
              Log.LogMessage(MessageImportance.High, "Hello from an inline task created by Roslyn!");
              Log.LogMessageFromText($"Parameter1: '{Parameter1}'", MessageImportance.High);
              Log.LogMessageFromText($"Parameter2: '{Parameter2}'", MessageImportance.High);
              Parameter3 = "A value from the Roslyn CodeTaskFactory";
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
      <MySample Parameter1="A value for parameter 1" Parameter2="A value for parameter 2">
          <Output TaskParameter="Parameter3" PropertyName="NewProperty" />
      </MySample>

      <Message Text="NewProperty: '$(NewProperty)'" />
    </Target>
</Project>
```

Queste attività inline possono combinare i percorsi e ottenere il nome del file.

```xml
<Project xmlns='http://schemas.microsoft.com/developer/msbuild/2003' ToolsVersion="15.0">

    <UsingTask TaskName="PathCombine"
               TaskFactory="RoslynCodeTaskFactory"
               AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Paths ParameterType="System.String[]" Required="true" />
            <Combined ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            Combined = Path.Combine(Paths);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <UsingTask TaskName="PathGetFileName"
             TaskFactory="RoslynCodeTaskFactory"
             AssemblyFile="$(MSBuildBinPath)\Microsoft.Build.Tasks.Core.dll">
        <ParameterGroup>
            <Path ParameterType="System.String" Required="true" />
            <FileName ParameterType="System.String" Output="true" />
        </ParameterGroup>
        <Task>
            <Using Namespace="System" />
            <Code Type="Fragment" Language="C#">
            <![CDATA[
            FileName = System.IO.Path.GetFileName(Path);
            ]]>
            </Code>
        </Task>
    </UsingTask>

    <Target Name="Demo">
        <PathCombine Paths="$(Temp);MyFolder;$([System.Guid]::NewGuid()).txt">
            <Output TaskParameter="Combined" PropertyName="MyCombinedPaths" />
        </PathCombine>

        <Message Text="Combined Paths: '$(MyCombinedPaths)'" />

        <PathGetFileName Path="$(MyCombinedPaths)">
            <Output TaskParameter="FileName" PropertyName="MyFileName" />
        </PathGetFileName>

        <Message Text="File name: '$(MyFileName)'" />
    </Target>
</Project>
```

## <a name="provide-backward-compatibility"></a>Garantire la compatibilità con le versioni precedenti

`RoslynCodeTaskFactory`è diventato disponibile per la MSBuild versione 15.8. Si supponga di voler supportare le versioni precedenti di Visual Studio e MSBuild, quando non era disponibile, ma lo era, ma si vuole usare lo stesso `RoslynCodeTaskFactory` `CodeTaskFactory` script di compilazione. È possibile usare un costrutto che usa la proprietà per decidere in fase di compilazione se usare o eseguire il `Choose` fall back a , come `$(MSBuildVersion)` `RoslynCodeTaskFactory` `CodeTaskFactory` nell'esempio seguente:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <Choose>
    <When Condition=" '$(MSBuildVersion.Substring(0,2))' >= 16 Or
    ('$(MSBuildVersion.Substring(0,2))' == 15 And '$(MSBuildVersion.Substring(3,1))' >= 8)">
      <PropertyGroup>
        <TaskFactory>RoslynCodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </When>
    <Otherwise>
      <PropertyGroup>
        <TaskFactory>CodeTaskFactory</TaskFactory>
      </PropertyGroup>
    </Otherwise>
  </Choose>
  
  <UsingTask
    TaskName="HelloWorld"
    TaskFactory="$(TaskFactory)"
    AssemblyFile="$(MSBuildToolsPath)\Microsoft.Build.Tasks.Core.dll">
    <ParameterGroup />
    <Task>
      <Using Namespace="System"/>
      <Using Namespace="System.IO"/>
      <Code Type="Fragment" Language="cs">
        <![CDATA[
         Log.LogError("Using RoslynCodeTaskFactory");
      ]]>
      </Code>
    </Task>
  </UsingTask>

  <Target Name="RunTask" AfterTargets="Build">
    <Message Text="MSBuildVersion: $(MSBuildVersion)"/>
    <Message Text="TaskFactory: $(TaskFactory)"/>
    <HelloWorld />
  </Target>

</Project>
```

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Procedura dettagliata: Creare un'attività inline](../msbuild/walkthrough-creating-an-inline-task.md)
