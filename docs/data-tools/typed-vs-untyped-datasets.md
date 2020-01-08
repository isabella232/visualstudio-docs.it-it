---
title: Set di dati tipizzati e non tipizzati
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 430e57713f1bfb01219ea1ac8123f321ba0f5680
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586107"
---
# <a name="typed-vs-untyped-datasets"></a>Set di dati tipizzati e non tipizzati
Un set di dati tipizzato è un set di dati che viene innanzitutto derivato dalla classe di <xref:System.Data.DataSet> di base e quindi utilizza le informazioni della **Progettazione DataSet**, archiviate in un file XSD, per generare una nuova classe DataSet fortemente tipizzata. Le informazioni dello schema (tabelle, colonne e così via) vengono generate e compilate in questa nuova classe DataSet come set di oggetti e proprietà di prima classe. Poiché un DataSet tipizzato eredita dalla classe di <xref:System.Data.DataSet> di base, la classe tipizzata presuppone tutte le funzionalità della classe <xref:System.Data.DataSet> e può essere utilizzata con i metodi che accettano un'istanza di una classe <xref:System.Data.DataSet> come parametro.

Un set di dati non tipizzato, al contrario, non ha uno schema incorporato corrispondente. Come in un DataSet tipizzato, un set di dati non tipizzato contiene tabelle, colonne e così via, ma vengono esposte solo come raccolte. Tuttavia, dopo aver creato manualmente le tabelle e altri elementi di dati in un set di dati non tipizzato, è possibile esportare la struttura del set di dati come uno schema usando il metodo di <xref:System.Data.DataSet.WriteXmlSchema%2A> del set di dati.

## <a name="contrast-data-access-in-typed-and-untyped-datasets"></a>Contrasto dell'accesso ai dati nei set di dati tipizzati e non tipizzati
La classe per un set di dati tipizzato dispone di un modello a oggetti in cui le relative proprietà accettano i nomi effettivi delle tabelle e delle colonne. Se, ad esempio, si utilizza un set di dati tipizzato, è possibile fare riferimento a una colonna utilizzando codice come il seguente:

[!code-csharp[VbRaddataDatasets#4](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_1.cs)]
[!code-vb[VbRaddataDatasets#4](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_1.vb)]

Al contrario, se si utilizza un set di dati non tipizzato, il codice equivalente è:

[!code-csharp[VbRaddataDatasets#5](../data-tools/codesnippet/CSharp/typed-vs-untyped-datasets_2.cs)]
[!code-vb[VbRaddataDatasets#5](../data-tools/codesnippet/VisualBasic/typed-vs-untyped-datasets_2.vb)]

L'accesso tipizzato non è più semplice da leggere, ma anche completamente supportato da IntelliSense nell' **editor di codice**di Visual Studio. Oltre a essere più facile da utilizzare, la sintassi per il set di dati tipizzato fornisce il controllo del tipo in fase di compilazione, riducendo notevolmente la possibilità di errori nell'assegnazione di valori ai membri del set di dati. Se si modifica il nome di una colonna nella classe <xref:System.Data.DataSet> e quindi si compila l'applicazione, viene visualizzato un errore di compilazione. Facendo doppio clic sull'errore di compilazione nella **elenco attività**, è possibile passare direttamente alla riga o alle righe di codice che fanno riferimento al nome della colonna precedente. L'accesso a tabelle e colonne in un DataSet tipizzato è anche leggermente più rapido in fase di esecuzione, perché l'accesso viene determinato in fase di compilazione, non tramite raccolte in fase di esecuzione.

Anche se i set di dati tipizzati presentano molti vantaggi, un set di dati non tipizzato risulta utile in diverse circostanze. Lo scenario più ovvio è quando non è disponibile alcuno schema per il set di dati. Questa situazione può verificarsi, ad esempio, se l'applicazione sta interagendo con un componente che restituisce un set di dati, ma non si sa in anticipo quale sia la struttura. In modo analogo, in alcuni casi si utilizzano dati che non dispongono di una struttura prevedibile statica. In tal caso, non è pratico usare un DataSet tipizzato, perché sarebbe necessario rigenerare la classe DataSet tipizzata con ogni modifica nella struttura dei dati.

Più in generale, è possibile creare un set di dati in modo dinamico senza che sia disponibile uno schema. In tal caso, il set di dati è semplicemente una struttura comoda in cui è possibile tenere le informazioni, purché i dati possano essere rappresentati in modo relazionale. Allo stesso tempo, è possibile sfruttare le funzionalità del set di dati, ad esempio la possibilità di serializzare le informazioni da passare a un altro processo o scrivere un file XML.

## <a name="see-also"></a>Vedere anche

- [Strumenti di set di dati](../data-tools/dataset-tools-in-visual-studio.md)
