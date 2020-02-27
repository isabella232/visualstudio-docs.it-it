---
title: Attività di MSBuild | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b065ea8cdaea2e2b39aa78a666ea0348f7b254ae
ms.sourcegitcommit: 96737c54162f5fd5c97adef9b2d86ccc660b2135
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2020
ms.locfileid: "77633135"
---
# <a name="msbuild-tasks"></a>MSBuild (attività)

Una piattaforma di compilazione deve poter eseguire un numero illimitato di azioni durante il processo di compilazione. MSBuild usa le *attività* per eseguire queste azioni. Un'attività è un'unità di codice eseguibile utilizzata da MSBuild per eseguire operazioni di compilazione atomiche.

## <a name="task-logic"></a>Logica delle attività

 Il formato del file di progetto XML di MSBuild non è in grado di eseguire completamente le operazioni di compilazione, pertanto la logica dell'attività deve essere implementata all'esterno del file di progetto.

 La logica di esecuzione di un'attività viene implementata come classe .NET che implementa l'interfaccia <xref:Microsoft.Build.Framework.ITask>, definita nello spazio dei nomi <xref:Microsoft.Build.Framework>.

 La classe dell'attività definisce anche i parametri di input e di output disponibili per l'attività nel file di progetto. A tutte le proprietà non statiche impostabili pubbliche esposte dalla classe di attività è possibile assegnare valori nel file di progetto inserendo un attributo corrispondente con lo stesso nome nell'elemento [Task](../msbuild/task-element-msbuild.md) e impostandone il valore come illustrato negli esempi più avanti in questo articolo.

 Per scrivere un'attività personalizzata, è sufficiente creare una classe gestita che implementi l'interfaccia <xref:Microsoft.Build.Framework.ITask>. Per altre informazioni, vedere [Scrittura di attività](../msbuild/task-writing.md).

## <a name="execute-a-task-from-a-project-file"></a>Esecuzione di un'attività da un file di progetto

 Prima di eseguire un'attività nel file di progetto, è necessario eseguire il mapping del tipo nell'assembly che implementa l'attività al nome dell'attività con l'elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). In questo modo, MSBuild sa dove cercare la logica di esecuzione dell'attività quando viene trovata nel file di progetto.

 Per eseguire un'attività in un file di progetto MSBuild, creare un elemento con il nome dell'attività come figlio di un elemento `Target`. Se un'attività accetta i parametri, questi vengono passati come attributi dell'elemento.

 Gli elenchi di elementi e le proprietà di MSBuild possono essere utilizzati come parametri. Il codice seguente, ad esempio, chiama l'attività `MakeDir` e imposta il valore della proprietà `Directories` dell'oggetto `MakeDir` uguale al valore della proprietà `BuildDir`:

```xml
<Target Name="MakeBuildDirectory">
    <MakeDir
        Directories="$(BuildDir)" />
</Target>
```

 Le attività possono anche restituire informazioni al file di progetto, che è possibile archiviare in elementi o proprietà per un uso futuro. Il codice seguente, ad esempio, chiama l'attività `Copy` e archivia le informazioni dalla proprietà di output `CopiedFiles` nell'elenco di elementi `SuccessfullyCopiedFiles`.

```xml
<Target Name="CopyFiles">
    <Copy
        SourceFiles="@(MySourceFiles)"
        DestinationFolder="@(MyDestFolder)">
        <Output
            TaskParameter="CopiedFiles"
            ItemName="SuccessfullyCopiedFiles"/>
     </Copy>
</Target>
```

## <a name="included-tasks"></a>Attività incluse

 MSBuild viene fornito con molte attività, ad esempio [Copy](../msbuild/copy-task.md), che copia i file, [MakeDir](../msbuild/makedir-task.md), che creano le directory e [CSC](../msbuild/csc-task.md), C# che compila i file del codice sorgente. Per un elenco completo delle attività disponibili e informazioni sull'uso, vedere [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md).

## <a name="overridden-tasks"></a>Attività sottoposte a override

 MSBuild cerca le attività in diverse posizioni. La prima posizione sono i file con estensione *OverrideTasks* archiviati nelle directory di .NET Framework. Le attività in questi file eseguono l'override delle altre attività con gli stessi nomi, incluse le attività nel file di progetto. La seconda posizione sono i file con estensione *Tasks* archiviati nelle directory di .NET Framework. Se l'attività non è presente in nessuna di queste posizioni, viene usata l'attività nel file di progetto.

## <a name="see-also"></a>Vedere anche

- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Scrittura di attività](../msbuild/task-writing.md)
- [Attività inline](../msbuild/msbuild-inline-tasks.md)
