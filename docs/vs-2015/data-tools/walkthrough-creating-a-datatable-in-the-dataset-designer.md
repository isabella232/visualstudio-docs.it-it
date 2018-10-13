---
title: 'Procedura dettagliata: Creazione di una DataTable in Progettazione Dataset. | Microsoft Docs'
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
- DataTable objects, creating
- Dataset Designer, creating data tables
- tables [Visual Studio], creating
- data [Visual Studio], Dataset Designer
ms.assetid: abf0a2b5-e4e5-422e-97ef-55a0e35a82df
caps.latest.revision: 10
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 1f0f31528239794b9c7a3b4a4bf98542ed4bbcf2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49299962"
---
# <a name="walkthrough-creating-a-datatable-in-the-dataset-designer"></a>Procedura dettagliata: creazione di una DataTable in Progettazione DataSet
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come creare un <xref:System.Data.DataTable> (senza un oggetto TableAdapter) usando il **Progettazione Dataset**. Per informazioni sulla creazione di tabelle di dati che includono oggetti TableAdapter, vedere [creare e configurare oggetti TableAdapter](../data-tools/create-and-configure-tableadapters.md).  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di un nuovo progetto applicazione Windows  
  
-   Aggiunta di un nuovo set di dati all'applicazione  
  
-   Aggiunta di una nuova tabella di dati al set di dati  
  
-   Aggiunta di colonne alla tabella dati  
  
-   Impostazione della chiave primaria per la tabella  
  
## <a name="creating-a-new-windows-application"></a>Creazione di una nuova applicazione Windows  
  
#### <a name="to-create-a-new-windows-application-project"></a>Per creare un nuovo progetto Applicazione Windows  
  
1.  Dal **File** menu, creare un nuovo progetto.  
  
2.  Scegliere un linguaggio di programmazione le **tipi di progetto** riquadro.  
  
3.  Fare clic su **applicazione di Windows** nel **modelli** riquadro.  
  
4.  Denominare il progetto `DataTableWalkthrough`, quindi fare clic su **OK**.  
  
     Visual Studio aggiunge il progetto **Esplora soluzioni** unitamente **Form1** nella finestra di progettazione.  
  
## <a name="adding-a-new-dataset-to-the-application"></a>Aggiunta di un nuovo set di dati all'applicazione  
  
#### <a name="to-add-a-new-dataset-item-to-the-project"></a>Per aggiungere un nuovo elemento di set di dati al progetto  
  
1.  Nel menu **Progetto** fare clic su **Aggiungi nuovo elemento**.  
  
     Viene visualizzata la finestra di dialogo Aggiungi nuovo elemento.  
  
2.  Nel **modelli** , quindi selezionare **DataSet**.  
  
3.  Fare clic su **Aggiungi**.  
  
     Visual Studio aggiungerà un file denominato **DataSet1.xsd** al progetto e aprirlo nel **Progettazione Dataset**.  
  
## <a name="adding-a-new-datatable-to-the-dataset"></a>Aggiunta di una DataTable nuova al set di dati  
  
#### <a name="to-add-a-new-data-table-to-the-dataset"></a>Per aggiungere una nuova tabella di dati al set di dati  
  
1.  Trascinare un **DataTable** dal **set di dati** scheda della finestra di **della casella degli strumenti** nel **Progettazione Dataset**.  
  
     Una tabella denominata **DataTable1** viene aggiunto al set di dati.  
  
    > [!NOTE]
    >  Per creare una tabella di dati che include un oggetto TableAdapter, vedere [procedura dettagliata: creazione di un oggetto TableAdapter con più query](../data-tools/walkthrough-creating-a-tableadapter-with-multiple-queries.md).  
  
2.  Fare clic sulla barra del titolo della **DataTable1** e rinominarlo `Music`.  
  
## <a name="adding-columns-to-the-data-table"></a>Aggiunta di colonne alla tabella dati  
  
#### <a name="to-add-columns-to-the-data-table"></a>Per aggiungere colonne alla tabella dati  
  
1.  Fare doppio clic il **musica** tabella. Puntare **Add**, quindi fare clic su **colonna**.  
  
2.  Assegnare un nome di colonna `SongID`.  
  
3.  Nella finestra **Proprietà** impostare la proprietà <xref:System.Data.DataColumn.DataType%2A> su <xref:System.Int16?displayProperty=fullName>.  
  
4.  Ripetere questo processo e aggiungere le colonne seguenti:  
  
     `SongTitle`: <xref:System.String?displayProperty=fullName>  
  
     `Artist`: <xref:System.String?displayProperty=fullName>  
  
     `Genre`: <xref:System.String?displayProperty=fullName>  
  
## <a name="setting-the-primary-key-for-the-table"></a>Impostazione della chiave primaria per la tabella  
 Tutte le tabelle di dati devono avere una chiave primaria. Una chiave primaria identifica in modo univoco un record specifico in una tabella di dati.  
  
#### <a name="to-set-the-primary-key-of-the-data-table"></a>Per impostare la chiave primaria della tabella dati  
  
-   Fare doppio clic il **SongID** colonna e quindi fare clic su **Imposta chiave primaria**.  
  
     Icona di una chiave viene visualizzata accanto al **SongID** colonna.  
  
## <a name="saving-your-project"></a>Salvare il progetto  
  
#### <a name="to-save-the-datatablewalkthrough-project"></a>Per salvare il progetto DataTableWalkthrough  
  
-   Nel **File** menu, fare clic su **Salva tutto**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Ora che è stata creata la tabella, si potrebbero voler eseguire una delle azioni seguenti:  
  
|A|Vedere|  
|--------|---------|  
|Creare un modulo per i dati di input|[Procedura dettagliata: Visualizzazione dei dati in un Form Windows](../data-tools/walkthrough-displaying-data-on-a-windows-form.md).|  
|Aggiungere dati alla tabella|[Aggiunta di dati a un oggetto DataTable](http://msdn.microsoft.com/library/d6aa8474-7bde-48f7-949d-20dc38a1625b).|  
|Visualizzare i dati in una tabella|[Visualizzazione dei dati in un oggetto DataTable](http://msdn.microsoft.com/library/1d26e0fb-f6e0-4afa-9a9c-b8d55b8f20dc).|  
|Modificare i dati|[Modifiche a DataTable](http://msdn.microsoft.com/library/f08008a9-042e-4de9-94f3-4f0e502b1eb5)|  
|Eliminare una riga da una tabella|[Eliminazione di DataRow](http://msdn.microsoft.com/library/c34f531d-4b9b-4071-b2d7-342c402aa586)|  
  
## <a name="see-also"></a>Vedere anche  
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio dei dati](../data-tools/saving-data.md)   
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)