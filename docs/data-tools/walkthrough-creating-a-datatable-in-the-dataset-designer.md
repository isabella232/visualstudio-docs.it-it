---
title: 'Procedura dettagliata: Creazione di una DataTable in Progettazione Dataset'
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 1126117cb1fc26c4f61bfb0f6ed0e19e86ce9323
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072669"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Procedura dettagliata: Creare un oggetto DataTable in Progettazione Dataset

Questa procedura dettagliata illustra come creare un <xref:System.Data.DataTable> (senza un oggetto TableAdapter) usando il **Progettazione Dataset**. Per informazioni sulla creazione di tabelle di dati che includono oggetti TableAdapter, vedere [creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Creare una nuova applicazione Windows Forms Application

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **nome DataTableWalkthrough**, quindi scegliere **OK**.

     Il **nome DataTableWalkthrough** viene creato e aggiunto al progetto **Esplora soluzioni**.

## <a name="add-a-new-dataset-to-the-application"></a>Aggiungere un nuovo set di dati all'applicazione

1. Scegliere **Aggiungi nuovo elemento** dal menu **Progetto**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.

2. Nel riquadro di sinistra, selezionare **Data**, quindi selezionare **DataSet** nel riquadro centrale.

3. Scegliere **Aggiungi**.

     Visual Studio aggiunge un file denominato **DataSet1.xsd** al progetto e lo apre nella **Progettazione Dataset**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Aggiungere un nuovo DataTable al set di dati

1. Trascinare un **DataTable** dal **set di dati** scheda della finestra di **della casella degli strumenti** nel **Progettazione Dataset**.

     Una tabella denominata **DataTable1** viene aggiunto al set di dati.

2. Fare clic sulla barra del titolo della **DataTable1** e rinominarlo `Music`.

## <a name="add-columns-to-the-datatable"></a>Aggiungere colonne alla tabella di dati

1. Fare doppio clic il **musica** tabella. Puntare **Add**, quindi fare clic su **colonna**.

2. Assegnare un nome di colonna `SongID`.

3. Nella finestra **Proprietà** impostare la proprietà <xref:System.Data.DataColumn.DataType%2A> su <xref:System.Int16?displayProperty=fullName>.

4. Ripetere questo processo e aggiungere le colonne seguenti:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Impostare la chiave primaria per la tabella

Tutte le tabelle di dati devono avere una chiave primaria. Una chiave primaria identifica in modo univoco un record specifico in una tabella di dati.

Per impostare la chiave primaria, fare doppio clic il **SongID** colonna e quindi fare clic su **Imposta chiave primaria**. Icona di una chiave viene visualizzata accanto al **SongID** colonna.

## <a name="save-your-project"></a>Salvare il progetto

Per salvare la **nome DataTableWalkthrough** progetto scegliere la **File** dal menu **Salva tutto**.

## <a name="see-also"></a>Vedere anche

- [Creare e configurare i set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Convalida dei dati](../data-tools/validate-data-in-datasets.md)