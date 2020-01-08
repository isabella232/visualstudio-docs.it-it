---
title: Creare tabelle di ricerca nelle applicazioni Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9fe49ee90dba3edd0e2777817c4903c6101a1b47
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/01/2020
ms.locfileid: "75586770"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Creare tabelle di ricerca nelle applicazioni Windows Forms

La *tabella di ricerca* dei termini descrive i controlli associati a due tabelle di dati correlate. Questi controlli di ricerca visualizzano i dati della prima tabella in base a un valore selezionato nella seconda tabella.

È possibile creare tabelle di ricerca trascinando il nodo principale di una tabella padre (dalla [finestra Origini dati](add-new-data-sources.md#data-sources-window)) su un controllo nel form che è già associato alla colonna nella tabella figlio correlata.

Si consideri, ad esempio, una tabella di `Orders` in un database Sales. Ogni record della tabella `Orders` include una `CustomerID`, che indica il cliente che ha effettuato l'ordine. Il `CustomerID` è una chiave esterna che fa riferimento a un record del cliente nella tabella `Customers`. In questo scenario si espande la tabella `Orders` nella finestra **origini dati** e si imposta il nodo principale su **Details**. Impostare quindi la colonna `CustomerID` per usare una <xref:System.Windows.Forms.ComboBox> (o qualsiasi altro controllo che supporta l'associazione di ricerca) e trascinare il nodo `Orders` nel form. Infine, trascinare il nodo `Customers` sul controllo associato alla colonna correlata, in questo caso la <xref:System.Windows.Forms.ComboBox> associata alla colonna `CustomerID`.

## <a name="to-databind-a-lookup-control"></a>Per associare un controllo di ricerca

1. Con il progetto aperto, aprire la finestra **origini dati** scegliendo **Visualizza** > **altre** **origini dati** > di Windows.

    > [!NOTE]
    > Per le tabelle di ricerca è necessario che nella finestra **origini dati** siano disponibili due tabelle o oggetti correlati. Per altre informazioni, vedere [relazioni nei DataSet](relationships-in-datasets.md).

2. Espandere i nodi nella finestra **origini dati** fino a visualizzare la tabella padre e tutte le relative colonne, nonché la tabella figlio correlata e tutte le relative colonne.

    > [!NOTE]
    > Il nodo della tabella figlio è il nodo visualizzato come nodo figlio espandibile nella tabella padre.

3. Modificare il tipo di rilascio della tabella figlio in **Dettagli** selezionando **Dettagli** dall'elenco di controllo nel nodo della tabella figlio. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Individuare il nodo che mette in correlazione le due tabelle (il nodo `CustomerID` nell'esempio precedente). Modificare il tipo di rilascio in una <xref:System.Windows.Forms.ComboBox> selezionando **ComboBox** dall'elenco di controllo.

5. Trascinare il nodo della tabella figlio principale dalla finestra **origini dati** nel form.

     Nel form vengono visualizzati i controlli associati a un oggetto con etichette descrittive e una striscia di strumenti (<xref:System.Windows.Forms.BindingNavigator>). Un [set di dati](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

6. Trascinare il nodo della tabella padre principale dalla finestra **origini dati** direttamente nel controllo Lookup (il <xref:System.Windows.Forms.ComboBox>).

     Sono ora stabilite le associazioni di ricerca. Fare riferimento alla tabella seguente per le proprietà specifiche impostate per il controllo.

    |Gli|Spiegazione dell'impostazione|
    |--------------| - |
    |**DataSource**|Questa proprietà viene impostata da Visual Studio sul <xref:System.Windows.Forms.BindingSource> creato per la tabella trascinata nel controllo (a differenza del <xref:System.Windows.Forms.BindingSource> creato al momento della creazione del controllo).<br /><br /> Se è necessario apportare una modifica, impostare questa impostazione sulla <xref:System.Windows.Forms.BindingSource> della tabella con la colonna che si desidera visualizzare.|
    |**DisplayMember**|Questa proprietà viene impostata da Visual Studio sulla prima colonna successiva alla chiave primaria con tipo di dati stringa per la tabella che si intende trascinare nel controllo.<br /><br /> Se è necessario apportare una modifica, impostare il nome della colonna che si desidera visualizzare.|
    |**ValueMember**|Questa proprietà viene impostata da Visual Studio sulla prima colonna che partecipa alla chiave primaria o la prima colonna della tabella nel caso in cui non sia stata definita alcuna chiave.<br /><br /> Se è necessario apportare una modifica, impostarla sulla chiave primaria nella tabella con la colonna che si desidera visualizzare.|
    |**SelectedValue**|Visual Studio imposta questa proprietà sulla colonna originale eliminata dalla finestra **origini dati** .<br /><br /> Se è necessario apportare una modifica, impostarla sulla colonna chiave esterna nella tabella correlata.|

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
