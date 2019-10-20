---
title: Debug di flussi di lavoro da un computer remoto (legacy) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, debugging remotely
- debugging workflows, remotely
- remote debugging, workflows
- debugging, remote
ms.assetid: 44eaec8f-9959-4ae7-a374-670946f933c1
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: bce98714832042471145bcf7d908a62b15bdb144
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656850"
---
# <a name="debugging-workflows-from-a-remote-computer-legacy"></a>Esecuzione del debug dei flussi di lavoro da computer remoto (legacy)
In questo argomento viene descritto come eseguire il debug di applicazioni [!INCLUDE[wf](../includes/wf-md.md)] legacy remote che sono compilate con la [!INCLUDE[wfd1](../includes/wfd1-md.md)] legacy. Usare la [!INCLUDE[wfd2](../includes/wfd2-md.md)] legacy quando l'applicazione deve fare riferimento a [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

 Quando si installa [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)], una delle opzioni di installazione dei componenti prevede l'installazione del debugger [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] per [!INCLUDE[wf](../includes/wf-md.md)]. In questo modo vengono installati i componenti di debug remoto. Questi componenti di debug remoto devono essere installati nel computer nel quale si desidera eseguire il debug del flusso di lavoro remoto.

 Inoltre, l'assembly contenente la definizione del flusso di lavoro del flusso di lavoro legacy per il quale si sta eseguendo il debug in un computer remoto deve essere installato nella Global Assembly Cache (GAC) del computer locale dal quale si sta eseguendo il debug. Ad esempio, se un flusso di lavoro legacy è in esecuzione nel computer remoto A e si sta eseguendo il debug da un computer locale B, la definizione del flusso di lavoro deve essere presente nella GAC del computer B. Ciò consente alla finestra di progettazione di deserializzare e visualizzare sul computer B il markup del flusso di lavoro in esecuzione in modalità remota nel computer A. Per ulteriori informazioni sulla Global Assembly Cache, visitare il sito MSDN Library.

 Il debug remoto di [!INCLUDE[wf2](../includes/wf2-md.md)] funziona nello stesso modo del debug remoto per altri componenti [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Per ulteriori informazioni, vedere [!INCLUDE[vs_current_long](../includes/vs-current-long-md.md)] debug remoto in MSDN Library.

## <a name="see-also"></a>Vedere anche
 [Debug dei flussi di lavoro legacy](../workflow-designer/debugging-legacy-workflows.md)