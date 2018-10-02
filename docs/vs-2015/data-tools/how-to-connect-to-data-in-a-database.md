---
title: 'Procedura: connettersi ai dati in un Database | Microsoft Docs'
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
- databases, connecting to
- data sources, databases
- data [Visual Studio], connecting to databases
- data sources, creating
- database connections
ms.assetid: 6c56e54e-8834-4297-85aa-cc1a443ba556
caps.latest.revision: 55
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 72b278305995e2edb86e612e0c5c3789c8ce756a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47520003"
---
# <a name="how-to-connect-to-data-in-a-database"></a>Procedura: connettersi ai dati di un database
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile connettere l'applicazione a un database usando Visual Studio. Dopo avere creato la connessione dati, Visual Studio genera un modello dati che verrà usato dall'applicazione per interagire con i dati del database. Gli oggetti nel modello di dati vengono visualizzati nei [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). È quindi possibile creare controlli associati a dati trascinando elementi dal **finestra Origini dati** all'area di progettazione. Per altre informazioni, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
 In questo argomento vengono fornite istruzioni per la connessione a un database e la creazione dei tipi di modelli dati seguenti:  
  
-   Set di dati  
  
-   Entity Data Model (EDM)  
  
> [!NOTE]
>  È inoltre possibile usare Visual Studio per creare classi LINQ to SQL da un database. Tuttavia, classi LINQ to SQL non vengono visualizzati nel **Zdroje dat** finestra e pertanto non possono essere trascinate direttamente in una finestra di progettazione per creare controlli associati a dati. Per altre informazioni sulla creazione di LINQ alle classi di SQL da un database, vedere [procedura: creare classi LINQ to SQL mappate a tabelle e visualizzazioni (O/R Designer)](../data-tools/how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
##  <a name="dataset"></a> La connessione a un Database e la creazione di un set di dati  
 Quando si crea un set di dati basato su un database, Visual Studio crea un set di classi che rappresentano una visualizzazione programmabile dei dati. La classe principale viene chiamata un *dataset tipizzato*. Il dataset tipizzato contiene oggetti della tabella dati che rappresentano tabelle del database. Per altre informazioni sui dataset tipizzati, vedere [strumenti di set di dati in Visual Studio](../data-tools/dataset-tools-in-visual-studio.md).  
  
 Dopo avere creato un set di dati, è possibile creare controlli WPF o Windows Form con associazione a dati trascinando oggetti dataset dalla finestra Origini dati a Progettazione WPF o a Progettazione Windows Form.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-a-dataset"></a>Per connettere l'applicazione a un database e creare un set di dati  
  
1.  Creare un nuovo progetto o aprirne uno esistente in Visual Studio.  
  
2.  Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.  
  
     Il **configurazione guidata origine dati** apre.  
  
3.  Nel **scegliere un tipo di origine dati** pagina, selezionare **Database**, quindi fare clic su **successivo**.  
  
4.  Nel **scegliere un modello di Database** pagina, selezionare **set di dati**, quindi fare clic su **successivo**.  
  
5.  Nel **Seleziona connessione dati** pagina, selezionare una connessione dati dall'elenco delle connessioni disponibili e quindi fare clic su **successivo**.  
  
     Se la connessione dati desiderata non è disponibile, creare una nuova connessione seguendo i passaggi descritti in [creazione di una nuova connessione al Database](#CreatingDataConnection).  
  
6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, facoltativamente, deselezionare le **Sì, Salva la connessione come** casella di controllo se si desidera salvare la stringa di connessione direttamente nel file compilato applicazione. Per impostazione predefinita, la connessione viene salvata nel file di configurazione dell'applicazione. Per altre informazioni, vedere [procedura: salvare e modificare le stringhe di connessione](~/E:/Repos/visualstudio-docs-pr/docs/data-tools/how-to-save-and-edit-connection-strings.md).  
  
7.  Nel **Scegli oggetti di Database** pagina, selezionare gli oggetti di database che verrà utilizzato nell'applicazione. È anche possibile scegliere di sostituire il valore predefinito **nome del set di dati**.  
  
8.  Scegliere **Fine**. Il set di dati appena creato è ora disponibile nel **Zdroje dat** finestra.  
  
    > [!NOTE]
    >  Se il **Zdroje dat** finestra non è aperta, fare clic su **Mostra origini dati** sul **dati** menu per aprire la finestra.  
  
9. È ora possibile trascinare elementi dal **Zdroje dat** finestra di progettazione WPF, la finestra di progettazione Windows Form, o il [Component Designer](http://msdn.microsoft.com/library/61a3a450-5b15-465e-bd9a-72a6c8c2b282) per creare controlli associati a dati. Per altre informazioni, vedere [associare controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md).  
  
##  <a name="edm"></a> La connessione al Database e la creazione di un Entity Data Model  
 Quando si crea un Entity Data Model basato su un database, Visual Studio crea un set di classi che rappresentano una visualizzazione programmabile dei dati. Per altre informazioni su Entity Data Model e ADO.NET Entity Framework, vedere [Panoramica di Entity Framework](http://msdn.microsoft.com/library/a2166b3d-d8ba-4a0a-8552-6ba1e3eaaee0).  
  
 Dopo avere creato un Entity Data Model, è possibile creare controlli WPF o Windows Form con associazione a dati trascinando oggetti entità dalla finestra Origini dati a Progettazione WPF.  
  
#### <a name="to-connect-your-application-to-a-database-and-create-an-entity-data-model"></a>Per connettere l'applicazione a un database e creare un Entity Data Model  
  
1.  Creare un nuovo progetto o aprirne uno esistente in Visual Studio.  
  
2.  Seguire i passaggi nel **procedura guidata Entity Data Model** per connettersi a un database e specificare il contenuto del modello. Per altre informazioni, vedere [procedura: creare un File con estensione edmx nuovo](http://msdn.microsoft.com/en-us/beb8189e-e51c-4051-839c-9902c224abf2).  
  
3.  Dopo aver completato la **Entity Data Model Wizard**Entity Data Model creato viene aperto in Entity Data Model Designer e gli oggetti dati sono ora disponibili nel **Zdroje dat** finestra.  
  
    > [!NOTE]
    >  Se il **Zdroje dat** finestra non è aperta, fare clic su **Mostra origini dati** sul **dati** menu per aprire la finestra.  
  
4.  Se la finestra di progettazione WPF è aperto, è possibile trascinare elementi dal **Zdroje dat** finestra di progettazione per creare controlli associati a Entity Data Model. Per altre informazioni, vedere [WPF di associare controlli ai dati in Visual Studio](../data-tools/bind-wpf-controls-to-data-in-visual-studio2.md).  
  
     Se la finestra di progettazione Windows Form è aperto, non è possibile trascinare elementi dal **Zdroje dat** nella finestra di progettazione. Per creare controlli associati a Entity Data Model, è necessario compilare il progetto, aggiungere una nuova origine dati dell'oggetto basata sull'Entity Data Model, quindi trascinare tali oggetti nella finestra di progettazione.  
  
##  <a name="CreatingDataConnection"></a> Creazione di una nuova connessione al Database  
 Quando si usa la **configurazione guidata origine dati**o nella **procedura guidata Entity Data Model**, è necessario specificare una connessione al database di cui si desidera utilizzare. Se non è già presente una connessione al database, crearne una eseguendo la procedura indicata di seguito.  
  
 Queste istruzioni presuppongono che si è già iniziato la **configurazione guidata origine dati** o il **Entity Data Model Wizard** come descritto in [la connessione al Database e la creazione di un set di dati ](#dataset) e [ci si connette al Database e la creazione di un Entity Data Model](#edm).  
  
#### <a name="to-create-a-new-database-connection"></a>Per creare una nuova connessione al database  
  
1.  Nel **Seleziona connessione dati** pagina della **configurazione guidata origine dati** o le **procedura guidata Entity Data Model**, fare clic su **nuova connessione**.  
  
     Si verificherà una delle azioni seguenti:  
  
    -   Se già stata creata una connessione dati in Visual Studio, il **Aggiungi connessione** verrà visualizzata la finestra di dialogo.  
  
    -   Se questa è la prima connessione dati è stato creato in Visual Studio, il **Scegli origine dati** consente di visualizzare la finestra di dialogo. Selezionare il tipo di database che si desidera connettersi a e quindi fare clic su **OK** per visualizzare i **Aggiungi connessione** nella finestra di dialogo.  
  
2.  Nel **Aggiungi connessione** finestra di dialogo immettere le informazioni richieste. Il **Aggiungi connessione** nella finestra di dialogo è diversa per ogni tipo di provider di dati.  
  
    > [!NOTE]
    >  Se selezionato **zdroj dat** nel **Aggiungi connessione** la finestra di dialogo non è l'origine dati si desidera connettersi, fare clic su **modifica** per aprire il **i dati delle modifiche Origine** finestra di dialogo e quindi selezionare un'origine dati diversa.  
  
3.  Nel **Aggiungi connessione** finestra di dialogo, fare clic su **OK**.  
  
     Si torna al **Seleziona connessione dati** pagina del **configurazione guidata origine dati** o nella **procedura guidata Entity Data Model**.  
  
4.  Nel **Seleziona connessione dati** pagina, assicurarsi che sia selezionata la nuova connessione dati e quindi fare clic su **successivo**.  
  
5.  Completare i passaggi rimanenti **configurazione guidata origine dati** o nella **Entity Data Model Wizard**.  
  
## <a name="net-framework-security"></a>Sicurezza di .NET Framework  
 L'archiviazione di informazioni riservate, ad esempio una password, può avere implicazioni sulla sicurezza dell'applicazione. L'autenticazione di Windows, detta anche sicurezza integrata, consente di controllare l'accesso a un database in modo più sicuro. Per altre informazioni, vedere [Protezione delle informazioni di connessione](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="see-also"></a>Vedere anche  
 [Aggiungere nuove origini dati](../data-tools/add-new-data-sources.md)   
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Connessione a un'origine dati](http://msdn.microsoft.com/library/9abc3f92-1be3-4e1a-b360-762dc689650e)