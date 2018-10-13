---
title: Aggiungere codice al set di dati in applicazioni a più livelli | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- n-tier applications, extending datasets
ms.assetid: d43c2ccd-4902-43d8-b1a8-d10ca5d3210c
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 48f27d2e1bb72b7c5c0aaf1a66673beae003dd66
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202215"
---
# <a name="add-code-to-datasets-in-n-tier-applications"></a>Aggiungere il codice nei set di dati di applicazioni a più livelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
È possibile estendere le funzionalità di un set di dati creando un file di classe parziale per il set di dati e aggiungendovi il codice (invece di aggiungere codice per il *DatasetName*. File di DataSet). Classi parziali consentono al codice per una classe specifica da dividere tra più file fisici. Per altre informazioni, vedere [parziali](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) oppure [classi e metodi parziali](http://msdn.microsoft.com/library/804cecb7-62db-4f97-a99f-60975bd59fa1).  
  
 Il codice che definisce un set di dati viene generato ogni volta che vengono apportate modifiche alla definizione del set di dati (nelle [creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)). Questo codice viene generato anche quando si apportano modifiche durante l'esecuzione di una procedura guidata che consente di modificare la configurazione di un set di dati. Per evitare che il codice in corso l'eliminazione durante la rigenerazione di un set di dati, aggiungere codice al file di classe parziale del set di dati.  
  
 Per impostazione predefinita, dopo aver separato il set di dati e `TableAdapter` code, il risultato è un file di classe discreti in ogni progetto. Il progetto originale include un filenamed *DatasetName*. Vb (o *DatasetName*. Designer.cs) che contiene il `TableAdapter` codice. Il progetto che è designato nel **DataSetProject** proprietà dispone di un file denominato *DatasetName*. DataSet.Designer.vb (o *DatasetName*. DataSet.Designer.cs). Questo file contiene il codice del dataset.  
  
> [!NOTE]
>  Quando si separano i set di dati e `TableAdapter`s (impostando il **DataSetProject** proprietà), sarà spostate automaticamente classi parziali del dataset presenti nel progetto. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
> [!NOTE]
>  Quando il codice di convalida deve essere aggiunto, il [creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)fornisce funzionalità per la generazione <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> gestori eventi. Per altre informazioni, vedere [aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
### <a name="to-add-code-to-datasets-in-n-tier-applications"></a>Per aggiungere codice al set di dati in applicazioni a più livelli  
  
1.  Individuare il progetto che contiene il file con estensione XSD (il [creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)).  
  
2.  Selezionare il **XSD** file per aprire il [creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Pulsante destro del mouse la tabella di dati a cui si desidera aggiungere il codice (il nome della tabella nella barra del titolo) e thenselect**Visualizza codice**.  
  
     Una classe parziale viene creata e aperto nell'Editor di codice.  
  
4.  Aggiungere codice all'interno della dichiarazione di classe parziale.  
  
     Nell'esempio seguente mostra dove aggiungere il codice in CustomersDataTable NorthwindDataSet:  
  
    ```vb  
    Partial Public Class CustomersDataTable  
        ' Add code here to add functionality   
        ' to the CustomersDataTable.  
    End Class  
    ```  
  
    ```csharp  
    partial class CustomersDataTable  
    {  
        // Add code here to add functionality  
        // to the CustomersDataTable.  
    }  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
 [Aggiungere codice agli oggetti TableAdapter in applicazioni a più livelli](../data-tools/add-code-to-tableadapters-in-n-tier-applications.md)   
 [Oggetti TableAdapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Panoramica di TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Cenni preliminari sull'aggiornamento gerarchico](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [Creazione di applicazioni dati](../data-tools/creating-data-applications.md)   
 [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)

