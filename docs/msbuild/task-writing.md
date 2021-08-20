---
title: Scrittura di attività | Microsoft Docs
description: Informazioni su come creare attività proprie per fornire il codice eseguito durante il MSBuild di compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, writing tasks
- tasks, creating for MSBuild
- MSBuild, creating tasks
ms.assetid: 3ebc5f87-8f00-46fc-82a1-228f35a6823b
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: cb9d35c236210b9fa7eb1ceacfc5aa205b49ee70
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122142728"
---
# <a name="task-writing"></a>Scrittura di attività

Le attività forniscono il codice che viene eseguito durante il processo di compilazione. Le attività sono contenute nelle destinazioni. Una libreria di attività tipiche è inclusa in MSBuild ed è anche possibile creare attività proprie. Per altre informazioni sulla libreria di attività incluse in MSBuild, vedere Informazioni [di riferimento sulle attività](../msbuild/msbuild-task-reference.md).

## <a name="tasks"></a>Attività

 Esempi di attività includono [Copy](../msbuild/copy-task.md), che copia uno o più file, [MakeDir](../msbuild/makedir-task.md), che crea una directory, e [Csc](../msbuild/csc-task.md), che compila i file di codice sorgente C#. Ogni attività viene implementata come classe .NET che implementa l'interfaccia <xref:Microsoft.Build.Framework.ITask>, definita nell'assembly *Microsoft.Build.Framework.dll*.

 È possibile implementare un'attività in due modi:

- Implementare direttamente l'interfaccia <xref:Microsoft.Build.Framework.ITask>.

- Derivare la classe dalla classe di supporto <xref:Microsoft.Build.Utilities.Task>, definita nell'assembly *Microsoft.Build.Utilities.dll*. L'attività implementa ITask e specifica le implementazioni predefinite di alcuni membri di ITask. Inoltre, la registrazione è più semplice.

In entrambi i casi è necessario aggiungere alla classe un metodo denominato `Execute`, ovvero il metodo che viene chiamato quando l'attività è in esecuzione. Questo metodo non accetta parametri e restituisce un valore `Boolean`: `true` se l'attività ha avuto esito positivo o `false` se ha avuto esito negativo. Nell'esempio seguente viene illustrata un'attività che non esegue alcuna azione e restituisce `true`.

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }
    }
}
```

 Il file di progetto seguente esegue questa attività:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <Target Name="MyTarget">
        <SimpleTask />
    </Target>
</Project>
```

 Durante l'esecuzione, le attività possono anche ricevere input dal file di progetto se si creano proprietà .NET per la classe dell'attività. MSBuild queste proprietà immediatamente prima di chiamare il metodo `Execute` dell'attività. Per creare una proprietà stringa, usare il codice dell'attività, ad esempio:

```csharp
using System;
using Microsoft.Build.Framework;
using Microsoft.Build.Utilities;

namespace MyTasks
{
    public class SimpleTask : Task
    {
        public override bool Execute()
        {
            return true;
        }

        public string MyProperty { get; set; }
    }
}
```

 Il seguente file di progetto esegue questa attività e imposta `MyProperty` sul valore specificato:

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
   <Target Name="MyTarget">
      <SimpleTask MyProperty="Value for MyProperty" />
   </Target>
</Project>
```

## <a name="register-tasks"></a>Registrazione di attività

 Se un progetto eseguirà un'attività, MSBuild deve sapere come individuare l'assembly che contiene la classe di attività. Le attività vengono registrate usando l'[elemento UsingTask (MSBuild)](../msbuild/usingtask-element-msbuild.md).

 Il file MSBuild *Microsoft.Common.Tasks* è un file di progetto che contiene un elenco di elementi che registrano tutte le attività fornite con `UsingTask` MSBuild. Questo file è incluso automaticamente durante la compilazione di ogni progetto. Se un'attività registrata in *Microsoft.Common.Tasks* è registrata anche nel file di progetto corrente, il file di progetto corrente ha la precedenza, ovvero è possibile sostituire un'attività predefinita con un'attività personalizzata con lo stesso nome.

> [!TIP]
> È possibile visualizzare un elenco delle attività fornite con MSBuild visualizzando il contenuto di *Microsoft.Common.Tasks*.

## <a name="raise-events-from-a-task"></a>Generazione di eventi da un'attività

 Se l'attività deriva dalla classe helper <xref:Microsoft.Build.Utilities.Task>, è possibile usare uno qualsiasi dei seguenti metodi helper per la classe <xref:Microsoft.Build.Utilities.Task> per generare eventi che verranno intercettati e visualizzati da tutti i logger registrati:

```csharp
public override bool Execute()
{
    Log.LogError("messageResource1", "1", "2", "3");
    Log.LogWarning("messageResource2");
    Log.LogMessage(MessageImportance.High, "messageResource3");
    ...
}
```

 Se l'attività implementa <xref:Microsoft.Build.Framework.ITask> direttamente, è comunque possibile generare tali eventi, ma è necessario usare l'interfaccia IBuildEngine. Nell'esempio seguente viene illustrata un'attività che implementa ITask e genera un evento personalizzato:

```csharp
public class SimpleTask : ITask
{
    public IBuildEngine BuildEngine { get; set; }

    public override bool Execute()
    {
        TaskEventArgs taskEvent =
            new TaskEventArgs(BuildEventCategory.Custom,
            BuildEventImportance.High, "Important Message",
           "SimpleTask");
        BuildEngine.LogBuildEvent(taskEvent);
        return true;
    }
}
```

## <a name="require-task-parameters-to-be-set"></a>Richiesta dell'impostazione dei parametri dell'attività

 È possibile contrassegnare determinate proprietà dell'attività come "obbligatorie" in modo che i file di progetto che eseguono l'attività siano obbligati a impostare valori per queste proprietà altrimenti la compilazione non riesce. Applicare l'attributo `[Required]` alla proprietà .NET nell'attività come segue:

```csharp
[Required]
public string RequiredProperty { get; set; }
```

 L'attributo `[Required]` è definito da <xref:Microsoft.Build.Framework.RequiredAttribute> nello spazio dei nomi <xref:Microsoft.Build.Framework>.

## <a name="how-msbuild-invokes-a-task"></a>Come MSBuild richiama un'attività

Quando si richiama un'attività, MSBuild crea innanzitutto un'istanza della classe di attività, quindi chiama i setter di proprietà dell'oggetto per i parametri dell'attività impostati nell'elemento attività nel file di progetto. Se l'elemento attività non specifica un parametro o se l'espressione specificata nell'elemento restituisce una stringa vuota, il setter di proprietà non viene chiamato.

Ad esempio, nel progetto

```xml
<Project>
 <Target Name="InvokeCustomTask">
  <CustomTask Input1=""
              Input2="$(PropertyThatIsNotDefined)"
              Input3="value3" />
 </Target>
</Project>
```

viene chiamato solo il metodo `Input3` setter per .

Un'attività non deve dipendere da un ordine relativo di chiamata del setter di proprietà di parametro.

### <a name="task-parameter-types"></a>Tipi di parametri dell'attività

L MSBuild gestisce in modo nativo le proprietà di tipo `string` `bool` , e `ITaskItem` `ITaskItem[]` . Se un'attività accetta un parametro di un tipo diverso, MSBuild richiama per eseguire la conversione da (con tutti i riferimenti a proprietà ed elementi <xref:System.Convert.ChangeType%2A> espansi) al tipo di `string` destinazione. Se la conversione non riesce per qualsiasi parametro di input, MSBuild genera un errore e non chiama il metodo `Execute()` dell'attività.

## <a name="example-1"></a>Esempio 1

### <a name="description"></a>Descrizione

Questa classe C# seguente illustra un'attività che deriva dalla classe <xref:Microsoft.Build.Utilities.Task> helper. L'attività restituisce `true`, che indica che ha avuto esito positivo.

### <a name="code"></a>Codice

```csharp
using System;
using Microsoft.Build.Utilities;

namespace SimpleTask1
{
    public class SimpleTask1: Task
    {
        public override bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-2"></a>Esempio 2

### <a name="description"></a>Descrizione

Questa classe C# seguente illustra un'attività che implementa <xref:Microsoft.Build.Framework.ITask> l'interfaccia . L'attività restituisce `true`, che indica che ha avuto esito positivo.

### <a name="code"></a>Codice

```csharp
using System;
using Microsoft.Build.Framework;

namespace SimpleTask2
{
    public class SimpleTask2: ITask
    {
        //When implementing the ITask interface, it is necessary to
        //implement a BuildEngine property of type
        //Microsoft.Build.Framework.IBuildEngine. This is done for
        //you if you derive from the Task class.
        public IBuildEngine BuildEngine { get; set; }

        // When implementing the ITask interface, it is necessary to
        // implement a HostObject property of type object.
        // This is done for you if you derive from the Task class.
        public object HostObject { get; set; }

        public bool Execute()
        {
            // This is where the task would presumably do its work.
            return true;
        }
    }
}
```

## <a name="example-3"></a>Esempio 3

### <a name="description"></a>Descrizione

Questa classe C# illustra un'attività che deriva dalla classe <xref:Microsoft.Build.Utilities.Task> helper. Ha una proprietà stringa obbligatoria e genera un evento che viene visualizzato da tutti i logger registrati.

### <a name="code"></a>Codice

:::code language="csharp" source="../snippets/csharp/VS_Snippets_Misc/msbuild_SimpleTask3/CS/SimpleTask3.cs" id="Snippet1":::

## <a name="example-4"></a>Esempio 4

### <a name="description"></a>Descrizione

L'esempio seguente illustra un file di progetto che richiama l'attività dell'esempio precedente, SimpleTask3.

### <a name="code"></a>Codice

```xml
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <UsingTask TaskName="SimpleTask3.SimpleTask3"
        AssemblyFile="SimpleTask3\bin\debug\simpletask3.dll"/>

    <Target Name="MyTarget">
        <SimpleTask3 MyProperty="Hello!"/>
    </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
