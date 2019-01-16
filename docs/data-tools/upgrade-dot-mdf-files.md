---
title: Aggiornare i file con estensione mdf
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 4e42058d2728d806551ae319112052e664950dab
ms.sourcegitcommit: 5a65ca6688a2ebb36564657d2d73c4b4f2d15c34
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "53863420"
---
# <a name="upgrade-mdf-files"></a>Aggiornare i file con estensione mdf

In questo argomento vengono descritte le opzioni per l'aggiornamento di un file di database (*mdf*) dopo aver installato una versione più recente di Visual Studio. Sono incluse istruzioni per le attività seguenti:

- Eseguire l'aggiornamento di un file di database per usare una versione più recente di SQL Server Express LocalDB

- Eseguire l'aggiornamento di un file di database per usare una versione più recente di SQL Server Express

- Usare un file di database in Visual Studio, ma conservare la compatibilità con una versione precedente di SQL Server Express o LocalDB

- Assicurarsi di SQL Server Express il motore di database predefinito

È possibile usare Visual Studio per aprire un progetto che contiene un file di database (*mdf*) che è stato creato utilizzando una versione precedente di SQL Server Express o LocalDB. Tuttavia, per continuare a sviluppare il progetto in Visual Studio, è necessario tale versione di SQL Server Express o LocalDB installata nello stesso computer di Visual Studio, oppure è necessario aggiornare il file di database. Se si aggiorna il file di database, sarà possibile accedervi con le versioni precedenti di SQL Server Express o LocalDB.

Può anche chiesto di aggiornare un file di database che sia stato creato con una versione precedente di SQL Server Express o LocalDB se la versione del file non è compatibile con l'istanza di SQL Server Express o LocalDB attualmente installato. Per risolvere il problema, Visual Studio verrà richiesto di aggiornare il file.

> [!IMPORTANT]
> È consigliabile eseguire il backup del file di database prima di aggiornarlo.

> [!WARNING]
> Se si aggiorna un' *mdf* file che è stato creato in LocalDB 2014 (V12) a 32 bit a LocalDB 2016 (V13) o versioni successive, non sarà in grado di aprire il file nuovo nella versione a 32 bit di LocalDB.

Prima di aggiornare un database, considerare i criteri seguenti:

-   Non eseguire l'aggiornamento se si desidera lavorare sul progetto in una versione precedente sia una versione più recente di Visual Studio.

-   Non eseguire l'aggiornamento se l'applicazione verrà utilizzato in ambienti che usano SQL Server Express anziché LocalDB.

-   Non eseguire l'aggiornamento se l'applicazione usa le connessioni remote, perché non accettarle LocalDB.

-   Non aggiornare l'applicazione si basa su Internet Information Services (IIS).

-   Se si desidera testare le applicazioni di database in un ambiente sandbox, ma non si desidera amministrare un database, prendere in considerazione l'aggiornamento.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Per eseguire l'aggiornamento di un file di database per usare la versione di Local DB

1.  Nelle **Esplora Server**, selezionare la **Connetti al Database** pulsante.

2.  Nel **Aggiungi connessione** finestra di dialogo, specificare le informazioni seguenti:

    -   **Origine dati**: `Microsoft SQL Server (SqlClient)`

    -   **Nome server**:

        -   Usare la versione predefinita: `(localdb)\MSSQLLocalDB`.  Si specificherà ProjectV12 o ProjectV13, a seconda di quale versione di Visual Studio viene installata e quando è stata creata la prima istanza di Local DB. Il **MSSQLLocalDB** nodo **Esplora oggetti di SQL Server** mostra quale versione fa riferimento a.

        -   Per usare una versione specifica: `(localdb)\ProjectsV12` o `(localdb)\ProjectsV13`, dove V12 è LocalDB 2014 e V13 è LocalDB 2016.

    -   **Collegare un file di database**: Il percorso fisico del database primario *mdf* file.

    -   Nome &logico: Il nome che si desidera utilizzare con il file.

3.  Selezionare il pulsante **OK** .

4.  Quando richiesto, selezionare la **Sì** pulsante per aggiornare il file.

    Il database viene aggiornato, è collegato al motore di database LocalDB e non è più compatibile con la versione precedente del database locale.

È inoltre possibile modificare una connessione di SQL Server Express per usare LocalDB, aprire il menu di scelta rapida per la connessione e quindi selezionando **Modifica connessione**. Nel **Modifica connessione** finestra di dialogo, modificare il nome del server a `(LocalDB)\MSSQLLocalDB`. Nel **delle proprietà avanzate** finestra di dialogo, assicurarsi che **User Instance** è impostata su **False**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Per eseguire l'aggiornamento di un file di database per usare la versione di SQL Server Express

1.  Menu di scelta rapida per la connessione al database, selezionare **Modifica connessione**.

2.  Nel **Modifica connessione** finestra di dialogo, seleziona la **avanzate** pulsante.

3.  Nel **delle proprietà avanzate** finestra di dialogo, seleziona la **OK** pulsante senza modificare il nome del server.

    Il file di database in modo da corrispondere alla versione corrente di SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Per funzionare con il database in Visual Studio, mantenendo la compatibilità con SQL Server Express

-   In Visual Studio, aprire il progetto senza l'aggiornamento.

    -   Per eseguire il progetto, selezionare la **F5** chiave.

    -   Per modificare il database, aprire il *mdf* del file in **Esplora soluzioni**, espandere il nodo in **Esplora Server** per lavorare con il database.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Per rendere SQL Server Express il motore di database predefinito

1.  Nella barra dei menu, selezionare **degli strumenti** > **opzioni**.

2.  Nel **opzioni** finestra di dialogo espandere il **strumenti di Database** opzioni e quindi selezionare **connessioni dati**.

3.  Nel **nome dell'istanza di SQL Server** testo, specificare il nome dell'istanza di SQL Server Express o LocalDB che si desidera utilizzare. Se l'istanza non è denominato, specificare `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB`.

4.  Selezionare il pulsante **OK** .

    SQL Server Express è il motore di database predefinito per le applicazioni.

## <a name="see-also"></a>Vedere anche

- [Accesso ai dati in Visual Studio](accessing-data-in-visual-studio.md)