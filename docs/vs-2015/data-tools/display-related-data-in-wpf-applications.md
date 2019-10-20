---
title: Visualizzare dati correlati nelle applicazioni WPF | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6efa79fc59ed9812cf6162096dd462100b71fbca
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72672419"
---
# <a name="display-related-data-in-wpf-applications"></a>Visualizzare dati correlati in applicazioni WPF
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In alcune applicazioni, potrebbe essere necessario utilizzare dati provenienti da più tabelle o entità correlate l'una all'altra in una relazione padre-figlio. Ad esempio, potrebbe essere necessario visualizzare una griglia in cui vengono visualizzati i clienti di una tabella `Customers`. Quando l'utente seleziona un cliente specifico, in un'altra griglia vengono visualizzati gli ordini per il cliente da una tabella `Orders` correlata.

 È possibile creare controlli associati a dati che visualizzano dati correlati trascinando gli elementi dalla finestra **origini dati** a WPF Designer.

## <a name="to-create-controls-that-display-related-records"></a>Per creare controlli che visualizzano record correlati

1. Scegliere **Mostra origini dati** dal menu **Dati** per aprire la finestra **Origini dati**.

2. Fare clic su **Aggiungi nuova origine dati** e completare la **Configurazione guidata origine dati**.

3. Aprire WPF Designer e assicurarsi che la finestra di progettazione contenga un contenitore che rappresenta un obiettivo di rilascio valido per gli elementi nella finestra **origini dati** .

     Per altre informazioni sugli obiettivi di rilascio validi, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

4. Nella finestra **origini dati** espandere il nodo che rappresenta la tabella o l'oggetto padre nella relazione. La tabella o l'oggetto padre si trova sul lato "uno" di una relazione uno-a-molti.

5. Trascinare il nodo padre (o tutti gli elementi singoli del nodo padre) dalla finestra **origini dati** in un obiettivo di rilascio valido nella finestra di progettazione.

     Visual Studio genera il codice XAML che crea nuovi controlli associati a dati per ogni elemento trascinato. Il codice XAML aggiunge anche un nuovo <xref:System.Windows.Data.CollectionViewSource> per la tabella o l'oggetto padre alle risorse dell'obiettivo di rilascio. Per alcune origini dati, Visual Studio genera anche codice per caricare i dati nella tabella o nell'oggetto padre. Per altre informazioni, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

6. Nella finestra **origini dati** individuare la tabella o l'oggetto figlio correlato. Le tabelle e gli oggetti figlio correlati vengono visualizzati come nodi espandibili nella parte inferiore dell'elenco di dati del nodo padre.

7. Trascinare il nodo figlio (o tutti gli elementi singoli del nodo figlio) dalla finestra **origini dati** in un obiettivo di rilascio valido nella finestra di progettazione.

     Visual Studio genera XAML per creare nuovi controlli associati a dati per ognuno degli elementi trascinati. Il codice XAML aggiunge anche un nuovo <xref:System.Windows.Data.CollectionViewSource> per la tabella o l'oggetto figlio alle risorse dell'obiettivo di rilascio. Questo nuovo <xref:System.Windows.Data.CollectionViewSource> viene associato alla proprietà della tabella o dell'oggetto padre che è stato appena trascinato nella finestra di progettazione. Per alcune origini dati, Visual Studio genera anche codice per caricare i dati nella tabella o nell'oggetto figlio.

     Nella figura seguente viene illustrata la tabella **Orders** correlata della tabella **Customers** in un set di dati nella finestra **origini dati** .

     ![Finestra Origini dati che mostra la relazione](../data-tools/media/datasources2.gif "DataSources2")

## <a name="see-also"></a>Vedere anche
 [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md) [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md) [creare tabelle di ricerca nelle applicazioni WPF](../data-tools/create-lookup-tables-in-wpf-applications.md) [procedura dettagliata: visualizzazione di dati correlati in un'applicazione WPF](../data-tools/walkthrough-displaying-related-data-in-a-wpf-application.md)
