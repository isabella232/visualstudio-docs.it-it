---
redirect_url: /visualstudio/ide/logical-operators-in-search-expressions
ms.openlocfilehash: fe896af873197c95a4b226396e0b6333fdc40cfa
ms.sourcegitcommit: ec1c7e7e3349d2f3a4dc027e7cfca840c029367d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/07/2017
---
title: "Operatori di ricerca avanzati nelle espressioni di ricerca | Microsoft Docs" ms.custom: "" ms.date: "06/02/2017" ms.reviewer: "" ms.suite: "" ms.technology: 
  - "vs-help-viewer" ms.tgt_pltfrm: "" ms.topic: "article" helpviewer_keywords: 
  - "Help Viewer, ricerca di parole chiave"
  - "Help Viewer, ricerca di codice"
  - "Help Viewer, ricerca di codice in base al linguaggio di programmazione"
  - "Help Viewer, ricerca di titoli"
  - "ricerca di codice [Help Viewer]"
  - "ricerca di titoli [Help Viewer]" ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e caps.latest.revision: 9 author: "gewarren" ms.author: "gewarren" manager: ghogen
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operatori di ricerca avanzati nelle espressioni di ricerca
Usando gli operatori di ricerca avanzati in Help Viewer, è possibile affinare la ricerca di contenuto specificando l'area dell'argomento in cui cercare il termine. La tabella seguente descrive i quattro operatori di ricerca avanzata disponibili.

|Per cercare|Usare|Esempio|Risultato|  
|-------------------|---------|-------------|------------|  
|Un termine nel titolo dell'argomento|title:|title:binaryreader|Argomenti che contengono "binaryreader" nei titoli.|  
|Un termine in un esempio di codice|code:|code:readdouble|Argomenti che contengono "readdouble" in un esempio di codice.|  
|Un termine in un 'esempio di un linguaggio di programmazione specifico|code:vb:|code:vb:string|Argomenti che contengono "string" in un esempio di codice di Visual Basic.|  
|Un argomento associato a una parola chiave di indice specifica|keyword:|keyword:readbyte|Argomenti associati alla parola chiave di indice "readbyte".|  

> [!WARNING]
>  È necessario immettere gli operatori di ricerca avanzati seguiti da due punti senza spazio affinché il motore di ricerca li possa riconoscere.    

## <a name="programming-languages-for-code-examples"></a>Linguaggi di programmazione per esempi di codice
È possibile usare l'operatore code: per trovare contenuti relativi a diversi linguaggi di programmazione. Vengono tuttavia restituiti solo i risultati relativi al contenuto contrassegnato con un linguaggio di programmazione specifico. Per restituire gli esempi per un linguaggio di programmazione specifico, usare uno dei valori di linguaggio di programmazione seguenti:  

|Linguaggio di programmazione|Sintassi dell'operatore di ricerca|  
|--------------------|---------|  
|Visual Basic|code:vb<br/>code:visualbasic|  
|C#|code:c#<br/>code:csharp|  
|C++|code:cpp<br/>code:c++<br/>code:cplusplus|  
|F#|code:f#<br/>code:fsharp|  
|JavaScript|code:javascript<br/>code:js|  
|XAML|: xaml|
