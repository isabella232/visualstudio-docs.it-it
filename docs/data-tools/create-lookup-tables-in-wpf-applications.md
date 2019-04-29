---
title: Creare tabelle di ricerca in applicazioni WPF
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [WPF], displaying
- WPF, data binding in Visual Studio
- WPF data binding [Visual Studio]
- displaying data, WPF
- WPF [WPF], data
- WPF Designer, data binding
- data binding, WPF
ms.assetid: 56a1fbff-c7e8-4187-a1c1-ffd17024bc1b
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1631f1b93f79c21914f990620f7e0047c301163f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62567819"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Creare tabelle di ricerca in applicazioni WPF

Il termine *tabella di ricerca* (talvolta chiamato un *binding di ricerca*) descrive un controllo che visualizza le informazioni da una tabella dati in base al valore di un campo di chiave esterna in un'altra tabella. È possibile creare una tabella di ricerca trascinando il nodo principale di una tabella padre o dell'oggetto nel **Zdroje dat** finestra in un controllo che è già associato a una colonna o proprietà in una tabella figlio correlata.

Ad esempio, si consideri una tabella di `Orders` in un database di vendite. Ogni record di `Orders` tabella include un `CustomerID` che indica il cliente che ha effettuato l'ordine. Il `CustomerID` è una chiave esterna che punta a un record del cliente nel `Customers` tabella. Quando si visualizza un elenco di ordini dal `Orders` tabella, è possibile visualizzare il nome del cliente effettivo anziché il `CustomerID`. Perché è il nome del cliente nel `Customers` tabella, è necessario creare una tabella di ricerca per visualizzare il nome del cliente. La tabella di ricerca utilizza il `CustomerID` valore di `Orders` registrare per spostarsi all'interno della relazione e restituire il nome del cliente.

## <a name="to-create-a-lookup-table"></a>Per creare una tabella di ricerca

1. Aggiungere uno dei seguenti tipi di origini dati con dati correlati al progetto:

    - Set di dati o Entity Data Model.

    - WCF Data Service, servizio WCF o un servizio web. Per altre informazioni, vedere [Procedura: Connettersi ai dati di un servizio](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Oggetti. Per altre informazioni, vedere [associazione agli oggetti in Visual Studio](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Prima di creare una tabella di ricerca, due tabelle o oggetti correlati devono esistere come un'origine dati per il progetto.

2. Aprire il **WPF Designer**e assicurarsi che la finestra di progettazione contiene un contenitore che è una destinazione di rilascio validi per gli elementi nel **Zdroje dat** finestra.

     Per altre informazioni sulle destinazioni di rilascio validi, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

3. Scegliere **Mostra origini dati** dal menu **Dati** per aprire la finestra **Origini dati**.

4. Espandere i nodi le **Zdroje dat** finestra fino a quando non è possibile visualizzare la tabella padre o l'oggetto e la tabella figlio correlata o l'oggetto.

    > [!NOTE]
    > La tabella figlio correlata o l'oggetto è il nodo che viene visualizzato come nodo figlio espandibile sotto la tabella padre o l'oggetto.

5. Fare clic sul menu a discesa per il nodo figlio e selezionare **dettagli**.

6. Espandere il nodo figlio.

7. Sotto il nodo figlio, fare clic sul menu a discesa scegliere per l'elemento che correla i dati padre e figlio. (Nell'esempio precedente, questo è il **CustomerID** nodo.) Selezionare uno dei seguenti tipi di controlli che supportano il binding di ricerca:

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > Se il **ListBox** oppure **ListView** controllo non viene visualizzato nell'elenco, è possibile aggiungere questi controlli per l'elenco. Per informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Qualsiasi controllo personalizzato che deriva da <xref:System.Windows.Controls.Primitives.Selector>.

        > [!NOTE]
        > Per informazioni su come aggiungere controlli personalizzati per l'elenco dei controlli è possono selezionare per gli elementi di **Zdroje dat** finestra, vedere [aggiungere controlli personalizzati alla finestra Origini dei dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Trascinare il nodo figlio dal **Zdroje dat** finestra in un contenitore in WPF designer. (Nell'esempio precedente, il nodo figlio è il **ordini** nodo.)

     Visual Studio genera XAML che crea nuovi controlli associati a dati per ognuno degli elementi che si trascinano. il XAML aggiunge anche un nuovo <xref:System.Windows.Data.CollectionViewSource> per la tabella figlio o un oggetto alle risorse di destinazione di rilascio. Per alcune origini dati, Visual Studio genera inoltre il codice per caricare i dati nella tabella o dell'oggetto. Per altre informazioni, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Trascinare il nodo padre di **Zdroje dat** finestra al controllo di ricerca di associazione creato in precedenza. (Nell'esempio precedente, il nodo padre è il **clienti** nodo).

     Visual Studio configura alcune proprietà sul controllo per configurare il binding di ricerca. Nella tabella seguente sono elencate le proprietà modificate da Visual Studio. Se necessario, è possibile modificare queste proprietà nel XAML o nel **proprietà** finestra.

    |Proprietà|Spiegazione dell'impostazione|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Questa proprietà specifica la raccolta o associazione usato per ottenere i dati che viene visualizzati nel controllo. Visual Studio imposta questa proprietà il <xref:System.Windows.Data.CollectionViewSource> per i dati padre è stato trascinato al controllo.|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Questa proprietà specifica il percorso dell'elemento di dati che viene visualizzato nel controllo. Visual Studio imposta questa proprietà per la prima colonna o proprietà nei dati di padre, dopo la chiave primaria, con un tipo di dati stringa.<br /><br /> Se si desidera visualizzare una colonna diversa o proprietà nei dati dell'elemento padre, è possibile modificare questa proprietà per il percorso di una proprietà diversa.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio, questa proprietà viene associato alla colonna o alla proprietà dei dati che è stato trascinato nella finestra di progettazione figlio. Si tratta della chiave esterna per i dati padre.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio imposta questa proprietà per il percorso della colonna o una proprietà dei dati che rappresenta la chiave esterna di dati padre / figlio.|

## <a name="see-also"></a>Vedere anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Visualizzare dati correlati in applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)
- [Procedura dettagliata: Visualizzazione di dati correlati in un'applicazione WPF](../data-tools/display-related-data-in-wpf-applications.md)