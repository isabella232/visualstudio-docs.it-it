---
title: Set di DataSet tipizzati e non tipizzati | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 39a16a200bbc057288ae2741e7d504566b0368e1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72667149"
---
# <a name="typed-vs-untyped-datasets"></a>Set di dati tipizzati e non tipizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un set di dati tipizzato è un set di dati che viene innanzitutto derivato dalla classe di base <xref:System.Data.DataSet> e quindi utilizza le informazioni del **Progettazione DataSet**, memorizzato in un file XSD, per generare una nuova classe DataSet fortemente tipizzata. Le informazioni dello schema (tabelle, colonne e così via) vengono generate e compilate in questa nuova classe DataSet come set di oggetti e proprietà di prima classe. Poiché un DataSet tipizzato eredita dalla <xref:System.Data.DataSet> classe di base, la classe tipizzata presuppone tutte le funzionalità della <xref:System.Data.DataSet> classe e può essere utilizzata con i metodi che accettano un'istanza di una <xref:System.Data.DataSet> classe come parametro.

 Un set di dati non tipizzato, al contrario, non ha uno schema incorporato corrispondente. Come in un DataSet tipizzato, un set di dati non tipizzato contiene tabelle, colonne e così via, ma vengono esposte solo come raccolte. Tuttavia, dopo aver creato manualmente le tabelle e gli altri elementi di dati in un set di dati non tipizzato, è possibile esportare la struttura del set di dati come uno schema usando il metodo del set di dati <xref:System.Data.DataSet.WriteXmlSchema%2A> .

## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Contrasto dell'accesso ai dati nei set di dati tipizzati e non tipizzati
 La classe per un set di dati tipizzato dispone di un modello a oggetti in cui le relative proprietà accettano i nomi effettivi delle tabelle e delle colonne. Se, ad esempio, si utilizza un set di dati tipizzato, è possibile fare riferimento a una colonna utilizzando codice come il seguente:

 [!code-csharp[VbRaddataDatasets#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#4)]
 [!code-vb[VbRaddataDatasets#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#4)]

 Al contrario, se si utilizza un set di dati non tipizzato, il codice equivalente è:

 [!code-csharp[VbRaddataDatasets#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#5)]
 [!code-vb[VbRaddataDatasets#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#5)]

 L'accesso tipizzato non è più semplice da leggere, ma anche completamente supportato da IntelliSense nell' [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **editor di codice**. Oltre a essere più facile da utilizzare, la sintassi per il set di dati tipizzato fornisce il controllo del tipo in fase di compilazione, riducendo notevolmente la possibilità di errori nell'assegnazione di valori ai membri del set di dati. Se si modifica il nome di una colonna nella <xref:System.Data.DataSet> classe e quindi si compila l'applicazione, viene visualizzato un errore di compilazione. Facendo doppio clic sull'errore di compilazione nella **elenco attività**, è possibile passare direttamente alla riga o alle righe di codice che fanno riferimento al nome della colonna precedente. L'accesso a tabelle e colonne in un set di dati tipizzato è anche leggermente più rapido in fase di esecuzione perché l'accesso viene determinato in fase di compilazione, non tramite raccolte in fase di esecuzione.

 Anche se i set di dati tipizzati presentano molti vantaggi, un set di dati non tipizzato risulta utile in diverse circostanze. Lo scenario più ovvio è quando non è disponibile alcuno schema per il set di dati. Questa situazione può verificarsi, ad esempio, se l'applicazione sta interagendo con un componente che restituisce un set di dati, ma non si sa in anticipo quale sia la struttura. In modo analogo, in alcuni casi si utilizzano dati che non dispongono di una struttura prevedibile statica. In tal caso, non è pratico usare un DataSet tipizzato, perché sarebbe necessario rigenerare la classe DataSet tipizzata con ogni modifica nella struttura dei dati.

 Più in generale, è possibile creare un set di dati in modo dinamico senza che sia disponibile uno schema. In tal caso, il set di dati è semplicemente una struttura comoda in cui è possibile tenere le informazioni, purché i dati possano essere rappresentati in modo relazionale. Allo stesso tempo, è possibile sfruttare le funzionalità del set di dati, ad esempio la possibilità di serializzare le informazioni da passare a un altro processo o scrivere un file XML.
