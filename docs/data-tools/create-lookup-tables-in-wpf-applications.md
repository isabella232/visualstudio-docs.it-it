---
title: Creare tabelle di ricerca in applicazioni WPF
description: Creare tabelle di ricerca nelle applicazioni WPF. Una tabella di ricerca è un controllo che mostra le informazioni di una tabella dati in base a un valore del campo di chiave esterna in un'altra tabella.
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
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 293f04ca111fe88c905a288885f7e4763ec1cdc3
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/10/2020
ms.locfileid: "94436693"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Creare tabelle di ricerca in applicazioni WPF

La *tabella di ricerca* termini (talvolta denominata *associazione di ricerca* ) descrive un controllo che visualizza informazioni da una tabella dati in base al valore di un campo di chiave esterna in un'altra tabella. È possibile creare una tabella di ricerca trascinando il nodo principale di una tabella o di un oggetto padre nella finestra **origini dati** su un controllo già associato a una colonna o a una proprietà in una tabella figlio correlata.

Si consideri, ad esempio, una tabella di `Orders` in un database Sales. Ogni record della `Orders` tabella include un valore `CustomerID` che indica il cliente che ha effettuato l'ordine. `CustomerID`È una chiave esterna che punta a un record del cliente nella `Customers` tabella. Quando si visualizza un elenco di ordini dalla `Orders` tabella, è possibile che si desideri visualizzare il nome effettivo del cliente anziché il `CustomerID` . Poiché il nome del cliente si trova nella `Customers` tabella, è necessario creare una tabella di ricerca per visualizzare il nome del cliente. Nella tabella di ricerca viene utilizzato il `CustomerID` valore del `Orders` record per spostarsi nella relazione e viene restituito il nome del cliente.

## <a name="to-create-a-lookup-table"></a>Per creare una tabella di ricerca

1. Aggiungere al progetto uno dei seguenti tipi di origini dati con dati correlati:

    - Set di dati o Entity Data Model.

    - WCF Data Services, servizio WCF o servizio Web. Per altre informazioni, vedere [procedura: connettersi ai dati in un servizio](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Oggetti. Per altre informazioni, vedere [Bind to Objects in Visual Studio](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Prima di poter creare una tabella di ricerca, due tabelle o oggetti correlati devono esistere come origine dati per il progetto.

2. Aprire **WPF Designer** e assicurarsi che la finestra di progettazione contenga un contenitore che rappresenta un obiettivo di rilascio valido per gli elementi nella finestra **origini dati** .

     Per altre informazioni sugli obiettivi di rilascio validi, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3. Scegliere **Mostra origini dati** dal menu **Dati** per aprire la finestra **Origini dati**.

4. Espandere i nodi nella finestra **origini dati** finché non sarà possibile visualizzare la tabella o l'oggetto padre e la tabella o l'oggetto figlio correlato.

    > [!NOTE]
    > La tabella o l'oggetto figlio correlato è il nodo visualizzato come nodo figlio espandibile nella tabella o nell'oggetto padre.

5. Fare clic sul menu a discesa del nodo figlio e selezionare **Dettagli**.

6. Espandere il nodo figlio.

7. Nel nodo figlio fare clic sul menu a discesa per l'elemento che mette in correlazione i dati figlio e padre. Nell'esempio precedente si tratta del nodo **CustomerID** . Selezionare uno dei seguenti tipi di controlli che supportano l'associazione di ricerca:

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > Se il controllo **ListBox** o **ListView** non è presente nell'elenco, è possibile aggiungere questi controlli all'elenco. Per informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Qualsiasi controllo personalizzato che deriva da <xref:System.Windows.Controls.Primitives.Selector> .

        > [!NOTE]
        > Per informazioni sull'aggiunta di controlli personalizzati all'elenco di controlli che è possibile selezionare per gli elementi nella finestra **origini dati** , vedere [aggiungere controlli personalizzati alla finestra Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Trascinare il nodo figlio dalla finestra **origini dati** in un contenitore in WPF Designer. Nell'esempio precedente, il nodo figlio è il nodo **Orders** .

     Visual Studio genera il codice XAML che crea nuovi controlli associati a dati per ogni elemento trascinato. Il codice XAML aggiunge anche un nuovo <xref:System.Windows.Data.CollectionViewSource> oggetto per la tabella o l'oggetto figlio alle risorse dell'obiettivo di rilascio. Per alcune origini dati, Visual Studio genera anche codice per caricare i dati nella tabella o nell'oggetto. Per altre informazioni, vedere [associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Trascinare il nodo padre dalla finestra **origini dati** nel controllo binding di ricerca creato in precedenza. Nell'esempio precedente, il nodo padre è il nodo **Customers** .

     Visual Studio imposta alcune proprietà nel controllo per configurare l'associazione di ricerca. La tabella seguente elenca le proprietà modificate da Visual Studio. Se necessario, è possibile modificare queste proprietà in XAML o nella finestra **Proprietà** .

    |Proprietà|Spiegazione dell'impostazione|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Questa proprietà specifica la raccolta o l'associazione utilizzata per ottenere i dati visualizzati nel controllo. Visual Studio imposta questa proprietà su <xref:System.Windows.Data.CollectionViewSource> per i dati padre trascinati nel controllo.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Questa proprietà specifica il percorso dell'elemento di dati visualizzato nel controllo. Visual Studio imposta questa proprietà sulla prima colonna o proprietà nei dati padre, dopo la chiave primaria, che ha un tipo di dati String.<br /><br /> Se si desidera visualizzare una colonna o una proprietà diversa nei dati padre, impostare questa proprietà sul percorso di un'altra proprietà.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|In Visual Studio questa proprietà viene associata alla colonna o alla proprietà dei dati figlio trascinati nella finestra di progettazione. Si tratta della chiave esterna per i dati padre.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio imposta questa proprietà sul percorso della colonna o della proprietà dei dati figlio che rappresenta la chiave esterna per i dati padre.|

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Visualizzare dati correlati in applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)
- [Procedura dettagliata: visualizzazione dei dati correlati in un'applicazione WPF](../data-tools/display-related-data-in-wpf-applications.md)
