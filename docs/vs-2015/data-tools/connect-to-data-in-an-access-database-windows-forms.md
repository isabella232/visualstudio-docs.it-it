---
title: Connettersi ai dati in un database di Access (Windows Forms) | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 8426e9fcaa29bef36b6701c78d622f6f42fd1171
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651137"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Connettersi ai dati in un database di Access (Windows Form)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile connettersi a un database di Access, ovvero un file con estensione MDF o accdb, usando Visual Studio. Dopo avere definito la connessione, i dati vengono visualizzati nella finestra **Origine dati** da cui è possibile trascinare tabelle o visualizzazioni nei form.

## <a name="prerequisites"></a>Prerequisites
 Per utilizzare queste procedure, è necessario disporre di un progetto Windows Forms Application e di un database di Access (file con estensione accdb) o di un database di Access 2000-2003 (file con estensione mdb). Attenersi alla procedura che corrisponde al tipo di file utilizzato.

## <a name="creating-the-dataset-for-an-accdb-file"></a>Creazione del set di dati per un file con estensione accdb
 È possibile connettersi ai database creati tramite Access 2013, Office 365, Access 2010 o Access 2007 utilizzando la procedura riportata di seguito.

#### <a name="to-create-the-dataset"></a>Per creare il dataset

1. Aprire l'applicazione Windows Forms a cui si vuole connettere i dati.

2. Scegliere **altre finestre**  > **origini dati**dal menu **Visualizza** .

     ![Visualizza altre origini dati di Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

     ![Aggiungi nuova origine dati](../data-tools/media/dataaddnewdatasource.png "dataAddNewDataSource")

4. Selezionare **database** nella pagina **scegliere un tipo di origine dati** e quindi fare clic su **Avanti**.

5. Selezionare **DataSet** nella pagina **scegliere un modello di database** e quindi fare clic su **Avanti**.

6. Nella pagina **Seleziona connessione dati** selezionare **Nuova connessione** per configurare una nuova connessione dati.

7. Modificare l' **origine dati** in **.NET Framework provider di dati per OLE DB**.

     ![Modificare provider di dati in OLE DB](../data-tools/media/datachangedatasourceoledb.png "dataChangeDataSourceOLEDB")

    > [!IMPORTANT]
    > Sebbene un'origine dati del **file di database di Microsoft Access (OLE DB)** possa sembrare la scelta corretta, è possibile utilizzare tale tipo di origine dati solo per i file di database con estensione mdb.

8. In **OLE DB provider**selezionare **Microsoft Office 12,0 Access motore di database provider OLE DB**.

     ![Provider di OLE DB Microsoft Office l'accesso 12,0](../data-tools/media/dataoledbprovideroffice12access.png "dataOLEDBProviderOffice12Access")

9. In **nome server o file**specificare il percorso e il nome del file con estensione accdb a cui si desidera connettersi, quindi selezionare **OK**.

    > [!NOTE]
    > Se il file di database dispone di un nome utente e di una password, specificarli prima di fare clic su **OK**.

10. Nella pagina **scegliere la connessione dati** selezionare **Avanti** .

11. Selezionare **Avanti** nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** .

12. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.

13. Selezionare le tabelle o le viste desiderate nel set di dati e quindi fare clic su **fine**.

     Il dataset viene aggiunto al progetto e le tabelle e le viste vengono visualizzate nella finestra **Origini dati**.

## <a name="creating-the-dataset-for-an-mdb-file"></a>Creazione del set di dati per un file con estensione mdb
 Il set di dati viene creato mediante l'esecuzione della **Configurazione guidata origine dati**.

#### <a name="to-create-the-dataset"></a>Per creare il dataset

1. Aprire l'applicazione Windows Forms a cui si vuole connettere i dati.

2. Scegliere **altre finestre**  > **origini dati**dal menu **Visualizza** .

     ![Visualizza altre origini dati di Windows](../data-tools/media/viewdatasources.png "ViewDataSources")

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

4. Selezionare **database** nella pagina **scegliere un tipo di origine dati** e quindi fare clic su **Avanti**.

5. Selezionare **DataSet** nella pagina **scegliere un modello di database** e quindi fare clic su **Avanti**.

6. Nella pagina **Seleziona connessione dati** selezionare **Nuova connessione** per configurare una nuova connessione dati.

7. Se l'origine dati non è **un file di database Microsoft Access (OLE DB)** , selezionare **Cambia** per aprire la finestra di dialogo **Modifica origine dati** e selezionare **file di database Microsoft Access**, quindi scegliere **OK**.

8. Nel **nome del file di database**specificare il percorso e il nome del file con estensione mdb a cui si desidera connettersi, quindi selezionare **OK**.

     ![Aggiungi file di database di accesso alla connessione](../data-tools/media/dataaddconnectionaccessmdb.png "dataAddConnectionAccessMDB")

9. Nella pagina **scegliere la connessione dati** selezionare **Avanti** .

10. Selezionare **Avanti** nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** .

11. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.

12. Selezionare le tabelle o le viste desiderate nel set di dati e quindi fare clic su **fine**.

     Il dataset viene aggiunto al progetto e le tabelle e le viste vengono visualizzate nella finestra **Origini dati**.

## <a name="security"></a>Sicurezza
 L'archiviazione di informazioni riservate, ad esempio una password, può avere implicazioni sulla sicurezza dell'applicazione. L'autenticazione di Windows, detta anche sicurezza integrata, consente di controllare l'accesso a un database in modo più sicuro. Per altre informazioni, vedere [Protezione delle informazioni di connessione](https://msdn.microsoft.com/library/1471f580-bcd4-4046-bdaf-d2541ecda2f4).

## <a name="next-steps"></a>Passaggi successivi
 Il set di dati appena creato è ora disponibile nella finestra **origini dati** . A questo punto è possibile eseguire una delle attività seguenti:

- Selezionare gli elementi nella finestra **origini dati** e trascinarli nel form. vedere [associare Windows Forms controlli ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md).

- Aprire l'origine dati nel Progettazione DataSet per aggiungere o modificare gli oggetti che compongono il set di dati.

- Aggiungere la logica di convalida all'evento <xref:System.Data.DataTable.ColumnChanging> o <xref:System.Data.DataTable.RowChanging> delle tabelle dati nel DataSet. vedere [convalidare i dati nei set](../data-tools/validate-data-in-datasets.md)di dati.

## <a name="see-also"></a>Vedere anche

 [Preparazione dell'applicazione per la ricezione](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad) di [controlli di associazione dati ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md) [convalida](https://msdn.microsoft.com/library/b3a9ee4e-5d4d-4411-9c56-c811f2b4ee7e) dei dati di dati [procedure dettagliate](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4)