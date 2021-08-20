---
title: Attività di MSBuild | Microsoft Docs
description: Informazioni su MSBuild usa attività o unità di codice eseguibile che eseguono operazioni di compilazione atomiche durante il processo di compilazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tasks
- MSBuild, tasks
ms.assetid: 5d3cc4a7-e5db-4f73-b707-8b6882fddcf8
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 949429136da49e562f6c7f24cb78391a0ceb021e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122108616"
---
# <a name="msbuild-tasks"></a>MSBuild (attività)

Una piattaforma di compilazione deve poter eseguire un numero illimitato di azioni durante il processo di compilazione. MSBuild usa *le attività* per eseguire queste azioni. Un'attività è un'unità di codice eseguibile usato MSBuild per eseguire operazioni di compilazione atomiche.

## <a name="task-logic"></a>Logica delle attività

 Il MSBuild file di progetto XML non può eseguire completamente le operazioni di compilazione, pertanto la logica dell'attività deve essere implementata all'esterno del file di progetto.

 La logica di esecuzione di un'attività viene implementata come classe .NET che implementa l'interfaccia <xref:Microsoft.Build.Framework.ITask>, definita nello spazio dei nomi <xref:Microsoft.Build.Framework>.

 La classe dell'attività definisce anche i parametri di input e di output disponibili per l'attività nel file di progetto. A tutte le proprietà non astratte non statiche impostabili pubbliche esposte dalla classe di attività è possibile assegnare valori nel file di progetto inserendo un attributo corrispondente con lo stesso nome nell'elemento [Task](../msbuild/task-element-msbuild.md) e impostandone il valore come illustrato negli esempi più avanti in questo articolo.

 Per scrivere un'attività personalizzata, è sufficiente creare una classe gestita che implementi l'interfaccia <xref:Microsoft.Build.Framework.ITask>. Per altre informazioni, vedere [Scrittura di attività.](../msbuild/task-writing.md)

## <a name="execute-a-task-from-a-project-file"></a>Esecuzione di un'attività da un file di progetto

 Prima di eseguire un'attività nel file di progetto, è necessario eseguire il mapping del tipo nell'assembly che implementa l'attività al nome dell'attività con l'elemento [UsingTask](../msbuild/usingtask-element-msbuild.md). Ciò consente MSBuild sapere dove cercare la logica di esecuzione dell'attività quando la trova nel file di progetto.

 Per eseguire un'attività in MSBuild file di progetto, creare un elemento con il nome dell'attività come figlio di un `Target` elemento . Se un'attività accetta i parametri, questi vengono passati come attributi dell'elemento.

 MSBuild gli elenchi di elementi e le proprietà possono essere usati come parametri. Ad esempio, il codice seguente chiama l'attività e imposta il valore della proprietà `MakeDir` `Directories` dell'oggetto `MakeDir` uguale al valore della proprietà `BuildDir` :

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

 MSBuild viene fornito con molte attività, ad esempio [Copia](../msbuild/copy-task.md), che copia i file, [MakeDir](../msbuild/makedir-task.md), che crea directory, e [Csc](../msbuild/csc-task.md), che compila i file di codice sorgente C#. Per un elenco completo delle attività disponibili e delle informazioni sull'utilizzo, vedere [Informazioni di riferimento sulle attività.](../msbuild/msbuild-task-reference.md)

## <a name="overridden-tasks"></a>Attività sottoposte a override

 MSBuild cerca le attività in diverse posizioni. Il primo percorso è in file con estensione *. OverrideTasks* archiviato nelle directory .NET Framework. Le attività in questi file eseguono l'override delle altre attività con gli stessi nomi, incluse le attività nel file di progetto. Il secondo percorso si trova nei file con estensione *. Attività* nelle .NET Framework directory. Se l'attività non è presente in nessuna di queste posizioni, viene usata l'attività nel file di progetto.

## <a name="see-also"></a>Vedi anche

- [Concetti relativi a MSBuild](../msbuild/msbuild-concepts.md)
- [MSBuild](../msbuild/msbuild.md)
- [Scrittura di attività](../msbuild/task-writing.md)
- [Attività inline](../msbuild/msbuild-inline-tasks.md)
