---
title: Aggiungere codice a oggetti TableAdapter in applicazioni a più livelli | Microsoft Docs
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
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 942850e776cdd493afaad56b782b417db2040625
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673108"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Aggiungere il codice nei TableAdapter di applicazioni a più livelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per estendere la funzionalità di un, è possibile `TableAdapter` creare un file di classe parziale per `TableAdapter` e aggiungervi codice, anziché aggiungere codice a *DataSetName*. File DataSet. Designer). Le classi parziali consentono di dividere il codice per una classe specifica tra più file fisici. Per ulteriori informazioni, vedere [partial](https://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) o [partial (Type)](https://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).

 Il codice che definisce un `TableAdapter` viene generato ogni volta che vengono apportate modifiche a `TableAdapter` . Questo codice viene generato anche quando vengono apportate modifiche durante l'esecuzione di una procedura guidata che modifica la configurazione del `TableAdapter` . Per impedire l'eliminazione del codice durante la rigenerazione di un `TableAdapter` , aggiungere il codice al file di classe parziale di `TableAdapter` .

 Per impostazione predefinita, dopo aver separato il set di dati e il `TableAdapter` codice, il risultato è un file di classe discreto in ogni progetto. Il progetto originale include un file denominato *DataSetName*. Designer. vb (o *DataSetName*. Designer.cs) che contiene il `TableAdapter` codice. Il progetto designato nella proprietà del **progetto DataSet** dispone di un file denominato *DataSetName*. DataSet. designer. vb (o *DataSetName*. DataSet.Designer.cs) che contiene il codice del set di dati.

> [!NOTE]
> Quando si separano i set di dati e i (impostando `TableAdapter` la proprietà del **progetto DataSet** ), le classi del set di dati parziali esistenti nel progetto non verranno spostate automaticamente. Le classi parziali del set di dati esistenti devono essere spostate manualmente nel progetto DataSet.

> [!NOTE]
> In Progettazione DataSet sono disponibili funzionalità per la generazione <xref:System.Data.DataTable.ColumnChanging> e i <xref:System.Data.DataTable.RowChanging> gestori eventi quando è necessaria la convalida. Per altre informazioni, vedere [aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Per aggiungere codice utente a un TableAdapter in un'applicazione a più livelli

1. Individuare il progetto che contiene il file XSD (set di dati).

2. Fare doppio clic sul file **xsd** per aprire il set di dati.

3. Fare clic con il pulsante destro del mouse sull'oggetto `TableAdapter` a cui si desidera aggiungere il codice, quindi scegliere**Visualizza codice**.

     Viene creata una classe parziale che viene aperta nell'editor di codice.

4. Aggiungere codice all'interno della dichiarazione di classe parziale.

5. Nell'esempio seguente viene illustrato come aggiungere codice a `CustomersTableAdapter` in `NorthwindDataSet` :

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

## <a name="see-also"></a>Vedere anche
 [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md) [aggiungere codice ai set di dati in applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md) [oggetti TableAdapter](https://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364) [Panoramica Panoramica](https://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650) degli [aggiornamenti gerarchici](https://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)