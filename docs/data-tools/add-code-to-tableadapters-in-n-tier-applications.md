---
title: Aggiungere il codice nei TableAdapter di applicazioni a più livelli
description: Aggiungere codice agli adattatori tabella nelle applicazioni a più livelli. Creare un file di classe parziale per TableAdapter e aggiungerne il codice (anziché a DatasetName.DataSet.Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 55b6a64953944bacd8fcda73a9edeab00a99afc5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067208"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Aggiungere il codice nei TableAdapter di applicazioni a più livelli
È possibile estendere la funzionalità di un TableAdapter creando un file di classe parziale per l'oggetto TableAdapter e aggiungendo codice al tableadapter invece di aggiungere codice al file *DatasetName.DataSet.Designer.* Le classi parziali consentono di dividere il codice per una classe specifica tra più file fisici. Per altre informazioni, vedere [Parziale](/dotnet/visual-basic/language-reference/modifiers/partial) o [parziale (tipo).](/dotnet/csharp/language-reference/keywords/partial-type)

Il codice che definisce un TableAdapter viene generato ogni volta che vengono apportate modifiche all'oggetto TableAdapter nel set di dati. Questo codice viene generato anche quando vengono apportate modifiche durante l'esecuzione di una procedura guidata che modifica la configurazione dell'oggetto TableAdapter. Per impedire l'eliminazione del codice durante la rigenerazione di un TableAdapter, aggiungere codice al file di classe parziale dell'oggetto TableAdapter.

Per impostazione predefinita, dopo aver separato il set di dati e il codice TableAdapter, il risultato è un file di classe discreto in ogni progetto. Il progetto originale ha un file denominato *DatasetName.Designer.vb* (o *DatasetName.Designer.cs)* che contiene il codice TableAdapter. Il progetto designato nella proprietà **Dataset Project** contiene un file denominato *DatasetName.DataSet.Designer.vb* (o *DatasetName.DataSet.Designer.cs)* che contiene il codice del set di dati.

> [!NOTE]
> Quando si separano i dataset e gli oggetti TableAdapter (impostando la proprietà **Progetto DataSet**), le classi parziali del dataset presenti nel progetto non vengono spostate automaticamente. Le classi di set di dati parziali esistenti devono essere spostate manualmente nel progetto di set di dati.

> [!NOTE]
> Il set di dati fornisce funzionalità per la generazione <xref:System.Data.DataTable.ColumnChanging> di gestori eventi e quando è necessaria la <xref:System.Data.DataTable.RowChanging> convalida. Per altre informazioni, vedere [Aggiungere la convalida a un set di dati a più livelli.](../data-tools/add-validation-to-an-n-tier-dataset.md)

[!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]

## <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Per aggiungere codice utente a un oggetto TableAdapter in un'applicazione a più livelli

1. Individuare il progetto che contiene il file *xsd.*

2. Fare doppio clic sul file *xsd* per aprire il **Progettazione DataSet**.

3. Fare clic con il pulsante destro del mouse sull'oggetto TableAdapter a cui si vuole aggiungere il codice e **quindi scegliere Visualizza codice.**

     Viene creata una classe parziale che viene aperta nell'editor di codice.

4. Aggiungere codice all'interno della dichiarazione di classe parziale.

5. Nell'esempio seguente viene illustrato dove aggiungere codice a `CustomersTableAdapter` in `NorthwindDataSet` :

    ```vb
    Partial Public Class CustomersTableAdapter
        ' Add code here to add functionality
        ' to the CustomersTableAdapter.
    End Class
    ```

    ```csharp
    public partial class CustomersTableAdapter
    {
        // Add code here to add functionality
        // to the CustomersTableAdapter.
    }
    ```

## <a name="see-also"></a>Vedi anche

- [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)
- [Aggiungere il codice nei set di dati di applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md)
- [Creare e configurare oggetti TableAdapter](create-and-configure-tableadapters.md)
- [Panoramica dell'aggiornamento gerarchico](hierarchical-update.md)
