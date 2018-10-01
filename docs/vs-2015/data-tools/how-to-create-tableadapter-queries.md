---
title: 'Procedura: creare query TableAdapter | Microsoft Docs'
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
- TableAdapters, creating queries
- queries [Visual Studio], creating
- data [Visual Studio], TableAdapter queries
- queries [Visual Studio], TableAdapters
ms.assetid: df0cf4a5-e9cc-4de6-8b94-ce74fb7b2452
caps.latest.revision: 20
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: f7d4bd84d5cd4538d06048fd6953fa95fc344da0
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528125"
---
# <a name="how-to-create-tableadapter-queries"></a>Procedura: creare query TableAdapter
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Query TableAdapter sono istruzioni SQL o stored procedure che è possibile eseguire l'applicazione su un database.  
  
 Aggiungere tutte le query a un oggetto TableAdapter in quanto richiede l'applicazione. Query TableAdapter vengono visualizzati come metodi su un oggetto TableAdapter. Quando si crea una query denominata `FillByCity` che accetta un parametro che rappresenta il valore di città, la query viene aggiunta all'oggetto TableAdapter. Viene aggiunto come un metodo tipizzato che accetta il tipo corretto di parametri come argomento, ovvero in questo caso una stringa che rappresenta il valore di città. Si chiama la query TableAdapter esattamente come qualsiasi metodo su qualsiasi oggetto. Ad esempio, il codice seguente esegue il `FillByCity` Progettazione query e i riempimenti il `Customers` tabella con tutti i clienti con un valore city di `Seattle`:  
  
 [!code-csharp[VbRaddataTableAdapters#1](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataTableAdapters/CS/Form1.cs#1)]
 [!code-vb[VbRaddataTableAdapters#1](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataTableAdapters/VB/Form1.vb#1)]  
  
 Le query TableAdapter sono riempire una tabella di dati (`Fill` e `FillBy` query) o restituire nuove tabelle di dati, popolate con i dati restituiti dalla query (`GetData` e `GetDataBy` query).  
  
 È possibile aggiungere query TableAdapter esistente eseguendo il [modifica di TableAdapter](../data-tools/editing-tableadapters.md). (Fare doppio clic su qualsiasi oggetto TableAdapter e scegliere **Aggiungi Query**.)  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="create-a-query-in-the-dataset-designer"></a>Creare una query in Progettazione Dataset  
  
#### <a name="to-add-a-query-to-a-tableadapter-in-the-dataset-designer"></a>Per aggiungere una query a un oggetto TableAdapter in Progettazione Dataset  
  
1.  Aprire un set di dati di **Progettazione Dataset**. Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3).  
  
2.  Il TableAdapter desiderato e scegliere **Aggiungi Query**.  
  
     oppure  
  
3.  Trascinare un **Query** dalle **set di dati** scheda della finestra di **della casella degli strumenti** in una tabella nella finestra di progettazione.  
  
     Il **configurazione guidata Query TableAdapter** apre.  
  
4.  Completare la procedura guidata. la query viene aggiunto all'oggetto TableAdapter.  
  
## <a name="create-a-query-directly-on-a-form-in-your-windows-application"></a>Creare una Query direttamente in un Form nell'applicazione Windows  
 Se si dispone di un'istanza di un oggetto TableAdapter sul form è possibile aggiungere una query usando il [finestra di dialogo Generatore di criteri di ricerca](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d), che aggiunge un <xref:System.Windows.Forms.ToolStrip> controllo al form che accetti qualsiasi input in cui i parametri richiesti dalla query, nonché un pulsante per eseguire la query.  
  
#### <a name="to-add-a-query-to-a-tableadapter-using-the-search-criteria-dialog-box"></a>Per aggiungere una query a un TableAdapter utilizzando la finestra di dialogo di criteri di ricerca  
  
1.  Nella barra dei componenti, selezionare un oggetto TableAdapter.  
  
2.  Fare clic sul tag intelligente dell'oggetto TableAdapter e scegliere **Aggiungi Query**.  
  
3.  Completare la finestra di dialogo e la query viene aggiunto all'oggetto TableAdapter. Per altre informazioni, vedere [finestra di dialogo Generatore di criteri di ricerca](http://msdn.microsoft.com/library/0b306b92-f35e-45ef-a4be-3f653cd00c3d).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Procedura: modificare query TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)   
 [Procedura: Connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Procedura: esplorare i dati con il controllo BindingNavigator di Windows Form](http://msdn.microsoft.com/library/0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb)   
 [Procedura dettagliata: Visualizzazione dei dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Procedura dettagliata: creazione di un oggetto TableAdapter con più query](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)