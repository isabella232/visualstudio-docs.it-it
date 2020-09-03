---
title: Trovare problemi potenziali usando gli analizzatori di mappe codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.progression.codemapanalyzers
helpviewer_keywords:
- code analysis, dependency graphs
- dependency graphs, analyzing code
- graph documents, analyzing
ms.assetid: 9dd799a7-f7eb-42ff-8612-b19dde7ff4eb
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fc5d185640c9623a2213aaf7ad50fa68a088b15c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72669625"
---
# <a name="find-potential-problems-using-code-map-analyzers"></a>Trovare problemi potenziali usando gli analizzatori di mappe codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Eseguire gli analizzatori sulle mappe codice per identificare il codice che potrebbe essere eccessivamente complesso o che potrebbe richiedere un miglioramento. È possibile, ad esempio, usare gli analizzatori seguenti:

|**Per trovare codice con**|**Esaminare queste aree per vedere se**|
|-------------------------------|--------------------------------------------|
|Cicli o dipendenze circolari|È possibile semplificarli e stabilire se è possibile interrompere questi cicli.|
|Troppe dipendenze|Sono in esecuzione troppe funzioni o per determinare l'impatto della modifica di queste aree. Una mappa del codice corretto mostra un numero minimo di dipendenze. Per rendere il codice più facile da gestire, modificare, testare e riutilizzare, stabilire se effettuare il refactoring di queste aree in modo che siano definite più chiaramente o se è possibile unire codice che esegue funzioni simili.|
|Nessuna dipendenza|Sono necessarie o se è necessario rimuovere questo codice.|

## <a name="analyze-code-maps"></a>Analizzare mappe del codice

1. Sulla barra degli strumenti della mappa scegliere **Layout**, **Analizzatori**e quindi l'analizzatore da eseguire:

   |**Analizzatore**|**Per identificare i nodi che**|
   |------------------|--------------------------------|
   |**Analizzatore Riferimenti circolari**|Hanno dipendenze circolari tra loro. **Nota:**  Le dipendenze circolari presenti nel gruppo **generics** non vengono visualizzate sulla mappa quando si espande il gruppo.|
   |**Analizzatore Trova hub**|Rientrano nel primo 25% dei nodi con connessione elevata<br /><br /> **Per nascondere tutti gli altri nodi nella mappa**<br /><br /> -Aprire il menu di scelta rapida per la mappa, scegliere **Avanzate**, **selezionare**, **Nascondi non selezionato**.<br />     La mappa consente di nascondere i nodi non selezionati e l'analizzatore identifica nuovi nodi come hub.|
   |**Analizzatore Nodi senza riferimenti**|Non contengono riferimenti da altri nodi. **Attenzione:**  Verificare ognuno di questi casi prima di presupporre che il codice non venga usato. Non è possibile trovare alcune dipendenze, ad esempio le dipendenze XAML e di runtime, in modo statico nel codice.|

   Gli analizzatori di mappe codice continueranno l'esecuzione una volta applicati. Se si modifica la mappa, eventuali analizzatori applicati automaticamente rielaboreranno la mappa aggiornata. Per interrompere l'esecuzione di un analizzatore, sulla barra degli strumenti mappa scegliere **Layout**, **Analizzatori**. Disattivare l'analizzatore selezionato.

> [!TIP]
> Se si ha una mappa di dimensioni molto grandi, l'esecuzione di un analizzatore potrebbe provocare un'eccezione per memoria insufficiente. In questo caso, modificare la mappa per ridurne l'ambito o generarne una di dimensioni più piccole e quindi eseguire l'analizzatore.

## <a name="see-also"></a>Vedere anche
 Eseguire il mapping delle [dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md) [usare le mappe codice per eseguire il debug](../modeling/use-code-maps-to-debug-your-applications.md) [dei metodi di mapping delle applicazioni nello stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
