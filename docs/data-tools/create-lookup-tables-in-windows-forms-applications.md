---
title: Creare tabelle di ricerca nelle applicazioni Windows Forms
description: Informazioni su come creare tabelle di ricerca in Windows applicazioni Form. Una tabella di ricerca descrive i controlli associati a due tabelle di dati correlate.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8d8eda7fadbf0c0e94da85442ef852c0e735d80a1b6ffdecab192ace2387d85d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121264662"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Creare tabelle di ricerca nelle applicazioni Windows Forms

La tabella *di ricerca* dei termini descrive i controlli associati a due tabelle di dati correlate. Questi controlli di ricerca visualizzano i dati della prima tabella in base a un valore selezionato nella seconda tabella.

È possibile creare tabelle di ricerca trascinando il nodo principale di una tabella padre (dalla finestra Origini dati [)](add-new-data-sources.md#data-sources-window)in un controllo del form già associato alla colonna nella tabella figlio correlata.

Si consideri, ad esempio, una tabella `Orders` di in un database di vendita. Ogni record nella tabella `Orders` include un oggetto , che indica il cliente che ha effettuato `CustomerID` l'ordine. è `CustomerID` una chiave esterna che punta a un record cliente nella `Customers` tabella. In questo scenario si espande la tabella nella finestra Origini dati e si `Orders` imposta il nodo principale su **Dettagli**.  Impostare quindi la colonna in modo da usare (o qualsiasi altro controllo che supporta l'associazione di ricerca) e trascinare `CustomerID` <xref:System.Windows.Forms.ComboBox> il nodo nel `Orders` form. Trascinare infine `Customers` il nodo nel controllo associato alla colonna correlata, in questo caso l'oggetto associato alla <xref:System.Windows.Forms.ComboBox> `CustomerID` colonna.

## <a name="to-databind-a-lookup-control"></a>Per eseguire l'associazione dati di un controllo di ricerca

1. Con il progetto aperto, aprire la **finestra Origini** dati **scegliendo** Visualizza altre origini  >  **Windows**  >  **dati**.

    > [!NOTE]
    > Per le tabelle di ricerca è necessario che nella finestra Origini dati siano disponibili **due tabelle o oggetti** correlati. Per altre informazioni, vedere [Relazioni nei set di dati.](relationships-in-datasets.md)

2. Espandere i nodi nella **finestra Origini** dati fino a visualizzare la tabella padre e tutte le relative colonne, la tabella figlio correlata e tutte le relative colonne.

    > [!NOTE]
    > Il nodo della tabella figlio è il nodo visualizzato come nodo figlio espandibile nella tabella padre.

3. Modificare il tipo di rilascio della tabella figlio in **Dettagli** selezionando **Dettagli** nell'elenco di controlli nel nodo della tabella figlio. Per altre informazioni, vedere [Impostare il controllo da creare quando si trascina dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Individuare il nodo che mette in relazione le due tabelle `CustomerID` (il nodo nell'esempio precedente). Modificare il tipo di rilascio in <xref:System.Windows.Forms.ComboBox> un oggetto selezionando **ComboBox** nell'elenco dei controlli.

5. Trascinare il nodo della tabella figlio principale dalla **finestra Origini** dati nel form.

     I controlli associati a dati (con etichette descrittive) e una barra degli strumenti ( <xref:System.Windows.Forms.BindingNavigator> ) vengono visualizzati nel form. Nella barra dei componenti vengono visualizzati un [oggetto DataSet](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md) <xref:System.Windows.Forms.BindingSource> , e <xref:System.Windows.Forms.BindingNavigator> .

6. Trascinare ora il nodo principale della tabella padre dalla **finestra Origini** dati direttamente nel controllo di ricerca ( <xref:System.Windows.Forms.ComboBox> ).

     Le associazioni di ricerca sono ora stabilite. Fare riferimento alla tabella seguente per le proprietà specifiche impostate nel controllo .

    |Proprietà|Spiegazione dell'impostazione|
    |--------------| - |
    |**DataSource**|Questa proprietà viene impostata da Visual Studio sul <xref:System.Windows.Forms.BindingSource> creato per la tabella trascinata nel controllo (a differenza del <xref:System.Windows.Forms.BindingSource> creato al momento della creazione del controllo).<br /><br /> Se è necessario apportare una regolazione, impostata sul valore della tabella <xref:System.Windows.Forms.BindingSource> con la colonna che si vuole visualizzare.|
    |**DisplayMember**|Questa proprietà viene impostata da Visual Studio sulla prima colonna successiva alla chiave primaria con tipo di dati stringa per la tabella che si intende trascinare nel controllo.<br /><br /> Se è necessario apportare una rettifica, impostata sul nome della colonna che si vuole visualizzare.|
    |**ValueMember**|Questa proprietà viene impostata da Visual Studio sulla prima colonna che partecipa alla chiave primaria o la prima colonna della tabella nel caso in cui non sia stata definita alcuna chiave.<br /><br /> Se è necessario apportare una rettifica, impostata sulla chiave primaria nella tabella con la colonna che si vuole visualizzare.|
    |**Selectedvalue**|Visual Studio imposta questa proprietà sulla colonna originale rilasciata dalla **finestra Origini** dati.<br /><br /> Se è necessario apportare una rettifica, impostata sulla colonna chiave esterna nella tabella correlata.|

## <a name="see-also"></a>Vedi anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
