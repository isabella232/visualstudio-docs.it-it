---
title: Set di dati tipizzati e non tipizzati
description: Comprendere la differenza tra set di dati tipizzati e non tipizzati. Contrasta l'accesso ai dati nei set di dati tipizzati e non tipizzati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3ce12fd272297429ba62c4e947025ada7c350d26
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122036836"
---
# <a name="typed-vs-untyped-datasets"></a>Set di dati tipizzati e non tipizzati
Un set di dati tipizzato è un set di dati derivato prima dalla classe di base e quindi usa le informazioni di Progettazione DataSet , archiviate in un file xsd, per generare una nuova classe dataset fortemente <xref:System.Data.DataSet> tipizzato.  Le informazioni dello schema (tabelle, colonne e così via) vengono generate e compilate in questa nuova classe di set di dati come set di proprietà e oggetti di prima classe. Poiché un set di dati tipizzato eredita dalla classe di base, la classe tipizzato presuppone tutte le funzionalità della classe e può essere usata con metodi che accettano un'istanza di una classe <xref:System.Data.DataSet> <xref:System.Data.DataSet> come <xref:System.Data.DataSet> parametro.

Un set di dati non tipizzato, al contrario, non ha uno schema predefinito corrispondente. Come in un set di dati tipizzato, un set di dati non tipizzato contiene tabelle, colonne e così via, ma questi vengono esposti solo come raccolte. Tuttavia, dopo aver creato manualmente le tabelle e altri elementi dati in un set di dati non tipizzato, è possibile esportare la struttura del set di dati come schema usando il metodo del set di <xref:System.Data.DataSet.WriteXmlSchema%2A> dati.

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Contrasto dell'accesso ai dati nei set di dati tipizzati e non tipizzati
La classe per un set di dati tipizzato ha un modello a oggetti in cui le relative proprietà accettano i nomi effettivi delle tabelle e delle colonne. Ad esempio, se si usa un set di dati tipizzato, è possibile fare riferimento a una colonna usando codice simile al seguente:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet4":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet4":::

Al contrario, se si lavora con un set di dati non tipizzato, il codice equivalente è:

:::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs" id="Snippet5":::
:::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb" id="Snippet5":::

L'accesso tipizzato non solo è più facile da leggere, ma è anche completamente supportato da IntelliSense nell'editor Visual Studio **codice.** Oltre a essere più semplice da usare, la sintassi per il set di dati tipizzato fornisce il controllo dei tipi in fase di compilazione, riducendo notevolmente la possibilità di errori nell'assegnazione di valori ai membri del set di dati. Se si modifica il nome di una colonna nella classe e quindi si compila <xref:System.Data.DataSet> l'applicazione, viene visualizzato un errore di compilazione. Facendo doppio clic sull'errore di compilazione nel **Elenco attività**, è possibile passare direttamente alla riga o alle righe di codice che fanno riferimento al nome della colonna precedente. Anche l'accesso a tabelle e colonne in un set di dati tipizzato è leggermente più veloce in fase di esecuzione perché l'accesso viene determinato in fase di compilazione, non tramite raccolte in fase di esecuzione.

Anche se i set di dati tipizzati presentano molti vantaggi, un set di dati non tipizzato è utile in diverse circostanze. Lo scenario più ovvio è quando non è disponibile alcuno schema per il set di dati. Ciò può verificarsi, ad esempio, se l'applicazione interagisce con un componente che restituisce un set di dati, ma non si conosce in anticipo la struttura. Analogamente, in alcuni casi si lavora con dati che non hanno una struttura statica e prevedibile. In tal caso, non è pratico usare un set di dati tipizzato, perché sarebbe necessario rigenerare la classe del set di dati tipizzato con ogni modifica nella struttura dei dati.

Più in generale, spesso è possibile creare un set di dati in modo dinamico senza avere uno schema disponibile. In tal caso, il set di dati è semplicemente una struttura pratica in cui è possibile conservare le informazioni, purché i dati possano essere rappresentati in modo relazionale. Allo stesso tempo, è possibile sfruttare le funzionalità del set di dati, ad esempio la possibilità di serializzare le informazioni da passare a un altro processo o di scrivere un file XML.

## <a name="see-also"></a>Vedi anche

- [Strumenti del set di dati](../data-tools/dataset-tools-in-visual-studio.md)
