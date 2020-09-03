---
title: Operatori di ricerca avanzati nelle espressioni di ricerca | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5088fc04f4440260bdb9d3f040d99061c05d243
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72620341"
---
# <a name="advanced-search-operators-in-search-expressions"></a>Operatori di ricerca avanzati nelle espressioni di ricerca
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Usando gli operatori di ricerca avanzati, è possibile affinare la ricerca di contenuto creando espressioni di ricerca più complesse da quelle più semplici. Come illustrato nella tabella seguente, questi operatori limitano il contesto in cui viene eseguita una query.

> [!WARNING]
> È necessario immettere gli operatori di ricerca avanzati seguiti da due punti senza spazio affinché il motore di ricerca li possa riconoscere.

|Per cercare|Uso|Esempio|Risultato|
|-------------------|---------|-------------|------------|
|Un termine nel titolo dell'argomento|title:|title:binaryreader|Argomenti che contengono "binaryreader" nei titoli.|
|Un termine in un esempio di codice|code:|code:readdouble|Argomenti che contengono "readdouble" in un esempio di codice.|
|Un termine in un 'esempio di un linguaggio di programmazione specifico|code:vb:|code:vb:string|Argomenti che contengono "string" in un esempio di Visual Basic.|
|Un argomento associato a una parola chiave di indice specifica|keyword:|keyword:readbyte|Argomenti associati alla parola chiave di indice "readbyte".|

 È possibile usare l'operatore code: per trovare contenuti relativi a diversi linguaggi di programmazione. Restituisce tuttavia solo i risultati relativi al contenuto contrassegnato con un linguaggio di programmazione specifico. La tabella seguente elenca i linguaggi di programmazione supportati da questo operatore:

|Linguaggio di programmazione|Uso|
|--------------------------|---------|
|Visual Basic|code:vb<br /><br /> Oppure<br /><br /> code:visualbasic|
|C#|code:c#<br /><br /> Oppure<br /><br /> code:csharp|
|C++|code:cpp<br /><br /> Oppure<br /><br /> code:c++<br /><br /> Oppure<br /><br /> code:cplusplus|
|F#|code:f#<br /><br /> Oppure<br /><br /> code:fsharp|
|JavaScript|code:javascript<br /><br /> Oppure<br /><br /> code:js|
|XAML|: xaml|

## <a name="see-also"></a>Vedere anche
 [Operatori logici nelle espressioni di ricerca](../ide/logical-operators-in-search-expressions.md) [Suggerimenti per la ricerca full-text](../ide/full-text-search-tips.md)
