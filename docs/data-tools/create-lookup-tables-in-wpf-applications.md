---
title: Creare tabelle di ricerca in applicazioni WPF
description: Creare tabelle di ricerca nelle app WPF. Una tabella di ricerca è un controllo che mostra le informazioni di una tabella dati in base a un valore di campo di chiave esterna in un'altra tabella.
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 52c14b4fd8369db5df57579ea20b3ff9e17c898f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631464"
---
# <a name="create-lookup-tables-in-wpf-applications"></a>Creare tabelle di ricerca in applicazioni WPF

Il termine *tabella di ricerca* (talvolta denominata associazione di ricerca ) descrive un controllo che visualizza informazioni da una tabella dati in base al valore di un campo di chiave esterna in un'altra tabella.  È possibile creare una tabella di ricerca trascinando il nodo  principale di una tabella o di un oggetto padre nella finestra Origini dati in un controllo già associato a una colonna o a una proprietà in una tabella figlio correlata.

Si consideri ad esempio una tabella di `Orders` in un database sales. Ogni record nella tabella `Orders` include un oggetto che indica quale cliente ha effettuato `CustomerID` l'ordine. è `CustomerID` una chiave esterna che punta a un record cliente nella `Customers` tabella. Quando si visualizza un elenco di ordini dalla tabella, può essere necessario visualizzare il nome effettivo `Orders` del cliente anziché `CustomerID` . Poiché il nome del cliente si trova nella tabella, è necessario `Customers` creare una tabella di ricerca per visualizzare il nome del cliente. La tabella di ricerca usa `CustomerID` il valore nel record per esplorare la relazione e restituire il nome del `Orders` cliente.

## <a name="to-create-a-lookup-table"></a>Per creare una tabella di ricerca

1. Aggiungere al progetto uno dei tipi seguenti di origini dati con dati correlati:

    - Set di dati o Entity Data Model.

    - Servizio dati WCF, servizio WCF o servizio Web. Per altre informazioni, vedere [Procedura: Connessione ai dati in un servizio](../data-tools/how-to-connect-to-data-in-a-service.md).

    - Oggetti. Per altre informazioni, vedere [Eseguire l'associazione a oggetti in Visual Studio](bind-objects-in-visual-studio.md).

    > [!NOTE]
    > Prima di poter creare una tabella di ricerca, è necessario che due tabelle o oggetti correlati esistano come origine dati per il progetto.

2. Aprire WPF **Designer** e assicurarsi che la finestra di progettazione contenga un contenitore che rappresenta una destinazione di rilascio valida per gli elementi nella **finestra Origini** dati .

     Per altre informazioni sulle destinazioni di rilascio valide, vedere [Associare i controlli WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)ai dati in Visual Studio .

3. Scegliere **Mostra origini dati** dal menu **Dati** per aprire la finestra **Origini dati**.

4. Espandere i nodi nella **finestra Origini** dati fino a visualizzare la tabella o l'oggetto padre e la tabella o l'oggetto figlio correlato.

    > [!NOTE]
    > La tabella o l'oggetto figlio correlato è il nodo visualizzato come nodo figlio espandibile sotto la tabella o l'oggetto padre.

5. Fare clic sul menu a discesa per il nodo figlio e selezionare **Dettagli**.

6. Espandere il nodo figlio.

7. Nel nodo figlio fare clic sul menu a discesa per l'elemento che mette in relazione i dati figlio e padre. Nell'esempio precedente si tratta del **nodo CustomerID.** Selezionare uno dei tipi di controlli seguenti che supportano l'associazione di ricerca:

    - **ComboBox**

    - **ListBox**

    - **ListView**

        > [!NOTE]
        > Se il **controllo ListBox** o **ListView** non viene visualizzato nell'elenco, è possibile aggiungere questi controlli all'elenco. Per informazioni, vedere [Impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

    - Qualsiasi controllo personalizzato che deriva da <xref:System.Windows.Controls.Primitives.Selector> .

        > [!NOTE]
        > Per informazioni su come aggiungere controlli personalizzati all'elenco di  controlli che è possibile selezionare per gli elementi nella finestra Origini dati, vedere Aggiungere controlli personalizzati alla finestra [Origini dati](../data-tools/add-custom-controls-to-the-data-sources-window.md).

8. Trascinare il nodo figlio dalla **finestra Origini** dati in un contenitore nella finestra di progettazione WPF. Nell'esempio precedente il nodo figlio è **il nodo Orders.**

     Visual Studio genera XAML che crea nuovi controlli associati a dati per ognuno degli elementi trascinati. Il codice XAML aggiunge anche un nuovo <xref:System.Windows.Data.CollectionViewSource> oggetto o tabella figlio alle risorse della destinazione di rilascio. Per alcune origini dati, Visual Studio anche il codice per caricare i dati nella tabella o nell'oggetto. Per altre informazioni, vedere [Associare i controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

9. Trascinare il nodo padre dalla **finestra Origini** dati nel controllo di associazione di ricerca creato in precedenza. Nell'esempio precedente il nodo padre è **il nodo** Customers.

     Visual Studio alcune proprietà nel controllo per configurare l'associazione di ricerca. Nella tabella seguente sono elencate le proprietà Visual Studio modifica. Se necessario, è possibile modificare queste proprietà nel codice XAML o nella **finestra** Proprietà.

    |Proprietà|Spiegazione dell'impostazione|
    |--------------| - |
    |<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>|Questa proprietà specifica la raccolta o l'associazione utilizzata per ottenere i dati visualizzati nel controllo . Visual Studio imposta questa proprietà su <xref:System.Windows.Data.CollectionViewSource> per i dati padre trascinati nel controllo .|
    |<xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A>|Questa proprietà specifica il percorso dell'elemento di dati visualizzato nel controllo . Visual Studio imposta questa proprietà sulla prima colonna o proprietà nei dati padre, dopo la chiave primaria, con un tipo di dati stringa.<br /><br /> Se si vuole visualizzare una colonna o una proprietà diversa nei dati padre, modificare questa proprietà nel percorso di una proprietà diversa.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValue%2A>|Visual Studio associa questa proprietà alla colonna o alla proprietà dei dati figlio trascinati nella finestra di progettazione. Si tratta della chiave esterna per i dati padre.|
    |<xref:System.Windows.Controls.Primitives.Selector.SelectedValuePath%2A>|Visual Studio imposta questa proprietà sul percorso della colonna o della proprietà dei dati figlio che rappresenta la chiave esterna per i dati padre.|

## <a name="see-also"></a>Vedi anche

- [Associare controlli WPF ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
- [Visualizzare dati correlati in applicazioni WPF](../data-tools/display-related-data-in-wpf-applications.md)
- [Procedura dettagliata: Visualizzazione di dati correlati in un'applicazione WPF](../data-tools/display-related-data-in-wpf-applications.md)
