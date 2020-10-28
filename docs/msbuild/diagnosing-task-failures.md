---
title: Diagnosi degli errori delle attività | Microsoft Docs
description: Informazioni su come diagnosticare gli errori delle attività MSBuild identificando l'attività non riuscita, il nome dello strumento e altre informazioni.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: eaf55cc529be8fc61e05d1a76096e26d965aa136
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796472"
---
# <a name="diagnosing-task-failures"></a>Diagnosi degli errori delle attività

`MSB6006` viene generato quando una <xref:Microsoft.Build.Utilities.ToolTask> classe derivata da esegue un processo dello strumento che restituisce un codice di uscita diverso da zero se l'attività non registra un errore più specifico.

## <a name="identifying-the-failing-task"></a>Identificazione dell'attività non riuscita

Quando si verifica un errore di attività, il primo passaggio consiste nell'identificare l'attività che ha avuto esito negativo.

Il testo dell'errore specifica il nome dello strumento, ovvero un nome descrittivo fornito dall'implementazione dell'attività <xref:Microsoft.Build.Utilities.ToolTask.ToolName> o il nome del file eseguibile, e il codice di uscita numerico. Ad esempio, in

```text
error MSB6006: "custom tool" exited with code 1.
```

Il nome dello strumento è `custom tool` e il codice di uscita è `1` .

### <a name="command-line-builds"></a>Compilazioni da riga di comando

Se la compilazione è stata configurata in modo da includere un riepilogo (impostazione predefinita), il riepilogo sarà simile al seguente:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Questo risultato indica che l'errore si è verificato in un'attività definita alla riga 19 del file `S:\MSB6006_demo\MSB6006_demo.csproj` , in una destinazione denominata `InvokeToolTask` , nel progetto `S:\MSB6006_demo\MSB6006_demo.csproj` .

### <a name="in-visual-studio"></a>In Visual Studio

Le stesse informazioni sono disponibili nell'elenco errori di Visual Studio nelle colonne `Project` , `File` e `Line` .

## <a name="finding-more-failure-information"></a>Ricerca di ulteriori informazioni sugli errori

Questo errore viene generato quando l'attività non registra un errore specifico. La mancata registrazione di un errore è spesso dovuta al fatto che l'attività non è configurata per comprendere il formato di errore emesso dallo strumento chiamato.

Gli strumenti ben configurati in genere emettono informazioni contestuali o sugli errori nel flusso di output standard o di errore e le attività acquisiscono e registrano queste informazioni per impostazione predefinita. Esaminare le voci del log prima che si verifichi l'errore per ulteriori informazioni. Per conservare queste informazioni, potrebbe essere necessario rieseguire la compilazione con un livello di registrazione superiore.

## <a name="next-steps"></a>Passaggi successivi

Speriamo che il contesto aggiuntivo o gli errori identificati nella registrazione rivelino la causa principale del problema.

In caso contrario, potrebbe essere necessario limitare le possibili cause esaminando le proprietà e gli elementi che sono input per l'attività non riuscita.
