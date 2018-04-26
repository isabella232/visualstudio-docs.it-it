---
title: Finestra di progettazione del flusso di lavoro - debug dei flussi di lavoro da un Computer remoto (Legacy)
ms.date: 11/04/2016
ms.topic: conceptual
ms.prod: visual-studio-dev15
ms.technology: vs-workflow-designer
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 391180cd76fe5e0cccca802ba1cbfb78277dabc1
ms.sourcegitcommit: e13e61ddea6032a8282abe16131d9e136a927984
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/26/2018
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Esecuzione del debug dei flussi di lavoro da computer remoto (legacy)

In questo argomento viene descritto come eseguire il debug remoto Windows Workflow Foundation (WF) le applicazioni legacy che vengono compilate con la progettazione del flusso di lavoro Windows legacy. Utilizzare la finestra di progettazione del flusso di lavoro legacy quando l'applicazione deve avere come destinazione .NET Framework versione 3.5 o la WinFX.

 Quando si installa Visual Studio, è una delle opzioni di installazione del componente per l'installazione di Visual Studio del Debugger per Windows Workflow Foundation (WF). In questo modo vengono installati i componenti di debug remoto. Questi componenti di debug remoto devono essere installati nel computer nel quale si desidera eseguire il debug del flusso di lavoro remoto.

 Inoltre, l'assembly contenente la definizione del flusso di lavoro del flusso di lavoro legacy per il quale si sta eseguendo il debug in un computer remoto deve essere installato nella Global Assembly Cache (GAC) del computer locale dal quale si sta eseguendo il debug. Ad esempio, se un flusso di lavoro legacy è in esecuzione nel computer remoto A e si sta eseguendo il debug da un computer locale B, la definizione del flusso di lavoro deve essere presente nella GAC del computer B. Ciò consente alla finestra di progettazione di deserializzare e visualizzare sul computer B il markup del flusso di lavoro in esecuzione in modalità remota nel computer A. Per ulteriori informazioni sulla Global Assembly Cache, visitare il sito MSDN Library.

 Le funzioni di debug remoto di Windows Workflow Foundation funzionano come il debug remoto per altri componenti di Visual Studio. Per altre informazioni, vedere Visual Studio il debug remoto in MSDN Library.

## <a name="see-also"></a>Vedere anche

- [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)