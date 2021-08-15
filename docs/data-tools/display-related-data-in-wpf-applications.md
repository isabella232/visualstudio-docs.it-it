---
title: Visualizzare dati correlati in applicazioni WPF
description: Visualizzare i dati correlati nelle applicazioni WPF. Usare i dati di più tabelle o entità correlate tra loro in una relazione padre-figlio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 3aa80194-0191-474d-9d28-5ec05654b426
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 2aedad0255ed6d6f281b9030f4cc15ed36e4db296bba1912f5ac203811c0a2bd
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121347318"
---
# <a name="display-related-data-in-wpf-applications"></a>Visualizzare dati correlati in applicazioni WPF

In alcune applicazioni può essere necessario usare dati provenienti da più tabelle o entità correlate tra loro in una relazione padre-figlio. Ad esempio, potrebbe essere necessario visualizzare una griglia che visualizza i clienti di una `Customers` tabella. Quando l'utente seleziona un cliente specifico, un'altra griglia visualizza gli ordini per tale cliente da una tabella `Orders` correlata.

È possibile creare controlli associati a dati che visualizzano dati correlati trascinando gli elementi dalla **finestra** Origini dati a Wpf Designer.

## <a name="to-create-controls-that-display-related-records"></a>Per creare controlli che visualizzano record correlati

1. Scegliere **Mostra origini dati** dal menu **Dati** per aprire la finestra **Origini dati**.

2. Fare clic su **Aggiungi nuova origine dati** e completare la **Configurazione guidata origine dati**.

3. Aprire Progettazione WPF e assicurarsi che la finestra di progettazione contenga un contenitore che rappresenta una destinazione di rilascio valida per gli elementi nella **finestra Origini** dati.

     Per altre informazioni sulle destinazioni di rilascio valide, vedere [Associare i controlli WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)ai dati in Visual Studio .

4. Nella finestra **Origini dati** espandere il nodo che rappresenta la tabella o l'oggetto padre nella relazione. La tabella o l'oggetto padre si trova sul lato "uno" di una relazione uno-a-molti.

5. Trascinare il nodo padre (o i singoli  elementi nel nodo padre) dalla finestra Origini dati in una destinazione di rilascio valida nella finestra di progettazione.

     Visual Studio genera XAML che crea nuovi controlli associati a dati per ogni elemento trascinato. Il codice XAML aggiunge anche un nuovo oggetto o tabella <xref:System.Windows.Data.CollectionViewSource> padre alle risorse della destinazione di rilascio. Per alcune origini dati, Visual Studio anche il codice per caricare i dati nella tabella o nell'oggetto padre. Per altre informazioni, vedere [Associare i controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

6. Nella finestra **Origini dati** individuare la tabella o l'oggetto figlio correlato. Le tabelle e gli oggetti figlio correlati vengono visualizzati come nodi espandibili nella parte inferiore dell'elenco di dati del nodo padre.

7. Trascinare il nodo figlio (o i singoli  elementi nel nodo figlio) dalla finestra Origini dati in una destinazione di rilascio valida nella finestra di progettazione.

     Visual Studio genera XAML che crea nuovi controlli associati a dati per ognuno degli elementi trascinati. Il codice XAML aggiunge anche un nuovo <xref:System.Windows.Data.CollectionViewSource> oggetto o tabella figlio alle risorse della destinazione di rilascio. Questo nuovo oggetto è associato alla proprietà della tabella o dell'oggetto <xref:System.Windows.Data.CollectionViewSource> padre appena trascinato nella finestra di progettazione. Per alcune origini dati, Visual Studio anche il codice per caricare i dati nella tabella o nell'oggetto figlio.

     Nella figura seguente viene illustrata **la tabella Orders** correlata della tabella **Customers** in un set di dati nella **finestra Origini** dati .

     ![Finestra Origini dati con visualizzazione delle relazioni](../data-tools/media/datasources2.gif)

## <a name="see-also"></a>Vedi anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Creare tabelle di ricerca in applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md)
