---
title: Creazione e modifica di dataset tipizzati | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- Designer_Microsoft.VSDesigner.DataSource.Designer.DataSourceRootDesigner
- vs.data.adddataset
dev_langs:
- VB
- CSharp
- C++
- aspx
- aspx
helpviewer_keywords:
- datasets [Visual Basic], visual designer
- data [Visual Studio], Dataset Designer
- Dataset Designer
ms.assetid: cd0dbe93-be9b-41e4-bc39-e9300678c1f2
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 8c18717cd2a5c7e05b79dbe575d919ef0c8670dd
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49225842"
---
# <a name="creating-and-editing-typed-datasets"></a>Creazione e modifica di dataset tipizzati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il**Progettazione Dataset** è un set di strumenti visivi che è possibile usare per creare e modificare DataSet tipizzati e i singoli elementi in essi contenuti.  
  
 Il **Progettazione Dataset** fornisce rappresentazioni visive di oggetti contenuti nel dataset tipizzati. Si creano e modificano [TableAdapter](../data-tools/tableadapter-overview.md), [query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md), <xref:System.Data.DataTable>s <xref:System.Data.DataColumn>s, e <xref:System.Data.DataRelation>s con il **Progettazione Dataset**.  
  
 Per aprire la **Progettazione Dataset**, fare doppio clic su un set di dati **Esplora soluzioni**, o fare doppio clic su un set di dati nel **Zdroje dat** finestra e fare clic su **modifica Set di dati con Progettazione**. Per altre informazioni, vedere [procedura: aprire un set di dati in Progettazione Dataset](http://msdn.microsoft.com/library/36fc266f-365b-42cb-aebb-c993dc2c47c3). Aggiunta di una nuova <xref:System.Data.DataSet> elementi con il **Aggiungi nuovo elemento** verrà aperta la finestra di dialogo il **Progettazione Dataset** con un set di dati vuoto pronto per la modifica.  
  
> [!NOTE]
>  Il **Progettazione Dataset** può essere utilizzato per estendere le funzionalità di un set di dati. Fare doppio clic sulla finestra di progettazione o fare clic e scegliere **Visualizza codice** per creare un file di classe parziale in cui è possibile aggiungere codice al set di dati non verrà modificato o eliminato dalla finestra di progettazione. Per informazioni su come estendere le funzionalità di un oggetto TableAdapter, vedere [estendono la funzionalità di un oggetto TableAdapter](../data-tools/extend-the-functionality-of-a-tableadapter.md).  
  
 La tabella seguente elenca le attività comuni che è possibile eseguire con il **Progettazione Dataset**.  
  
|A|Vedere|  
|--------|---------|  
|Creare un oggetto TableAdapter|[Creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md)|  
|Modificare un TableAdapter|[Procedura: modificare oggetti TableAdapter](http://msdn.microsoft.com/library/ca178745-e35a-45f1-a395-23cddfd8f855)|  
|Creare una query TableAdapter|[Procedura: Creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md)|  
|Modificare una query TableAdapter|[Procedura: Modificare query TableAdapter](../data-tools/how-to-edit-tableadapter-queries.md)|  
|Creare un <xref:System.Data.DataTable>|[Procedura: Creare tabelle di dati](../data-tools/how-to-create-data-tables.md)|  
|Modificare un <xref:System.Data.DataTable>|[Progettazione di DataTables](../data-tools/designing-datatables.md)|  
|Creare un <xref:System.Data.DataColumn>|[Procedura: aggiungere colonne a un oggetto DataTable](http://msdn.microsoft.com/library/8ca21f77-b99a-47a7-a656-7cfd7a1bd9df)|  
|Creare una relazione tra due <xref:System.Data.DataTable>s|[Procedura: creare DataRelation mediante Progettazione Dataset](http://msdn.microsoft.com/library/a3ab4803-0b50-4b74-9920-ab20bfbf1aa2)|  
|Estendere le funzionalità del set di dati|[Procedura: estendere la funzionalità di un set di dati](http://msdn.microsoft.com/library/dfbc21eb-7ea2-4942-addd-49677f5493be)|  
|Aggiungere la convalida a una tabella di dati <xref:System.Data.DataTable.ColumnChanging> evento|[Procedura: convalidare i dati durante la modifica delle colonne](http://msdn.microsoft.com/library/a2680600-67b6-4a40-a77e-b5bc638281c5)|  
|Aggiungere la convalida a una tabella di dati <xref:System.Data.DataTable.RowChanging> evento|[Procedura: convalidare i dati durante la modifica delle righe](http://msdn.microsoft.com/library/afc03c77-dfed-4302-9376-929400468ecc)|  
  
## <a name="creating-objects-on-the-design-surface"></a>Creazione di oggetti nell'area di progettazione  
 È possibile creare i set di dati aggiungendo e modificando i singoli oggetti che costituiscono un set di dati. La tabella seguente fornisce una spiegazione dei diversi oggetti disponibili nel **set di dati** scheda le **della casella degli strumenti** che possono essere trascinati nell'area di progettazione:  
  
|Object|Descrizione|  
|------------|-----------------|  
|TableAdapter|Contiene una raccolta di comandi dati e una connessione dati che vengono usati per comunicare con il database sottostante e popolare una tabella di dati. Per altre informazioni, vedere [TableAdapter Overview](../data-tools/tableadapter-overview.md) e [creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).|  
|Query|Query TableAdapter sono fortemente tipizzato i metodi che eseguono istruzioni SQL e stored procedure. Esegue una query TableAdapter popola una tabella di dati con i dati o eseguire altre attività di database. Per altre informazioni, vedere [procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md). La query trascinando una query in una tabella aggiunta a tale tabella, mentre il trascinamento di una query in un'area vuota del **Progettazione Dataset** crea una query globale. Per altre informazioni, vedere [procedura: aggiungere query globali a un oggetto TableAdapter](../data-tools/how-to-add-global-queries-to-a-tableadapter.md).|  
|<xref:System.Data.DataTable>|Rappresenta una raccolta in memoria delle righe restituite da un database.|  
|Relazione (<xref:System.Data.DataRelation>)|Rappresenta una relazione padre-figlio tra due <xref:System.Data.DataTable>s. Per altre informazioni, vedere [Introduzione agli oggetti DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192) e [procedura dettagliata: creazione di una relazione tra le tabelle dati](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82).|  
  
> [!NOTE]
>  Il **Progettazione Dataset** si connette a un database sottostante viene creato solo quando un set di dati; la finestra di progettazione non rileva automaticamente le successive modifiche al database. Per aggiornare un XSD esistente, eseguire nuovamente il **configurazione guidata**. Se le relazioni della tabella sono state modificate, rimuovere e aggiungere nuovamente le relative tabelle al file con estensione xsd.  
  
## <a name="linq-to-dataset"></a>LINQ to Dataset  
 [!INCLUDE[linq_dataset](../includes/linq-dataset-md.md)] Abilita [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d) sui dati in un <xref:System.Data.DataSet> oggetto. Per altre informazioni, vedere [LINQ to DataSet](http://msdn.microsoft.com/library/743e3755-3ecb-45a2-8d9b-9ed41f0dcf17).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un set di dati con Progettazione Dataset](../data-tools/walkthrough-creating-a-dataset-with-the-dataset-designer.md)   
 [Procedura dettagliata: Creazione di un oggetto TableAdapter con più query](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md)   
 [Procedura dettagliata: Creazione di una DataTable in Progettazione Dataset](../data-tools/walkthrough-creating-a-datatable-in-the-dataset-designer.md)   
 [Procedura dettagliata: Creazione di una relazione tra le tabelle di dati](http://msdn.microsoft.com/library/9b3f1c87-7098-4ed4-a710-cde8f8059f82)   
 [Procedura dettagliata: Visualizzazione dei dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992)   
 [Strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio di dati](../data-tools/saving-data.md)