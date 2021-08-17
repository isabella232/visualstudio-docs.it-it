---
title: 'Procedura: Ignorare gli errori nelle attività | Microsoft Docs'
description: Informazioni su come ignorare gli errori nelle MSBuild e controllare se una compilazione viene arrestata o continua quando si verifica un errore dell'attività.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, ignoring errors
- ContinueOnError attribute [MSBuild]
ms.assetid: e2f1ca4f-787b-44bd-bc64-81a036025e96
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: msbuild
ms.openlocfilehash: 3f40805c7798fbd4e93a0467ef6137d2ea0956d481821db25efb475a41e1a149
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121397657"
---
# <a name="how-to-ignore-errors-in-tasks"></a>Procedura: Ignorare gli errori nelle attività

A volte è necessario che una compilazione sia a tolleranza di errore in determinate attività. Se tali attività non critiche hanno esito negativo, si vuole che la compilazione prosegua perché può ugualmente produrre l'output necessario. Se, ad esempio, un progetto usa un'attività `SendMail` per inviare un messaggio di posta elettronica dopo che ogni componente è stato compilato, si può considerare accettabile che la compilazione continui fino al completamento anche quando i server di posta non sono disponibili e i messaggi di stato non possono essere inviati. O anche, ad esempio, se di solito i file intermedi vengono eliminati durante la compilazione, si può considerare accettabile che la compilazione continui fino al completamento anche quando tali file non possono essere eliminati.

## <a name="use-the-continueonerror-attribute"></a>Usare l'attributo ContinueOnError

L'attributo `ContinueOnError` dell'elemento `Task` controlla se una compilazione si arresta o continua quando si verifica un errore dell'attività. Questo attributo controlla anche se gli errori vengono considerati errori o avvisi quando la compilazione continua.

L'attributo `ContinueOnError` può contenere uno dei valori seguenti:

- **WarnAndContinue** o **true**. Quando un'attività ha esito negativo, le attività successive [nell'elemento Target](../msbuild/target-element-msbuild.md) e nella compilazione continuano a essere eseguite e tutti gli errori dell'attività vengono considerati avvisi.

- **ErrorAndContinue**. Quando un'attività ha esito negativo, l'esecuzione delle attività successive nell'elemento `Target` e della compilazione continua e tutti gli errori delle attività vengono considerati errori.

- **ErrorAndStop** o **false** (impostazione predefinita). Quando un'attività ha esito negativo, le attività rimanenti nell'elemento `Target` e la compilazione non vengono eseguite e l'intero elemento `Target` e la compilazione vengono considerati come non riusciti.

Le versioni di .NET Framework precedenti alla 4.5 supportano solo i valori `true` e `false`.

Il valore predefinito di `ContinueOnError` è `ErrorAndStop`. Se si imposta l'attributo su `ErrorAndStop`, il comportamento diventa esplicito per chiunque legga il file di progetto.

#### <a name="to-ignore-an-error-in-a-task"></a>Per ignorare un errore in un'attività

Usare l'attributo `ContinueOnError` dell'attività. Esempio:

```xml
<Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
```

## <a name="example"></a>Esempio

L'esempio di codice seguente mostra che la destinazione `Build` è ancora in esecuzione e che la compilazione è considerata riuscita, anche se l'attività `Delete` ha esito negativo.

```xml
<Project DefaultTargets="FakeBuild"
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">
    <ItemGroup>
        <Files Include="*.obj"/>
    </ItemGroup>
    <Target Name="Clean">
        <Delete Files="@(Files)" ContinueOnError="WarnAndContinue"/>
    </Target>

    <Target Name="FakeBuild" DependsOnTargets="Clean">
        <Message Text="Building after cleaning..."/>
    </Target>
</Project>
```

## <a name="see-also"></a>Vedi anche

- [MSBuild](../msbuild/msbuild.md)
- [Informazioni di riferimento sulle attività](../msbuild/msbuild-task-reference.md)
- [Attività](../msbuild/msbuild-tasks.md)
