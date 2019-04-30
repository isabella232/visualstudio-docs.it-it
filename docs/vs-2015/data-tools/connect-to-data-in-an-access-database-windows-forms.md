---
title: Connettersi ai dati in un database di Access (Windows Form) | Microsoft Docs
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
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
caps.latest.revision: 32
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a6909bade36dce15bfae725fbaab60f24236451
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436986"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Connettersi ai dati in un database di Access (Windows Form)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile connettersi a un database di Access (un file con estensione mdf o un file con estensione accdb) tramite Visual Studio. Dopo avere definito la connessione, i dati vengono visualizzati nella finestra **Origine dati** da cui è possibile trascinare tabelle o visualizzazioni nei form.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per usare queste procedure, è necessario un progetto di applicazione Windows Form e un database di Access (file con estensione accdb) o un database di Access 2000, 2003 (file con estensione mdb). Attenersi alla procedura che corrisponde al tipo di file utilizzato.  
  
## <a name="creating-the-dataset-for-an-accdb-file"></a>Creazione del set di dati per un file con estensione accdb  
 È possibile connettersi a database creati tramite Access 2013, Office 365, Access 2010 o Access 2007 tramite la procedura seguente.  
  
#### <a name="to-create-the-dataset"></a>Per creare il dataset  
  
1. Aprire l'applicazione Windows Forms a cui si vuole connettere i dati.  
  
2. Nel **View** dal menu **Other Windows** > **Zdroje dat**.  
  
     ![Visualizzare altre origini dati di Windows](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.  
  
     ![Aggiungi nuova origine dati](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")  
  
4. Selezionare **Database** nel **scegliere un tipo di origine dati** pagina e quindi selezionare **Next**.  
  
5. Selezionare **set di dati** nel **scegliere un modello di Database** pagina e quindi selezionare **Next**.  
  
6. Nella pagina **Seleziona connessione dati** selezionare **Nuova connessione** per configurare una nuova connessione dati.  
  
7. Modifica il **zdroj dat** al **Provider di dati .NET Framework per OLE DB**.  
  
     ![Modificare il Provider di dati in OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")  
  
    > [!IMPORTANT]
    > Anche se un'origine dati di **File di Database Microsoft Access (OLE DB)** può sembrare la scelta corretta, è usare quel tipo di origine dati solo per i file di database con estensione mdb.  
  
8. Nelle **Provider OLE DB**, selezionare **Office 12.0 Access Database Engine Provider Microsoft OLE DB**.  
  
     ![OLE DB Provider Microsoft Office 12.0 Access](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")  
  
9. Nelle **Server o nel nome file**, specificare il percorso e nome del file con estensione accdb a cui si desidera connettersi e quindi selezionare **OK**.  
  
    > [!NOTE]
    > Se il file di database ha un nome utente e password, specificarli e si seleziona **OK**.  
  
10. Selezionare **successivo** nel **scegliere la connessione dati** pagina.  
  
11. Selezionare **successivo** nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina.  
  
12. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.  
  
13. Selezionare le tabelle o viste desiderato nel set di dati e quindi selezionare **fine**.  
  
     Il dataset viene aggiunto al progetto e le tabelle e le viste vengono visualizzate nella finestra **Origini dati**.  
  
## <a name="creating-the-dataset-for-an-mdb-file"></a>Creazione di set di dati per un file con estensione mdb  
 Il set di dati viene creato mediante l'esecuzione della **Configurazione guidata origine dati**.  
  
#### <a name="to-create-the-dataset"></a>Per creare il dataset  
  
1. Aprire l'applicazione Windows Forms a cui si vuole connettere i dati.  
  
2. Nel **View** dal menu **Other Windows** > **Zdroje dat**.  
  
     ![Visualizzare altre origini dati di Windows](../data-tools/media/viewdatasources.png "ViewDataSources")  
  
3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.  
  
4. Selezionare **Database** nel **scegliere un tipo di origine dati** pagina e quindi selezionare **Next**.  
  
5. Selezionare **set di dati** nel **scegliere un modello di Database** pagina e quindi selezionare **Next**.  
  
6. Nella pagina **Seleziona connessione dati** selezionare **Nuova connessione** per configurare una nuova connessione dati.  
  
7. Se l'origine dati non è **File di Database Microsoft Access (OLE DB)**, selezionare **Change** per aprire il **Modifica origine dati** nella finestra di dialogo e selezionare **Microsoft Accedere al File di Database**, quindi selezionare **OK**.  
  
8. Nel **nome file del Database**, specificare il percorso e nome del file con estensione mdb a cui si desidera connettersi e quindi selezionare **OK**.  
  
     ![Aggiungi connessione File di Database di Access](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")  
  
9. Selezionare **successivo** nel **scegliere la connessione dati** pagina.  
  
10. Selezionare **successivo** nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina.  
  
11. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.  
  
12. Selezionare le tabelle o viste desiderato nel set di dati e quindi selezionare **fine**.  
  
     Il dataset viene aggiunto al progetto e le tabelle e le viste vengono visualizzate nella finestra **Origini dati**.  
  
## <a name="security"></a>Sicurezza  
 L'archiviazione di informazioni riservate, ad esempio una password, può avere implicazioni sulla sicurezza dell'applicazione. L'autenticazione di Windows, detta anche sicurezza integrata, consente di controllare l'accesso a un database in modo più sicuro. Per altre informazioni, vedere [Protezione delle informazioni di connessione](http://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).  
  
## <a name="next-steps"></a>Passaggi successivi  
 Il set di dati appena creato è ora disponibile nel **Zdroje dat** finestra. A questo punto è possibile eseguire una delle attività seguenti:  
  
- Selezionare gli elementi nel **Zdroje dat** finestra e trascinarli nel form (vedere [controlla Binding Windows Forms ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).  
  
- Aprire l'origine dati nella finestra di progettazione set di dati per aggiungere o modificare gli oggetti che costituiscono il set di dati.  
  
- Aggiungere logica di convalida per il <xref:System.Data.DataTable.ColumnChanging> oppure <xref:System.Data.DataTable.RowChanging> evento delle tabelle di dati nel set di dati (vedere [convalidare i dati nei set di dati](../data-tools/validate-data-in-datasets.md)).  
  
## <a name="see-also"></a>Vedere anche

 [Preparazione dell'applicazione al ricevimento di dati](http://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [La convalida dei dati](http://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e)   
 [Procedure dettagliate di data](http://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)