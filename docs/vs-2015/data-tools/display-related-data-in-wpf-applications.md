---
title: Visualizzare i dati correlati nelle applicazioni WPF | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c4068bcbf3ead7114013b93f02a784d682e5b4d5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530187"
---
# <a name="display-related-data-in-wpf-applications"></a>Visualizzare i dati correlati nelle applicazioni WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [visualizzare i dati correlati nelle applicazioni WPF](https://docs.microsoft.com/visualstudio/data-tools/display-related-data-in-wpf-applications).  
  
  
In alcune applicazioni, si potrebbe voler usare dati provenienti da più tabelle o entità sono correlate tra loro in una relazione padre-figlio. Potrebbe ad esempio, si desidera visualizzare una griglia in cui vengono visualizzati i clienti da un `Customers` tabella. Quando l'utente seleziona un cliente specifico, in un'altra griglia vengono visualizzati gli ordini per quel cliente da un processo di `Orders` tabella.  
  
 È possibile creare controlli associati a dati che visualizzano dati correlati trascinando elementi dal **Zdroje dat** finestra di progettazione WPF.  
  
## <a name="to-create-controls-that-display-related-records"></a>Per creare controlli che consentono di visualizzare i record correlati  
  
1.  Nel **dati** menu, fare clic su **Mostra origini dati** per aprire il **Zdroje dat** finestra.  
  
2.  Fare clic su **Aggiungi nuova origine dati**e completare la **configurazione dell'origine dati** procedura guidata.  
  
3.  Aprire la finestra di progettazione WPF e assicurarsi che la finestra di progettazione contiene un contenitore che è un obiettivo di rilascio validi per gli elementi di **Zdroje dat** finestra.  
  
     Per altre informazioni sulle destinazioni di rilascio validi, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
4.  Nel **Zdroje dat** finestra, espandere il nodo che rappresenta la tabella padre o dell'oggetto nella relazione. La tabella padre o l'oggetto è il lato "uno" di una relazione uno-a-molti.  
  
5.  Trascinare il nodo padre (o qualsiasi singoli elementi nel nodo padre) dal **Zdroje dat** finestra su un obiettivo di rilascio valido nella finestra di progettazione.  
  
     Visual Studio genera XAML che crea nuovi controlli associati a dati per ogni elemento trascinato. il XAML aggiunge anche un nuovo <xref:System.Windows.Data.CollectionViewSource> per oggetti per le risorse di destinazione di rilascio o la tabella padre. Per alcune origini dati, Visual Studio genera inoltre il codice per caricare i dati in un oggetto o la tabella padre. Per altre informazioni, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).  
  
6.  Nel **Zdroje dat** finestra, individuare la tabella figlio correlata o l'oggetto. Le tabelle figlio correlate e gli oggetti vengono visualizzati come nodi espandibili nella parte inferiore dell'elenco del nodo padre dei dati.  
  
7.  Trascinare il nodo figlio (o qualsiasi singoli elementi del nodo figlio) dal **Zdroje dat** finestra su un obiettivo di rilascio valido nella finestra di progettazione.  
  
     Visual Studio genera XAML che crea nuovi controlli associati a dati per ognuno degli elementi trascinati. il XAML aggiunge anche un nuovo <xref:System.Windows.Data.CollectionViewSource> per la tabella figlio o un oggetto alle risorse di destinazione di rilascio. Questa nuova <xref:System.Windows.Data.CollectionViewSource> è associato alla proprietà dell'oggetto che è stato appena trascinato nella finestra di progettazione o tabella padre. Per alcune origini dati, Visual Studio genera inoltre il codice per caricare i dati nella tabella figlio o nell'oggetto.  
  
     La figura seguente illustra i relativi **ordini** tabella del **clienti** tabella in un set di dati nel **Zdroje dat** finestra.  
  
     ![Finestra Origini dati che mostra relazione](../data-tools/media/datasources2.gif "DataSources2")  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)   
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md)   
 [Creare tabelle di ricerca nelle applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)   
 [Procedura dettagliata: visualizzazione dei dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)

