---
title: Operatori logici nelle espressioni di ricerca (Help Viewer)
description: Informazioni su come usare gli operatori logici e gli operatori di ricerca avanzati per perfezionare le espressioni di ricerca Microsoft Help Viewer.
ms.custom: SEO-VS-2020
ms.date: 11/02/2017
ms.topic: reference
helpviewer_keywords:
- Help Viewer, logical operators in search
- logical operators in search [Help Viewer]
ms.assetid: 0c38ae7d-3e20-4d47-a020-9677cd285916
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-help-viewer
ms.workload:
- multiple
ms.openlocfilehash: 5302c5a59595b98c601f98b1fbe6ca1168106f52aceb12081a4cf37875cf258e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358402"
---
# <a name="logical-and-advanced-operators-in-search-expressions"></a>Operatori logici e avanzati nelle espressioni di ricerca

È possibile usare gli operatori logici e gli operatori di ricerca avanzati per perfezionare la ricerca del contenuto della Guida in **Help Viewer**.

## <a name="logical-operators"></a>Operatori logici

Gli operatori logici specificano in che modo più termini di ricerca debbano essere combinati in una query di ricerca. La tabella seguente illustra gli operatori logici AND, OR, NOT e NEAR.

|Per cercare|Uso|Esempio|Risultato|
|-------------------|---------|-------------|------------|
|Entrambi i termini nello stesso articolo|AND|DIB AND tavolozza|Argomenti che contengono sia "DIB" che "tavolozza".|
|Uno dei termini in un articolo|OR|raster OR vettore|Argomenti che contengono "raster" o "vettore".|
|Primo termine senza il secondo nello stesso articolo|NOT|"sistema operativo" NOT DOS|Argomenti che contengono "sistema operativo" ma non "DOS".|
|Entrambi i termini, vicini in un articolo|VICINO|utente NEAR kernel|Gli argomenti che contengono "utente" in prossimità di "kernel".|

> [!IMPORTANT]
> Per essere riconosciuti dal motore di ricerca, gli operatori logici devono essere immessi interamente in lettere maiuscole.

## <a name="advanced-operators"></a>Operatori avanzati

Gli operatori di ricerca avanzati consentono di affinare la ricerca di contenuto specificando l'area di un articolo in cui cercare il termine. La tabella seguente descrive i quattro operatori di ricerca avanzata disponibili.

|Per cercare|Uso|Esempio|Risultato|
|-------------------|---------|-------------|------------|
|Un termine nel titolo dell'articolo|`title:`|`title:binaryreader`|Argomenti che contengono "binaryreader" nei titoli.|
|Un termine in un esempio di codice|`code:`|`code:readdouble`|Argomenti che contengono "readdouble" in un esempio di codice.|
|Un termine in un 'esempio di un linguaggio di programmazione specifico|`code:vb:`|`code:vb:string`|Argomenti che contengono "string" in un esempio di codice di Visual Basic.|
|Un articolo associato a una parola chiave di indice specifica|`keyword:`|`keyword:readbyte`|Argomenti associati alla parola chiave di indice "readbyte".|

> [!IMPORTANT]
> È necessario immettere gli operatori di ricerca avanzati seguiti da due punti senza spazio affinché il motore di ricerca li possa riconoscere.

### <a name="programming-languages-for-code-examples"></a>Linguaggi di programmazione per esempi di codice

È possibile usare l'operatore `code:` per trovare contenuti relativi a uno dei diversi linguaggi di programmazione. Per restituire gli esempi per un linguaggio di programmazione specifico, usare uno dei valori di linguaggio di programmazione seguenti:

|Linguaggio di programmazione|Sintassi dell'operatore di ricerca|
| - |---------|
|Visual Basic|`code:vb`<br/>`code:visualbasic`|
|C#|`code:c#`<br/>`code:csharp`|
|C++|`code:cpp`<br/>`code:c++`<br/>`code:cplusplus`|
|F#|`code:f#`<br/>`code:fsharp`|
|JavaScript|`code:javascript`<br/>`code:js`|
|XAML|`code:xaml`|

> [!NOTE]
> L'operatore `code:` trova solo il contenuto contrassegnato con un'etichetta di linguaggio di programmazione, anziché il contenuto contrassegnato in modo generico come codice.

## <a name="see-also"></a>Vedi anche

- [Procedura: Eseguire la ricerca di argomenti](../help-viewer/find-topics.md)
- [Microsoft Help Viewer](../help-viewer/overview.md)
