---
title: Diagnosi degli errori delle attività | Microsoft Docs
description: Informazioni su come diagnosticare MSBuild errori di attività identificando l'attività non riuscita, il nome dello strumento e altre informazioni.
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
manager: jmartens
ms.technology: msbuild
ms.workload:
- multiple
ms.openlocfilehash: 75ae93a5bf1b82d2101643512f2fa80da9d0271a51462181b7260c3652abdeed
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121370307"
---
# <a name="diagnosing-task-failures"></a>Diagnosi degli errori delle attività

`MSB6006` viene generato quando una classe derivata da esegue un processo dello strumento che restituisce un codice di uscita diverso da zero se l'attività non ha rilevato <xref:Microsoft.Build.Utilities.ToolTask> un errore più specifico.

## <a name="identifying-the-failing-task"></a>Identificazione dell'attività non riuscita

Quando si verifica un errore di attività, il primo passaggio consiste nell'identificare l'attività che ha esito negativo.

Il testo dell'errore specifica il nome dello strumento (un nome descrittivo fornito dall'implementazione dell'attività di o il nome dell'eseguibile) e il <xref:Microsoft.Build.Utilities.ToolTask.ToolName> codice di uscita numerico. Ad esempio, in

```text
error MSB6006: "custom tool" exited with code 1.
```

Il nome dello strumento è `custom tool` e il codice di uscita è `1` .

### <a name="command-line-builds"></a>Compilazioni da riga di comando

Se la compilazione è stata configurata per includere un riepilogo (impostazione predefinita), il riepilogo sarà simile al seguente:

```text
Build FAILED.

"S:\MSB6006_demo\MSB6006_demo.csproj" (default target) (1) ->
(InvokeToolTask target) ->
  S:\MSB6006_demo\MSB6006_demo.csproj(19,5): error MSB6006: "custom tool" exited with code 1.
```

Questo risultato indica che l'errore si è verificato in un'attività definita alla riga 19 del file , in una destinazione `S:\MSB6006_demo\MSB6006_demo.csproj` denominata , nel progetto `InvokeToolTask` `S:\MSB6006_demo\MSB6006_demo.csproj` .

### <a name="in-visual-studio"></a>In Visual Studio

Le stesse informazioni sono disponibili nell'Visual Studio degli errori nelle colonne `Project` `File` , e `Line` .

## <a name="finding-more-failure-information"></a>Ricerca di altre informazioni sugli errori

Questo errore viene generato quando l'attività non registra un errore specifico. La mancata registrazione di un errore è spesso dovuto al fatto che l'attività non è configurata per comprendere il formato di errore generato dallo strumento chiamato.

Gli strumenti ben comportati in genere generano informazioni contestuali o sugli errori nel flusso di output o di errore standard e le attività acquisiscono e registrano queste informazioni per impostazione predefinita. Per altre informazioni, esaminare le voci di log prima che si sia verificato l'errore. Potrebbe essere necessario rieseguire la compilazione con un livello di log superiore per mantenere queste informazioni.

## <a name="next-steps"></a>Passaggi successivi

Si spera che il contesto aggiuntivo o gli errori identificati nella registrazione rivelano la causa radice del problema.

In caso contrario, potrebbe essere necessario limitare le possibili cause esaminando le proprietà e gli elementi che sono input per l'attività non riuscita.
