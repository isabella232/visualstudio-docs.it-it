---
title: Creare tabelle di ricerca nelle applicazioni Windows Forms | Microsoft Docs
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
- lookup tables
- lookup tables, creating
ms.assetid: 0edd5385-c381-4b17-9096-74e2778db9d5
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3979d08757445e9df5fc159fe7642b04bf74b995
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72630928"
---
# <a name="create-lookup-tables-in-windows-forms-applications"></a>Creare tabelle di ricerca nelle applicazioni Windows Forms
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La *tabella di ricerca* dei termini descrive i controlli associati a due tabelle di dati correlate. Questi controlli di ricerca visualizzano i dati della prima tabella in base a un valore selezionato nella seconda tabella.

 È possibile creare tabelle di ricerca trascinando il nodo principale di una tabella padre (dalla [finestra Origini dati](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)) su un controllo nel form che è già associato alla colonna nella tabella figlio correlata.

 Si consideri, ad esempio, una tabella di `Orders` in un database Sales. Ogni record della `Orders` tabella include un oggetto `CustomerID` , che indica il cliente che ha effettuato l'ordine. `CustomerID`È una chiave esterna che punta a un record del cliente nella `Customers` tabella. In questo scenario la tabella viene espansa `Orders` nella finestra **origini dati** e il nodo principale viene impostato su **Details**. Impostare quindi la `CustomerID` colonna per usare un <xref:System.Windows.Forms.ComboBox> (o qualsiasi altro controllo che supporta l'associazione di ricerca) e trascinare il `Orders` nodo nel form. Infine, trascinare il `Customers` nodo sul controllo associato alla colonna correlata, in questo caso l'oggetto <xref:System.Windows.Forms.ComboBox> associato alla `CustomerID` colonna.

## <a name="to-databind-a-lookup-control"></a>Per associare un controllo di ricerca

1. Aprire la finestra **Origini dati**.

    > [!NOTE]
    > Per le tabelle di ricerca è necessario che nella finestra **origini dati** siano disponibili due tabelle o oggetti correlati.

2. Espandere i nodi nella finestra **origini dati** fino a visualizzare la tabella padre e tutte le relative colonne, nonché la tabella figlio correlata e tutte le relative colonne.

    > [!NOTE]
    > Il nodo della tabella figlio è il nodo visualizzato come nodo figlio espandibile nella tabella padre.

3. Modificare il tipo di rilascio della tabella figlio in **Dettagli** selezionando **Dettagli** dall'elenco di controllo nel nodo della tabella figlio. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

4. Individuare il nodo che mette in correlazione le due tabelle (il `CustomerID` nodo nell'esempio precedente). Modificare il tipo di rilascio in un <xref:System.Windows.Forms.ComboBox> selezionando **ComboBox** dall'elenco dei controlli.

5. Trascinare il nodo della tabella figlio principale dalla finestra **origini dati** nel form.

     Nel form vengono visualizzati i controlli associati a un oggetto con etichette descrittive e una striscia di strumenti ( <xref:System.Windows.Forms.BindingNavigator> ). Un [set di dati](../data-tools/dataset-tools-in-visual-studio.md), TableAdapter, <xref:System.Windows.Forms.BindingSource> e viene <xref:System.Windows.Forms.BindingNavigator> visualizzato nella barra dei componenti.

6. Trascinare ora il nodo principale della tabella padre dalla finestra **origini dati** direttamente nel controllo Lookup ( <xref:System.Windows.Forms.ComboBox> ).

     Sono ora stabilite le associazioni di ricerca. Fare riferimento alla tabella seguente per le proprietà specifiche impostate per il controllo.

    |Proprietà|Spiegazione dell'impostazione|
    |--------------|----------------------------|
    |**DataSource**|Questa proprietà viene impostata da Visual Studio sul <xref:System.Windows.Forms.BindingSource> creato per la tabella trascinata nel controllo (a differenza del <xref:System.Windows.Forms.BindingSource> creato al momento della creazione del controllo).<br /><br /> Se è necessario apportare una modifica, impostare questa impostazione sulla <xref:System.Windows.Forms.BindingSource> della tabella con la colonna che si desidera visualizzare.|
    |**DisplayMember**|Questa proprietà viene impostata da Visual Studio sulla prima colonna successiva alla chiave primaria con tipo di dati stringa per la tabella che si intende trascinare nel controllo.<br /><br /> Se è necessario apportare una modifica, impostare il nome della colonna che si desidera visualizzare.|
    |**ValueMember**|Questa proprietà viene impostata da Visual Studio sulla prima colonna che partecipa alla chiave primaria o la prima colonna della tabella nel caso in cui non sia stata definita alcuna chiave.<br /><br /> Se è necessario apportare una modifica, impostare questa impostazione sulla chiave primaria nella tabella con la colonna che si desidera visualizzare.|
    |**SelectedValue**|Visual Studio imposta questa proprietà sulla colonna originale eliminata dalla finestra **origini dati** .<br /><br /> Se è necessario apportare una modifica, impostarla sulla colonna chiave esterna nella tabella correlata.|

## <a name="see-also"></a>Vedere anche
 [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
