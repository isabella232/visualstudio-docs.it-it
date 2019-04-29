---
title: Connettersi ai dati in un database di Access (Windows Form)
ms.date: 02/12/2019
ms.topic: conceptual
helpviewer_keywords:
- databases, connecting to
- databases, Access
- data [Visual Studio], connecting
- connecting to data, from Access databases
- Access databases, connecting
ms.assetid: 4159e815-d430-4ad0-a234-e4125fcbef18
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 9d4fcce4664483cd1d981f6a0b1233a6302c553b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62568534"
---
# <a name="connect-to-data-in-an-access-database-windows-forms"></a>Connettersi ai dati in un database di Access (Windows Form)

È possibile connettersi a un database Access (entrambi un *mdf* file o un' *accdb* file) con Visual Studio. Dopo avere definito la connessione, i dati vengono visualizzati nella finestra **Origine dati** da cui è possibile trascinare tabelle o visualizzazioni nei form.

## <a name="prerequisites"></a>Prerequisiti

Per eseguire queste procedure, è necessario un progetto di applicazione Windows Forms e un database Access (file con estensione *accdb*) o un database Access 2000-2003 (file con estensione *mdb*). Attenersi alla procedura che corrisponde al tipo di file utilizzato.

## <a name="create-a-dataset-for-an-accdb-file"></a>Creare un set di dati per un file con estensione accdb

È possibile connettersi a database creati tramite Access 2013, Office 365, Access 2010 o Access 2007 tramite la procedura seguente.

1. Aprire l'applicazione Windows Forms a cui si vuole connettere i dati.

2. Per aprire la **Zdroje dat** finestra via il **View** dal menu **Other Windows** > **Zdroje dat**.

   ![Visualizza, Altre finestre, Origini dati](../data-tools/media/viewdatasources.png)

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

   Viene avviata la **Configurazione guidata origine dati**.

4. Selezionare **Database** nel **scegliere un tipo di origine dati** pagina e quindi selezionare **Next**.

5. Selezionare **set di dati** nel **scegliere un modello di Database** pagina e quindi selezionare **Next**.

6. Nella pagina **Seleziona connessione dati** selezionare **Nuova connessione** per configurare una nuova connessione dati.

   Verrà visualizzata la finestra di dialogo **Aggiungi connessione**.

7. Se **zdroj dat** non è impostata su **File di Database Microsoft Access (OLE DB)**, selezionare il **modifica** pulsante.

   Il **Modifica origine dati** verrà visualizzata la finestra di dialogo. Nell'elenco delle origini dati, scegliere **File di Database Microsoft Access**. Nel **provider di dati** elenco a discesa, selezionare **Provider di dati .NET Framework per OLE DB**, quindi scegliere **OK**.

8. Scegliere **esplorare** accanto a **nome file del Database**e quindi passare al *accdb* file e scegliere **Open**.

9. Immettere un nome utente e password (se necessario) e quindi scegliere **OK**.

10. Selezionare **successivo** nel **scegliere la connessione dati** pagina.

     È possibile ricevere una finestra di dialogo indicante che il file di dati non è presente nel progetto corrente. Selezionare **Sì** o **No**.

11. Selezionare **successivo** nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina.

12. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.

13. Selezionare le tabelle o viste da includere nel set di dati e quindi selezionare **fine**.

     Il dataset viene aggiunto al progetto e le tabelle e le viste vengono visualizzate nella finestra **Origini dati**.

## <a name="create-a-dataset-for-an-mdb-file"></a>Creare un set di dati per un file con estensione mdb

Il set di dati viene creato mediante l'esecuzione della **Configurazione guidata origine dati**.

1. Aprire l'applicazione Windows Forms a cui si vuole connettere i dati.

2. Nel **View** dal menu **Other Windows** > **Zdroje dat**.

   ![Visualizza, Altre finestre, Origini dati](../data-tools/media/viewdatasources.png)

3. Nella finestra **Origini dati** fare clic su **Aggiungi nuova origine dati**.

    Viene avviata la **Configurazione guidata origine dati**.

4. Selezionare **Database** nel **scegliere un tipo di origine dati** pagina e quindi selezionare **Next**.

5. Selezionare **set di dati** nel **scegliere un modello di Database** pagina e quindi selezionare **Next**.

6. Nella pagina **Seleziona connessione dati** selezionare **Nuova connessione** per configurare una nuova connessione dati.

7. Se l'origine dati non è **File di Database Microsoft Access (OLE DB)**, selezionare **Change** per aprire il **Modifica origine dati** nella finestra di dialogo e selezionare **Microsoft Accedere al File di Database**, quindi selezionare **OK**.

8. Nel **nome file del Database**, specificare il percorso e nome del *mdb* file che si desidera connettersi a e quindi selezionare **OK**.

   ![Aggiunta della connessione al file di database di Access](../data-tools/media/add-connection-access-db.png)

9. Selezionare **successivo** nel **scegliere la connessione dati** pagina.

10. Selezionare **successivo** nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina.

11. Espandere il nodo **Tabelle** nella pagina **Seleziona oggetti di database**.

12. Selezionare le tabelle o viste desiderato nel set di dati e quindi selezionare **fine**.

    Il dataset viene aggiunto al progetto e le tabelle e le viste vengono visualizzate nella finestra **Origini dati**.

## <a name="security"></a>Sicurezza

L'archiviazione di informazioni riservate, ad esempio una password, può avere implicazioni sulla sicurezza dell'applicazione. L'autenticazione di Windows, detta anche sicurezza integrata, consente di controllare l'accesso a un database in modo più sicuro. Per altre informazioni, vedere [Protezione delle informazioni di connessione](/dotnet/framework/data/adonet/protecting-connection-information).

## <a name="next-steps"></a>Passaggi successivi

Il set di dati appena creato è ora disponibile nel **Zdroje dat** finestra. A questo punto è possibile eseguire una delle attività seguenti:

- Selezionare gli elementi nel **Zdroje dat** finestra e trascinarli nel form (vedere [controlla Binding Windows Forms ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)).

- Aprire l'origine dati in **Progettazione DataSet** per aggiungere o modificare gli oggetti che costituiscono il set di dati.

- Aggiungere logica di convalida per il <xref:System.Data.DataTable.ColumnChanging> oppure <xref:System.Data.DataTable.RowChanging> evento delle tabelle di dati nel set di dati (vedere [convalidare i dati nei set di dati](../data-tools/validate-data-in-datasets.md)).

## <a name="see-also"></a>Vedere anche

- [Aggiungere connessioni](../data-tools/add-new-connections.md)