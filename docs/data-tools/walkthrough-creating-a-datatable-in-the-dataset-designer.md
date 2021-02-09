---
title: Creare una DataTable nel Progettazione DataSet
description: In questa procedura dettagliata creare una DataTable (senza un TableAdapter) usando il Progettazione DataSet. Creare una nuova Windows Forms Application e aggiungervi un nuovo set di dati.
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
ms.workload:
- data-storage
ms.openlocfilehash: feec31fa0a9e34ad63e0b849d09084081e5710e5
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858176"
---
# <a name="walkthrough-create-a-datatable-in-the-dataset-designer"></a>Procedura dettagliata: creare un oggetto DataTable nel Progettazione DataSet

In questa procedura dettagliata viene illustrato come creare un oggetto <xref:System.Data.DataTable> (senza un TableAdapter) utilizzando il **Progettazione DataSet**. Per informazioni sulla creazione di tabelle di dati che includono TableAdapter, vedere [creare e configurare TableAdapter](../data-tools/create-and-configure-tableadapters.md).

## <a name="create-a-new-windows-forms-application"></a>Creare una nuova applicazione Windows Forms Application

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **desktop di Windows**.

3. Nel riquadro centrale selezionare il tipo di progetto **App Windows Form** .

4. Denominare il progetto **DataTableWalkthrough**, quindi scegliere **OK**.

     Il progetto **DataTableWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="add-a-new-dataset-to-the-application"></a>Aggiungere un nuovo set di dati all'applicazione

1. Nel menu **Progetto** selezionare **Aggiungi nuovo elemento**.

     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento** .

2. Nel riquadro a sinistra selezionare **dati**, quindi selezionare **DataSet** nel riquadro centrale.

3. Scegliere **Aggiungi**.

     Visual Studio aggiunge un file denominato **DataSet1. xsd** al progetto e lo apre nella **Progettazione DataSet**.

## <a name="add-a-new-datatable-to-the-dataset"></a>Aggiungere una nuova DataTable al set di dati

1. Trascinare un **DataTable** dalla scheda **DataSet** della **casella degli strumenti** nel **Progettazione DataSet**.

     Al set di dati viene aggiunta una tabella denominata **DataTable1** .

2. Fare clic sulla barra del titolo di **DataTable1** e rinominarla `Music` .

## <a name="add-columns-to-the-datatable"></a>Aggiungere colonne alla DataTable

1. Fare clic con il pulsante destro del mouse sulla tabella **Music** . Scegliere **Aggiungi**, quindi fare clic su **colonna**.

2. Assegnare un nome alla colonna `SongID` .

3. Nella finestra **Proprietà** impostare la proprietà <xref:System.Data.DataColumn.DataType%2A> su <xref:System.Int16?displayProperty=fullName>.

4. Ripetere questo processo e aggiungere le colonne seguenti:

     `SongTitle`: <xref:System.String?displayProperty=fullName>

     `Artist`: <xref:System.String?displayProperty=fullName>

     `Genre`: <xref:System.String?displayProperty=fullName>

## <a name="set-the-primary-key-for-the-table"></a>Impostare la chiave primaria per la tabella

Tutte le tabelle di dati devono avere una chiave primaria. Una chiave primaria identifica in modo univoco un record specifico in una tabella di dati.

Per impostare la chiave primaria, fare clic con il pulsante destro del mouse sulla colonna **SongID** , quindi scegliere **Imposta chiave primaria**. Viene visualizzata un'icona a chiave accanto alla colonna **SongID** .

## <a name="save-your-project"></a>Salvare il progetto

Per salvare il progetto **DataTableWalkthrough** , scegliere **Salva tutto** dal menu **file** .

## <a name="see-also"></a>Vedi anche

- [Creare e configurare i set di dati in Visual Studio](../data-tools/create-and-configure-datasets-in-visual-studio.md)
- [Associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
- [Convalida dei dati](../data-tools/validate-data-in-datasets.md)
