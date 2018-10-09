---
title: Aggiungere codice agli oggetti TableAdapter in applicazioni a più livelli | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- TableAdapters, n-tier applications
- n-tier applications, extending TableAdapters
ms.assetid: dafac00e-df9d-4d4a-95a6-e34b4d099425
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: bd46596ff474a33be42b8c5118404845a39c2b7d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527319"
---
# <a name="add-code-to-tableadapters-in-n-tier-applications"></a>Aggiungere il codice nei TableAdapter di applicazioni a più livelli
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [aggiungere il codice TableAdapter in applicazioni a più livelli](https://docs.microsoft.com/visualstudio/data-tools/add-code-to-tableadapters-in-n-tier-applications).  
  
  
È possibile estendere le funzionalità di un `TableAdapter` creando un file di classe parziale per il `TableAdapter` e l'aggiunta di codice alla (invece di aggiungere codice per il *DatasetName*. File di DataSet). Classi parziali consentono al codice per una classe specifica da dividere tra più file fisici. Per altre informazioni, vedere [parziali](http://msdn.microsoft.com/library/7adaef80-f435-46e1-970a-269fff63b448) oppure [parziale (tipo)](http://msdn.microsoft.com/library/27320743-a22e-4c7b-b0b3-53afe3607334).  
  
 Il codice che definisce una `TableAdapter` viene generato ogni volta che vengono apportate modifiche al `TableAdapter` (nelle [creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)). Questo codice viene generato anche quando vengono apportate modifiche durante l'esecuzione di una procedura guidata modifica la configurazione della `TableAdapter`. Per impedire che il codice in corso l'eliminazione durante la rigenerazione di una `TableAdapter`, aggiungere codice al file di classe parziale del `TableAdapter`.  
  
 Per impostazione predefinita, dopo aver separato il set di dati e `TableAdapter` code, il risultato è un file di classe discreti in ogni progetto. Il progetto originale include un file denominato *DatasetName*. Vb (o *DatasetName*. Designer.cs) che contiene il `TableAdapter` codice. Il progetto che è designato nel **DataSetProject** proprietà ha un file denominato *DatasetName*. DataSet.Designer.vb (o *DatasetName*. DataSet.Designer.cs) che contiene il codice di set di dati.  
  
> [!NOTE]
>  Quando si separano i set di dati e `TableAdapter`s (impostando il **DataSetProject** proprietà), classi parziali del dataset presenti nel progetto non verranno spostate automaticamente. Le classi parziali del dataset devono essere spostate manualmente nel progetto di dataset.  
  
> [!NOTE]
>  Il [creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md) fornisce funzionalità per la generazione <xref:System.Data.DataTable.ColumnChanging> e <xref:System.Data.DataTable.RowChanging> gestori di eventi quando la convalida è necessaria. Per altre informazioni, vedere [aggiungere la convalida a un set di dati a più livelli](../data-tools/add-validation-to-an-n-tier-dataset.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
### <a name="to-add-user-code-to-a-tableadapter-in-an-n-tier-application"></a>Aggiungere il codice utente in un oggetto TableAdapter in un'applicazione a più livelli  
  
1.  Individuare il progetto che contiene il file con estensione XSD (il [creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)).  
  
2.  Fare doppio clic il **XSD** file per aprire il [creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md).  
  
3.  Fare doppio clic il `TableAdapter` che si desidera aggiungere il codice per e quindi selezionare**Visualizza codice**.  
  
     Una classe parziale viene creata e aperto nell'Editor di codice.  
  
4.  Aggiungere codice all'interno della dichiarazione di classe parziale.  
  
5.  L'esempio seguente mostra dove aggiungere il codice per il `CustomersTableAdapter` nella `NorthwindDataSet`:  
  
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
 [Panoramica delle applicazioni dati a più livelli](../data-tools/n-tier-data-applications-overview.md)   
 [Aggiungere codice al set di dati in applicazioni a più livelli](../data-tools/add-code-to-datasets-in-n-tier-applications.md)   
 [Oggetti TableAdapter](http://msdn.microsoft.com/library/09416de9-134c-4dc7-8262-6c8d81e3f364)   
 [Panoramica di TableAdapterManager](http://msdn.microsoft.com/library/33076d42-6b41-491a-ac11-6c6339aea650)   
 [Cenni preliminari sull'aggiornamento gerarchico](http://msdn.microsoft.com/library/c4f8e8b9-e4a5-4a02-8462-d03d1e8222d6)   
 [Creazione di applicazioni dati](../data-tools/creating-data-applications.md)
