---
title: 'Procedura dettagliata: Creazione di un set di dati con Progettazione Dataset | Microsoft Docs'
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
- datasets [Visual Basic], walkthroughs
- XML schemas, creating datasets
- data [Visual Studio], Dataset Designer
- Dataset Designer, walkthroughs
- datasets [Visual Basic], creating
ms.assetid: 12360f54-db6c-45d2-a91f-fee43214b555
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 7c17a93a5d250ce620c37a2a0a89472bf760750b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526835"
---
# <a name="walkthrough-creating-a-dataset-with-the-dataset-designer"></a>Procedura dettagliata: creazione di un dataset con Progettazione DataSet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata si creerà un set di dati usando il **Progettazione Dataset**. Illustra in dettaglio il processo di creazione di un nuovo progetto e aggiunta di una nuova **set di dati** elemento ad esso. Si apprenderà come creare le tabelle basate su tabelle in un database senza usare una procedura guidata.  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di una nuova **applicazioni Windows** progetto.  
  
-   Aggiunta di un oggetto vuoto **set di dati** elemento al progetto.  
  
-   Creazione e configurazione di un'origine dati nell'applicazione creando un set di dati con il **Progettazione Dataset**.  
  
-   Creazione di una connessione al database Northwind nel **Esplora Server**.  
  
-   Creazione di tabelle con i TableAdapter del set di dati basati su tabelle nel database.  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind nella versione SQL Server o Access. Per altre informazioni, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="creating-a-new-windows-application-project"></a>Crea un nuovo progetto applicazione Windows  
  
#### <a name="to-create-a-new-windows-application-project"></a>Per creare un nuovo progetto Applicazione Windows  
  
1.  Dal **File** menu, creare un nuovo progetto.  
  
2.  Scegliere un linguaggio di programmazione le **tipi di progetto** riquadro.  
  
3.  Fare clic su **applicazione di Windows** nel **modelli** riquadro.  
  
4.  Denominare il progetto `DatasetDesignerWalkthrough`, quindi fare clic su **OK**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per il progetto verrà aggiunto **Esplora soluzioni** e visualizzare un nuovo form nella finestra di progettazione.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Aggiunta di un nuovo set di dati all'applicazione  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Per aggiungere un nuovo elemento di set di dati al progetto  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi nuovo elemento**.  
  
2.  Nel **modelli** finestra di **Aggiungi nuovo elemento** nella finestra di dialogo fare clic su **set di dati**.  
  
3.  Nome del set di dati `NorthwindDataset`, quindi fare clic su **Add**.  
  
     [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] verrà aggiunto un file denominato **NorthwindDataSet. xsd** al progetto e aprirlo nel **Progettazione Dataset**.  
  
## <a name="creating-a-data-connection-in-server-explorer"></a>Creazione di una connessione dati in Esplora Server  
  
#### <a name="to-create-a-connection-to-the-northwind-database"></a>Per creare una connessione al database Northwind  
  
1.  Nel **View** menu, fare clic su **Esplora Server**.  
  
2.  Nelle **Esplora Server**, fare clic sui **Connetti al Database** pulsante.  
  
3.  Creare una connessione al database di esempio Northwind.  
  
    > [!NOTE]
    >  È possibile connettersi alla versione SQL Server o Access di Northwind per questa procedura dettagliata.  
  
## <a name="creating-the-tables-in-the-dataset"></a>Creazione di tabelle nel set di dati  
 In questa sezione verrà illustrate le procedure aggiungere tabelle al set di dati.  
  
#### <a name="to-create-the-customers-table"></a>Per creare la tabella Customers  
  
1.  Espandere la connessione dati creata nella **Esplora Server**, quindi espandere il **tabelle** nodo.  
  
2.  Trascinare il **clienti** tabella dal **Esplora Server** nel **Progettazione Dataset**.  
  
     Oggetto **clienti** tabella dei dati e **CustomersTableAdapter** vengono aggiunti al set di dati.  
  
#### <a name="to-create-the-orders-table"></a>Per creare la tabella Orders  
  
-   Trascinare il **ordini** tabella dal **Esplora Server** nel **Progettazione Dataset**.  
  
     Un' **ordini** tabella di dati **OrdersTableAdapter**e relazione dati tra il **clienti** e **ordini** tabelle vengono aggiunte al set di dati.  
  
#### <a name="to-create-the-orderdetails-table"></a>Per creare la tabella OrderDetails  
  
-   Trascinare il **Order Details** tabella dal **Esplora Server** nel **Progettazione Dataset**.  
  
     Un' **Order Details** tabella di dati **oggetto Order DetailsTableAdapter**e una relazione dati tra il **ordini** e **Order Details** tabelle vengono aggiunti al set di dati.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
### <a name="to-add-functionality-to-your-application"></a>Per aggiungere funzionalità all'applicazione  
  
-   Salvare il set di dati.  
  
-   Selezionare gli elementi di **Zdroje dat** finestra e trascinarli in un form. Per altre informazioni, vedere [controlli di associare Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).  
  
-   Aggiungere più query per gli oggetti TableAdapter. Per altre informazioni, vedere [procedura: creare query TableAdapter](../data-tools/how-to-create-tableadapter-queries.md).  
  
-   Aggiungere la logica di convalida per il <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> eventi delle tabelle di dati nel set di dati. Per altre informazioni, vedere [convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio di dati](../data-tools/saving-data.md)