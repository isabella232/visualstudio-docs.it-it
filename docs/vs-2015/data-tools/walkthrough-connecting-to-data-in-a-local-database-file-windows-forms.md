---
title: 'Procedura dettagliata: Connessione ai dati in un File di Database locale (Windows Form) | Microsoft Docs'
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
- local data, SQL Express
- SQL Express, walkthroughs
- SQL Express, connecting
- data [Visual Studio], local
- data [Visual Studio], connecting to SQL Express
ms.assetid: 5e16b7da-3fdc-4e69-bdb4-e8e700481811
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 9b2d17c5ed86e37d3c674ef9238702cd8557a90f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47531284"
---
# <a name="walkthrough-connecting-to-data-in-a-local-database-file-windows-forms"></a>Procedura dettagliata: connessione ai dati in un file di database lodale (Windows Form)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile visualizzare i dati in modo semplice e rapido da un file di database locale nell'applicazione creando un dataset e aggiungendo controlli associati a dati all'applicazione. In questa procedura dettagliata, verranno visualizzati i dati dal file di database locale creato seguendo i passaggi descritti in [creare un database SQL usando una finestra di progettazione](../data-tools/create-a-sql-database-by-using-a-designer.md). Dopo aver creato un progetto Windows Form, verrà stabilità la connessione al database e verrà indicato di visualizzare i dati della tabella Customers in una griglia dati del form dell'applicazione.  
  
 Quando si crea un database in Visual Studio 2013, il motore LocalDB di SQL Server Express viene utilizzato per accedere a un file di database (con estensione mdf) in SQL Server 2012. Nelle versioni precedenti di Visual Studio il motore di SQL Server Express viene utilizzato per accedere a un file di database (con estensione mdf). Visualizzare [Cenni preliminari sui dati locali](../data-tools/local-data-overview.md).  
  
 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]  
  
 In questa procedura dettagliata sono incluse le attività seguenti:  
  
-   [Creazione e configurazione di un set di dati](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_CreateDataset)  
  
-   [Aggiunta di controlli con associazione a dati](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md#BKMK_AddCtrls)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario accedere al database SampleDatabase. mdf creato completando [creare un database SQL usando una finestra di progettazione](../data-tools/create-a-sql-database-by-using-a-designer.md).  
  
##  <a name="BKMK_CreateDataset"></a> Creazione e configurazione di un set di dati  
  
#### <a name="to-create-and-configure-a-dataset"></a>Per creare e configurare un dataset  
  
1.  Creare un progetto Windows Forms e denominarlo **ConnectLocalData**.  
  
     Visualizzare [le applicazioni Client](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
2.  Se il **Zdroje dat** finestra non è visualizzato, premere i tasti Maiusc-Alt-D oppure sulla barra dei menu, scegliere **View**, **Other Windows**, **Mostra origini dati**.  
  
3.  Nel **Zdroje dat** finestra, scegliere il **Aggiungi nuova origine dati** collegamento.  
  
     Nel **configurazione guidata origine dati**, scegliere il **successivo** due volte per accettare le impostazioni predefinite.  
  
4.  Nel **Seleziona connessione dati** pagina, scegliere il **nuova connessione** pulsante.  
  
     Il **Scegli origine dati** verrà visualizzata la finestra di dialogo.  
  
5.  Nel **zdroj dat** elenco, scegliere **File di Database di Microsoft SQL Server**e quindi scegliere il **continua** pulsante.  
  
     Il **Aggiungi connessione** verrà visualizzata la finestra di dialogo.  
  
6.  Nel **nome file del Database** , specificare il file creato completando [creare un database SQL usando una finestra di progettazione](../data-tools/create-a-sql-database-by-using-a-designer.md), oppure scegliere il **Sfoglia** e individuare il tale file.  
  
     Per impostazione predefinita, il file è degli utenti\\*AccountUtente*\Documents\Visual Studio *versione*\projects\sampledatabasewalkthrough\sampledatabasewalkthrough.  
  
7.  Sotto **accedere al server**, accettare i valori predefiniti, scegliere il **OK** pulsante e quindi scegliere il **Avanti** pulsante.  
  
    > [!NOTE]
    >  Quando si creano connessioni a un file di database locale, è possibile scegliere di creare una copia del database nel progetto o di eseguire la connessione al file di database esistente nella posizione attuale. Visualizzare [procedura: gestire file di dati locali nel progetto](../data-tools/how-to-manage-local-data-files-in-your-project.md).  
  
8.  Nella finestra di dialogo visualizzata, scegliere **Sì** per copiare il file di database nel progetto.  
  
9. Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, scegliere il **successivo** pulsante.  
  
10. Nel **Scegli oggetti di Database** , espandere il **tabelle** nodo, seleziona il **clienti** e **ordini** caselle di controllo e quindi Scegliere il **fine** pulsante.  
  
     Il **SampleDatabaseDataSet** viene aggiunto al progetto e il **clienti** e **ordini** le tabelle vengono visualizzate nel **Zdroje dat** finestra.  
  
##  <a name="BKMK_AddCtrls"></a> Aggiunta di controlli con associazione a dati  
  
#### <a name="to-add-data-bound-controls"></a>Per aggiungere controlli con associazione a dati  
  
1.  Sposta l'oggetto principale **clienti** nodo dal **Zdroje dat** finestra nei **Form1**.  
  
     Sul form vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [SampleDatabaseDataSet](../data-tools/dataset-tools-in-visual-studio.md), [CustomersTableAdapter](../data-tools/tableadapter-overview.md), <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.  
  
2.  Per eseguire l'applicazione e visualizzare i dati aggiunti nella procedura dettagliata precedente, premere F5.  
  
3.  Scegliere l'icona di aggiunta gialla (![pulsante Aggiungi nella finestra di Windows Form](../data-tools/media/addrecord.png "AddRecord")), aggiungere un record del cliente e quindi salvare le modifiche scegliendo l'icona del disco (![pulsante Salva in Windows Form](../data-tools/media/saveinwf.png "SaveInWF")).  
  
4.  Eliminare il record appena creato per eliminarlo, quindi scegliere l'icona di eliminazione rossa (![pulsante Elimina in Windows Form](../data-tools/media/deleterecord.png "DeleteRecord")).  
  
## <a name="next-steps"></a>Passaggi successivi  
 È possibile creare o modificare oggetti nel set di dati se si apre l'origine dati nel [creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md). È possibile inoltre aggiungere logica di convalida agli eventi <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> delle tabelle dati presenti nel dataset. Visualizzare [convalida dei dati nei set di dati](../data-tools/validate-data-in-datasets.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dei dati locali](../data-tools/local-data-overview.md)   
 [Procedura: gestire file di dati locali nel progetto](../data-tools/how-to-manage-local-data-files-in-your-project.md)   
 [Associazione di controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparare l'applicazione per ricevere dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica dei dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Salvataggio di dati](../data-tools/saving-data.md)