---
title: Diagnosi degli errori delle attività Documenti Microsoft
ms.date: 09/25/2019
ms.topic: troubleshooting
f1_keywords:
- MSBuild.ToolTask.ToolCommandFailed
dev_langs:
- VB
- CSharp
- C++
- jsharp
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 89dcb8bddf2c92406ad5eff952d1f4050d7f9262
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593278"
---
# <a name="diagnosing-task-failures"></a>Diagnosi degli errori delle attività

`MSB6006`viene generato quando <xref:Microsoft.Build.Utilities.ToolTask>una classe derivata viene eseguita un processo dello strumento che restituisce un codice di uscita diverso da zero se l'attività non ha riportato un errore più specifico.

## <a name="identifying-the-failing-task"></a>Identificazione dell'attività non riuscita

Quando si verifica un errore di attività, il primo passaggio consiste nell'identificare l'attività che non riesce.

Il testo dell'errore specifica il nome dello strumento (un nome <xref:Microsoft.Build.Utilities.ToolTask.ToolName> descrittivo fornito dall'implementazione dell'attività o dal nome dell'eseguibile) e il codice di uscita numerico. Ad esempio, in

```text
error MSB6006: "custom tool" exited with code 1.
```

Il nome `custom tool` dello strumento è `1`e il codice di uscita è .

### <a name="command-line-builds"></a>Compilazioni da riga di comando

Se la compilazione è stata configurata per includere un riepilogo (impostazione predefinita), il riepilogo sarà simile al seguente:If the build was configured to include a summary (the default), the summary will look like this:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Questo risultato indica che l'errore si è verificato `S:\MSB6006_demo\MSB6006_demo.csproj`in un'attività `InvokeToolTask`definita nella `S:\MSB6006_demo\MSB6006_demo.csproj`riga 19 del file, in una destinazione denominata , nel progetto .

### <a name="in-visual-studio"></a>In Visual Studio

Le stesse informazioni sono disponibili nell'elenco `Project`degli `File`errori `Line`di Visual Studio nelle colonne , , e .

## <a name="finding-more-failure-information"></a>Ricerca di ulteriori informazioni sui guasti

Questo errore viene generato quando l'attività non ha rilevato un errore specifico. L'errore di registrazione di un errore è spesso dovuto al fatto che l'attività non è configurata per comprendere il formato di errore generato dallo strumento che chiama.

Gli strumenti ben gestiti in genere generano alcune informazioni contestuali o di errore nel loro output standard o flusso di errore e le attività acquisiscono e registrano queste informazioni per impostazione predefinita. Cercare ulteriori informazioni nelle voci di registro. Per mantenere queste informazioni, potrebbe essere necessario rieseguire la compilazione con un livello di log superiore.

## <a name="next-steps"></a>Passaggi successivi

Speriamo che il contesto aggiuntivo o gli errori identificati nella registrazione rivelino la causa principale del problema.

In caso contrario, potrebbe essere necessario limitare le possibili cause esaminando le proprietà e gli elementi che sono input per l'attività non riuscita.
