---
title: Elemento UsingTask (MSBuild) | Microsoft Docs
ms.date: 03/13/2017
ms.topic: reference
f1_keywords:
- http://schemas.microsoft.com/developer/msbuild/2003#UsingTask
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- UsingTask element [MSBuild]
- <UsingTask> element [MSBuild]
ms.assetid: 20247902-9446-4a1f-8253-5c7a17e4fe43
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 14556467e0907818333695b3388b2d11f3467ed7
ms.sourcegitcommit: 1d4f6cc80ea343a667d16beec03220cfe1f43b8e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/23/2020
ms.locfileid: "85289157"
---
# <a name="usingtask-element-msbuild"></a>Elemento UsingTask (MSBuild)

Associa l'attività a cui si fa riferimento in un elemento [Task](../msbuild/task-element-msbuild.md) all'assembly che contiene l'implementazione dell'attività.

 \<Project> \<UsingTask>

## <a name="syntax"></a>Sintassi

```xml
<UsingTask TaskName="TaskName"
    AssemblyName = "AssemblyName"
    TaskFactory = "ClassName"
    Condition="'String A'=='String B'" />
```

> [!NOTE]
> A differenza di proprietà ed elementi, verrà usato il *primo* `UsingTask` elemento che si applica a un oggetto `TaskName` . per eseguire l'override delle attività è necessario definire un nuovo `UsingTask` *prima* di quello esistente.

## <a name="attributes-and-elements"></a>Attributi ed elementi

 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.

### <a name="attributes"></a>Attributi

|Attributo|Descrizione|
|---------------|-----------------|
|`Architecture`|Attributo facoltativo.<br /><br /> Specifica che l'attività deve essere eseguita in un processo del bit specificato. Se il processo corrente non soddisfa il requisito, l'attività verrà eseguita in un processo host delle attività che lo esegue.<br /><br /> I valori supportati sono `x86` (32 bit), `x64` (64-bit), `CurrentArchitecture` e `*` (qualsiasi architettura).|  
|`AssemblyName`|Sono obbligatori sia l'attributo `AssemblyName` che l'attributo `AssemblyFile`.<br /><br /> Nome dell'assembly da caricare. L'attributo `AssemblyName` accetta assembly con nome sicuro, anche se non è obbligatorio un nome sicuro. L'uso di questo attributo equivale a caricare un assembly usando il metodo <xref:System.Reflection.Assembly.Load%2A> in .NET.<br /><br /> Non è possibile usare questo attributo se viene usato l'attributo `AssemblyFile`.|
|`AssemblyFile`|È obbligatorio l'attributo `AssemblyName` o l'attributo `AssemblyFile`.<br /><br /> Percorso del file dell'assembly. Questo attributo accetta percorsi completi o percorsi relativi. I percorsi relativi sono relativi alla directory del file di progetto o file di destinazioni in cui viene dichiarato l'elemento `UsingTask`. L'uso di questo attributo equivale a caricare un assembly usando il metodo <xref:System.Reflection.Assembly.LoadFrom%2A> in .NET.<br /><br /> Non è possibile usare questo attributo se viene usato l'attributo `AssemblyName`.|
|`Runtime`|Attributo facoltativo.<br /><br /> Specifica che l'attività deve essere eseguita in un .NET Framework Runtime della versione specificata. Se il processo corrente non soddisfa il requisito, l'attività verrà eseguita in un processo host delle attività che lo esegue. Non supportato in MSBuild di .NET Core.<br /><br /> I valori supportati sono `CLR2` (.NET Framework 3,5), `CLR4` (.NET Framework 4.7.2 o versione successiva), `CurrentRuntime` e `*` (qualsiasi Runtime).|  
|`TaskFactory`|Attributo facoltativo.<br /><br /> Specifica la classe nell'assembly responsabile della generazione di istanze del nome `Task` specificato.  L'utente può specificare anche un elemento figlio `Task` che la factory delle attività riceve e usa per generare l'attività. I contenuti dell'elemento `Task` sono specifici per la factory delle attività.|
|`TaskName`|Attributo obbligatorio.<br /><br /> Il nome dell'attività a cui fare riferimento da un assembly. In caso di ambiguità, questo attributo deve specificare sempre gli spazi dei nomi completi. In caso di ambiguità, MSBuild sceglie una corrispondenza arbitraria, con potenziali risultati imprevisti.|
|`Condition`|Attributo facoltativo.<br /><br /> La condizione da valutare. Per altre informazioni, vedere [Condizioni](../msbuild/msbuild-conditions.md).|

### <a name="child-elements"></a>Elementi figlio

|Elemento|Description|
|-------------|-----------------|
|[ParameterGroup](../msbuild/parametergroup-element.md)|Il set di parametri visualizzati nell'attività generata dall'elemento `TaskFactory` specificato.|
|[Attività](../msbuild/task-element-msbuild.md)|I dati che vengono passati all'elemento `TaskFactory` per generare un'istanza dell'attività.|

### <a name="parent-elements"></a>Elementi padre

| Elemento | Description |
| - | - |
| [Project](../msbuild/project-element-msbuild.md) | Elemento radice obbligatorio di un file di progetto MSBuild. |

## <a name="remarks"></a>Commenti

 È possibile fare riferimento alle variabili di ambiente, alle proprietà della riga di comando, alle proprietà a livello di progetto e agli elementi a livello di progetto negli elementi `UsingTask` inclusi nel file di progetto sia direttamente che tramite un file di progetto importato. Per altre informazioni, vedere [Tasks](../msbuild/msbuild-tasks.md) (Attività).

> [!NOTE]
> Le proprietà e gli elementi a livello di progetto non hanno alcun effetto se l'elemento `UsingTask` proviene da uno dei file con estensione *tasks* registrati a livello globale nel motore MSBuild. I valori a livello di progetto non sono globali per MSBuild.

 In MSBuild 4.0 è possibile caricare gli elementi UsingTask dai file con estensione *overridetask*.

L'assembly contenente l'attività personalizzata viene caricato quando `Task` viene utilizzato per la prima volta.

## <a name="example"></a>Esempio

 L'esempio seguente illustra come usare l'elemento `UsingTask` con un attributo `AssemblyName`.

```xml
<UsingTask TaskName="MyTask" AssemblyName="My.Assembly" TaskFactory="MyTaskFactory">
       <ParameterGroup>
              <Parameter1 ParameterType="System.String" Required="False" Output="False"/>
              <Parameter2 ParameterType="System.Int" Required="True" Output="False"/>
              ...
</ParameterGroup>
       <Task>
      ... Task factory-specific data ...
       </Task>
</UsingTask>
```

## <a name="example"></a>Esempio

 L'esempio seguente illustra come usare l'elemento `UsingTask` con un attributo `AssemblyFile`.

```xml
<UsingTask TaskName="Email"
              AssemblyFile="c:\myTasks\myTask.dll" />
```

## <a name="see-also"></a>Vedi anche

- [Attività](../msbuild/msbuild-tasks.md)
- [Procedura: configurare destinazioni e attività](../msbuild/how-to-configure-targets-and-tasks.md)   
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Riferimento allo schema del file di progetto](../msbuild/msbuild-project-file-schema-reference.md)
