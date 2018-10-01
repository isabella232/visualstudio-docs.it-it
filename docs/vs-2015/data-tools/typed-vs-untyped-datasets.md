---
title: Tipizzati e DataSet non tipizzati | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c83ba0bb-5425-4d47-8891-6b4dbf937701
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 287a0ceae792a91e676982f5ec47d3905966956b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526944"
---
# <a name="typed-vs-untyped-datasets"></a>Set di dati tipizzati e non tipizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [tipizzati e DataSet non tipizzati](https://docs.microsoft.com/visualstudio/data-tools/typed-vs-untyped-datasets).  
  
  
Un dataset tipizzato è un set di dati derivato dalla base inizialmente <xref:System.Data.DataSet> classe e quindi Usa le informazioni dal **Progettazione Dataset**, che viene archiviato in un file XSD, per generare un nuovo, fortemente tipizzate classe dataset. Informazioni dallo schema (tabelle, colonne e così via) vengano generate e compilate in questa nuova classe di set di dati come set di proprietà e oggetti di prima classe. Poiché un dataset tipizzato erediterà dalla base <xref:System.Data.DataSet> (classe), la classe tipizzata si presuppone che tutte le funzionalità del <xref:System.Data.DataSet> classe e può essere usato con metodi che accettano un'istanza di un <xref:System.Data.DataSet> classe come parametro.  
  
 Un set di dati non tipizzati, invece, non presenta alcun schema predefinito corrispondente. Come in un dataset tipizzato, un dataset non tipizzato contiene tabelle, colonne e così via, ma questi sono esposti solo come raccolte. (Tuttavia, dopo aver creato manualmente le tabelle e altri elementi di dati in un dataset non tipizzato, è possibile esportare la struttura del set di dati come uno schema tramite il set di dati <xref:System.Data.DataSet.WriteXmlSchema%2A> (metodo).)  
  
## <a name="contrasting-data-access-in-typed-and-untyped-datasets"></a>Accesso ai dati nei set di dati tipizzati e non tipizzati  
 La classe di un dataset tipizzato presenta un modello a oggetti in cui le relative proprietà hanno i nomi effettivi delle tabelle e colonne. Ad esempio, se si lavora con un dataset tipizzato, è possibile fare riferimento a una colonna usando codice simile al seguente:  
  
 [!code-csharp[VbRaddataDatasets#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#4)]
 [!code-vb[VbRaddataDatasets#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#4)]  
  
 Al contrario, se si lavora con un set di dati non tipizzati, il codice equivalente è:  
  
 [!code-csharp[VbRaddataDatasets#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataDatasets/CS/Form1.cs#5)]
 [!code-vb[VbRaddataDatasets#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataDatasets/VB/Form1.vb#5)]  
  
 Accesso tipizzato non solo è più facile da leggere, ma anche completamente supportata da IntelliSense nel [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] **Editor di codice**. Oltre a essere più facile lavorare con, la sintassi per il set di dati tipizzato consente un controllo in fase di compilazione, riducendo la possibilità di errori nell'assegnazione di valori ai membri del set di dati. Se si modifica il nome di una colonna di <xref:System.Data.DataSet> classe e quindi compilare l'applicazione, verrà visualizzato un errore di compilazione. Facendo doppio clic su errore di compilazione nel **elenco attività**, è possibile passare direttamente alla riga o le righe di codice che fanno riferimento al nome di colonna precedenti. Accesso a tabelle e colonne in un oggetto set di dati è inoltre leggermente più veloce in fase di esecuzione perché l'accesso è determinato in fase di compilazione, non tramite le raccolte in fase di esecuzione.  
  
 Anche se i dataset tipizzati offrono molti vantaggi, un dataset non tipizzato è utile in diverse circostanze. Lo scenario più ovvio è quando è disponibile per il set di dati alcuno schema. Ciò può verificarsi, ad esempio, se l'applicazione interagisca con un componente che restituisce un set di dati, ma non si conosce in anticipo qual è la relativa struttura. Analogamente, vi sono casi quando si lavora con i dati che non dispone di una struttura statica e prevedibile. In tal caso, è poco pratico da utilizzare un dataset tipizzato, perché sarebbe necessario rigenerare la classe dataset tipizzato con ogni modifica nella struttura dei dati.  
  
 Più in generale, esistono molte volte quando è possibile creare un set di dati in modo dinamico senza che sia disponibile uno schema. In tal caso, il set di dati è semplicemente una pratica struttura in cui è possibile mantenere informazioni, purché i dati possono essere rappresentati in modo relazionale. Allo stesso tempo, è possibile sfruttare le funzionalità del set di dati, ad esempio la possibilità di serializzare le informazioni per passare a un altro processo o per scrivere un file XML.

