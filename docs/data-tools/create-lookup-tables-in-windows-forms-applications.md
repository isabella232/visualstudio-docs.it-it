---
title: Creare tabelle di ricerca nelle applicazioni Windows Forms
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 782f5b422058d1564bde04251a92d95145f6edf3
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60045127"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Creare tabelle di ricerca nelle applicazioni Windows Forms

Il termine *tabella di ricerca* descrive i controlli associati a due tabelle dati correlate. Questi controlli di ricerca visualizzano i dati della prima tabella basata su un valore selezionato nella seconda tabella.

È possibile creare tabelle di ricerca tramite trascinamento del nodo principale di una tabella padre (dal [finestra Origini dati](add-new-data-sources.md#data-sources-window)) su un controllo nel form che è già associato alla colonna della tabella figlio correlata.

Ad esempio, si consideri una tabella di `Orders` in un database di vendite. Ogni record di `Orders` tabella include un `CustomerID`, che indica il cliente che ha effettuato l'ordine. Il `CustomerID` è una chiave esterna che punta a un record del cliente nel `Customers` tabella. In questo scenario, si espande il `Orders` nella tabella le **Zdroje dat** finestra e impostare il nodo principale **dettagli**. Quindi, impostare il `CustomerID` colonna da utilizzare un <xref:System.Windows.Forms.ComboBox> (o qualsiasi altro controllo che supporta il binding di ricerca) e trascinare il `Orders` nodo nel form. Infine, trascinare il `Customers` nodo nel controllo associato alla colonna correlata, in questo caso, il <xref:System.Windows.Forms.ComboBox> associato ai `CustomerID` colonna.

## <a name="to-databind-a-lookup-control"></a>Come associare un controllo di ricerca

1. Aprire il progetto, aprire il **Zdroje dat** finestra scegliendo **View** > **Other Windows** > **Zdroje dat**.

    > [!NOTE]
    > Le tabelle di ricerca richiedono che siano disponibili in due tabelle correlate o gli oggetti di **Zdroje dat** finestra. Per altre informazioni, vedere [relazioni nei DataSet](relationships-in-datasets.md).

2. Espandere i nodi le **Zdroje dat** finestra fino a quando non è possibile visualizzare la tabella padre e tutte le relative colonne e la tabella figlio correlata e tutte le relative colonne.

    > [!NOTE]
    > Il nodo della tabella figlio è il nodo che viene visualizzato come nodo figlio espandibile nella tabella padre.

3. Modificare il tipo di rilascio della tabella figlio alla **informazioni dettagliate** selezionando **dettagli** dall'elenco di controllo sul nodo della tabella figlio. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Individuare il nodo che correla le due tabelle (il `CustomerID` nodo nell'esempio precedente). Modificare il tipo di rilascio a un <xref:System.Windows.Forms.ComboBox> selezionando **ComboBox** dall'elenco di controllo.

5. Trascinare il nodo della tabella figlio principale dal **Zdroje dat** finestra nei form.

     I controlli con associazione a dati (con etichette descrittive) e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) vengono visualizzati nel form. Oggetto [set di dati](../data-tools/dataset-tools-in-visual-studio.md), [TableAdapter](../data-tools/create-and-configure-tableadapters.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

6. A questo punto, trascinare il nodo della tabella padre principale dal **Zdroje dat** finestra direttamente al controllo di ricerca (il <xref:System.Windows.Forms.ComboBox>).

     A questo punto vengono stabilite le associazioni di ricerca. Vedere la tabella seguente per le proprietà specifiche di quelle impostate nella finestra di controllo.

    |Proprietà|Spiegazione dell'impostazione|
    |--------------| - |
    |**DataSource**|Questa proprietà viene impostata da Visual Studio sul <xref:System.Windows.Forms.BindingSource> creato per la tabella trascinata nel controllo (a differenza del <xref:System.Windows.Forms.BindingSource> creato al momento della creazione del controllo).<br /><br /> Se è necessario apportare modifiche, impostare questa opzione il <xref:System.Windows.Forms.BindingSource> della tabella contenente la colonna che si desidera visualizzare.|
    |**DisplayMember**|Questa proprietà viene impostata da Visual Studio sulla prima colonna successiva alla chiave primaria con tipo di dati stringa per la tabella che si intende trascinare nel controllo.<br /><br /> Se è necessario apportare modifiche, impostare il nome della colonna da visualizzare.|
    |**ValueMember**|Questa proprietà viene impostata da Visual Studio sulla prima colonna che partecipa alla chiave primaria o la prima colonna della tabella nel caso in cui non sia stata definita alcuna chiave.<br /><br /> Se è necessario apportare modifiche, impostare la chiave primaria della tabella con la colonna che si desidera visualizzare.|
    |**SelectedValue**|Visual Studio imposta questa proprietà per la colonna originale trascinata dal **Zdroje dat** finestra.<br /><br /> Se è necessario apportare modifiche, impostare la colonna chiave esterna nella tabella correlata.|

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)