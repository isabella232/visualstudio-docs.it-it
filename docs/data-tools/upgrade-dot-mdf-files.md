---
title: Aggiornare i file con estensione mdf
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: d35611dcc7b6067cf6d6166aff521ef291b8dfcd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85281123"
---
# <a name="upgrade-mdf-files"></a>Aggiornare i file con estensione mdf

In questo argomento vengono descritte le opzioni per l'aggiornamento di un file di database (con*estensione MDF*) dopo l'installazione di una versione più recente di Visual Studio. Sono incluse le istruzioni per le attività seguenti:

- Aggiornare un file di database per utilizzare una versione più recente di SQL Server Express database locale

- Aggiornare un file di database per usare una versione più recente di SQL Server Express

- Usare un file di database in Visual Studio, ma mantenere la compatibilità con una versione precedente di SQL Server Express o del database locale

- Imposta come SQL Server Express il motore di database predefinito

È possibile utilizzare Visual Studio per aprire un progetto che contiene un file di database (con*estensione MDF*) creato utilizzando una versione precedente di SQL Server Express o del database locale. Tuttavia, per continuare a sviluppare il progetto in Visual Studio, è necessario che la versione di SQL Server Express o del database locale sia installata nello stesso computer di Visual Studio oppure è necessario aggiornare il file di database. Se si aggiorna il file di database, non sarà possibile accedervi utilizzando versioni precedenti di SQL Server Express o del database locale.

È inoltre possibile che venga richiesto di aggiornare un file di database creato con una versione precedente di SQL Server Express o database locale se la versione del file non è compatibile con l'istanza di SQL Server Express o database locale attualmente installato. Per risolvere il problema, in Visual Studio verrà richiesto di aggiornare il file.

> [!IMPORTANT]
> È consigliabile eseguire il backup del file di database prima di aggiornarlo.

> [!WARNING]
> Se si aggiorna un file con *estensione MDF* creato nel database locale 2014 (V12) 32 bit al database locale 2016 (V13) o versione successiva, non sarà possibile aprire nuovamente il file nella versione a 32 bit del database locale.

Prima di aggiornare un database, considerare i criteri seguenti:

- Non eseguire l'aggiornamento se si desidera lavorare sul progetto in una versione precedente e in una versione più recente di Visual Studio.

- Non eseguire l'aggiornamento se l'applicazione verrà utilizzata in ambienti che utilizzano SQL Server Express anziché il database locale.

- Non eseguire l'aggiornamento se l'applicazione usa connessioni remote, perché il database locale non le accetta.

- Non eseguire l'aggiornamento se l'applicazione si basa su Internet Information Services (IIS).

- Si consiglia di eseguire l'aggiornamento se si desidera testare le applicazioni di database in un ambiente sandbox ma non si desidera amministrare un database.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Per aggiornare un file di database per l'utilizzo della versione del database locale

1. In **Esplora server**selezionare il pulsante **Connetti al database** .

2. Nella finestra di dialogo **Aggiungi connessione** specificare le informazioni seguenti:

    - **Origine dati**: `Microsoft SQL Server (SqlClient)`

    - **Nome server**:

        - Per utilizzare la versione predefinita: `(localdb)\MSSQLLocalDB` .  In questo modo verrà specificato ProjectV12 o ProjectV13, a seconda della versione di Visual Studio installata e del momento in cui è stata creata la prima istanza del database locale. Il nodo **MSSQLLocalDB** in **Esplora oggetti di SQL Server** Mostra la versione a cui punta.

        - Per usare una versione specifica: `(localdb)\ProjectsV12` o `(localdb)\ProjectsV13` , dove V12 è il database locale 2014 e V13 è il database locale 2016.

    - **Alleghi un file di database**: il percorso fisico del file con *estensione MDF* primario.

    - **Nome logico**: il nome che si desidera utilizzare con il file.

3. Selezionare il pulsante **OK** .

4. Quando viene richiesto, selezionare il pulsante **Sì** per aggiornare il file.

    Il database viene aggiornato, viene collegato al motore di database del database locale e non è più compatibile con la versione precedente del database locale.

È inoltre possibile modificare una connessione SQL Server Express per utilizzare il database locale aprendo il menu di scelta rapida per la connessione e quindi selezionando **Modifica connessione**. Nella finestra di dialogo **Modifica connessione** modificare il nome del server in `(LocalDB)\MSSQLLocalDB` . Nella finestra di dialogo **proprietà avanzate** verificare che l' **istanza utente** sia impostata su **false**.

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Per aggiornare un file di database per l'utilizzo della versione SQL Server Express

1. Nel menu di scelta rapida per la connessione al database selezionare **Modifica connessione**.

2. Nella finestra di dialogo **Modifica connessione** selezionare il pulsante **Avanzate** .

3. Nella finestra di dialogo **proprietà avanzate** selezionare il pulsante **OK** senza modificare il nome del server.

    Il file di database viene aggiornato in modo che corrisponda alla versione corrente di SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Per lavorare con il database in Visual Studio, ma mantenere la compatibilità con SQL Server Express

- In Visual Studio aprire il progetto senza aggiornarlo.

  - Per eseguire il progetto, premere il tasto **F5** .

  - Per modificare il database, aprire il file con *estensione MDF* in **Esplora soluzioni**ed espandere il nodo in **Esplora server** per lavorare con il database.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Per rendere SQL Server Express il motore di database predefinito

1. Nella barra dei menu selezionare **Strumenti** > **Opzioni**.

2. Nella finestra di dialogo **Opzioni** espandere le opzioni **strumenti di database** , quindi selezionare **connessioni dati**.

3. Nella casella di testo **nome istanza SQL Server** specificare il nome dell'istanza di SQL Server Express o del database locale che si desidera utilizzare. Se l'istanza non è denominata, specificare `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB` .

4. Selezionare il pulsante **OK** .

    SQL Server Express sarà il motore di database predefinito per le applicazioni.

## <a name="see-also"></a>Vedere anche

- [Accesso ai dati in Visual Studio](accessing-data-in-visual-studio.md)
