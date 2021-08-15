---
title: Creare un oggetto DataTable nel Progettazione DataSet
description: In questa procedura dettagliata viene creato un oggetto DataTable (senza TableAdapter) usando il Progettazione DataSet. Creare una nuova Windows'applicazione Forms e aggiungerne uno nuovo.
ms.custom: SEO-VS-2020
ms.date: 10/19/2016
ms.topic: conceptual
helpviewer_keywords:
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 08c5355ab65947ef41a45f5d7f66f5b5e82a6994e9f0f0190870b28d687ffa7e
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346570"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Procedura dettagliata: Creare un oggetto DataTable nel Progettazione DataSet

In questa procedura dettagliata viene illustrato come creare <xref:System.Data.DataTable> un oggetto (senza un TableAdapter) **usando** Progettazione DataSet . Per informazioni sulla creazione di tabelle di dati che includono TableAdapter, vedere [Creare e configurare oggetti TableAdapter.](../data-tools/create-and-configure-tableadapters.md)

## <a name="create-a-new-windows-forms-application"></a>Creare una nuova applicazione Windows Forms Application

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop.**

3. Nel riquadro centrale selezionare il tipo di **progetto Windows app Forms.**

4. Assegnare al **progetto il nome DataTableWalkthrough** e quindi scegliere **OK.**

     Il **progetto DataTableWalkthrough** viene creato e aggiunto **Esplora soluzioni**.

## <a name="add-a-new-dataset-to-the-application"></a>Aggiungere un nuovo set di dati all'applicazione

1. Nel menu **Progetto** selezionare **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

2. Nel riquadro sinistro selezionare Dati **e** quindi Selezionare **DataSet** nel riquadro centrale.

3. Scegliere **Aggiungi**.

     Visual Studio aggiunge un file denominato **DataSet1.xsd** al progetto e lo apre nel **Progettazione DataSet**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Aggiungere un nuovo oggetto DataTable al set di dati

1. Trascinare **un oggetto DataTable** dalla **scheda DataSet** della casella **degli** strumenti **nel Progettazione DataSet**.

     Una tabella denominata **DataTable1** viene aggiunta al set di dati.

2. Fare clic sulla barra del titolo di **DataTable1** e rinominarla `Music` .

## <a name="add-columns-to-the-datatable"></a>Aggiungere colonne all'oggetto DataTable

1. Fare clic con il pulsante destro **del mouse Musica** tabella. Scegliere **Aggiungi**, quindi fare clic su **Colonna**.

2. Assegnare alla colonna il nome `SongID` .

3. Nella finestra **Proprietà** impostare la proprietà <xref:System.Data.DataColumn.DataType%2A> su <xref:System.Int16?displayProperty=fullName>.

4. Ripetere questo processo e aggiungere le colonne seguenti:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Impostare la chiave primaria per la tabella

Tutte le tabelle dati devono avere una chiave primaria. Una chiave primaria identifica in modo univoco un record specifico in una tabella dati.

Per impostare la chiave primaria, fare clic con il pulsante destro del mouse **sulla colonna SongID** e quindi scegliere **Imposta chiave primaria**. Accanto alla colonna SongID viene visualizzata **un'icona a** forma di chiave.

## <a name="save-your-project"></a>Salvare il progetto

Per salvare il **progetto DataTableWalkthrough,** **scegliere** Salva tutto dal menu **File.**

## <a name="see-also"></a>Vedi anche

- [Creare e configurare i set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Convalida dei dati](../data-tools/validate-data-in-datasets.md)
