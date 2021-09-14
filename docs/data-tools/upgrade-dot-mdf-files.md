---
title: Aggiornare i file con estensione mdf
description: Esaminare le opzioni per l'aggiornamento di un file di database (con estensione mdf) dopo l'installazione di una versione più recente di Visual Studio.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 8a84ef3c52092feab447dfb26110129f89b1a766
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631091"
---
# <a name="upgrade-mdf-files"></a>Aggiornare i file con estensione mdf

In questo argomento vengono descritte le opzioni per l'aggiornamento di un file di database ( con estensione *mdf*) dopo l'installazione di una versione più recente di Visual Studio. Include le istruzioni per le attività seguenti:

- Aggiornare un file di database per usare una versione più recente di SQL Server Express Local DB

- Aggiornare un file di database per usare una versione più recente di SQL Server Express

- Usare un file di database in Visual Studio ma mantenere la compatibilità con una versione precedente di SQL Server Express o Local DB

- Impostare SQL Server Express motore di database predefinito

È possibile usare Visual Studio per aprire un progetto che contiene un file di database ( con estensione *mdf*) creato usando una versione precedente di SQL Server Express o Local DB. Tuttavia, per continuare a sviluppare il progetto in Visual Studio, è necessario che tale versione di SQL Server Express o Local DB sia installata nello stesso computer di Visual Studio oppure aggiornare il file di database. Se si aggiorna il file di database, non sarà possibile accedervi usando versioni precedenti di SQL Server Express o Local DB.

Potrebbe anche essere richiesto di aggiornare un file di database creato con una versione precedente di SQL Server Express o Local DB se la versione del file non è compatibile con l'istanza di SQL Server Express o Local DB attualmente installata. Per risolvere il problema, Visual Studio verrà richiesto di aggiornare il file.

> [!IMPORTANT]
> È consigliabile eseguire il backup del file di database prima di aggiornarlo.

> [!WARNING]
> Se si aggiorna un file con estensione *mdf* creato in Local DB 2014 (V12) a 32 bit a Local DB 2016 (V13) o versione successiva, non sarà possibile aprire nuovamente il file nella versione a 32 bit di Local DB.

Prima di aggiornare un database, considerare i criteri seguenti:

- Non eseguire l'aggiornamento se si vuole lavorare sul progetto sia in una versione precedente che in una versione più recente di Visual Studio.

- Non eseguire l'aggiornamento se l'applicazione verrà usata in ambienti che usano SQL Server Express anziché Local DB.

- Non eseguire l'aggiornamento se l'applicazione usa connessioni remote, perché Local DB non le accetta.

- Non eseguire l'aggiornamento se l'applicazione si basa su Internet Information Services (IIS).

- È consigliabile eseguire l'aggiornamento se si vogliono testare le applicazioni di database in un ambiente sandbox ma non si vuole amministrare un database.

### <a name="to-upgrade-a-database-file-to-use-the-localdb-version"></a>Per aggiornare un file di database per l'uso della Local DB versione

1. In **Esplora server** selezionare il pulsante Connessione **al database.**

2. Nella finestra **di dialogo** Aggiungi connessione specificare le informazioni seguenti:

    - **Origine dati:**`Microsoft SQL Server (SqlClient)`

    - **Nome server**:

        - Per usare la versione predefinita: `(localdb)\MSSQLLocalDB` .  Verrà specificato ProjectV12 o ProjectV13, a seconda della versione di Visual Studio installata e del momento in cui è stata creata la Local DB istanza. Il **nodo MSSQLLocalDB** in **SQL Server Esplora oggetti** la versione a cui punta.

        - Per usare una versione specifica: o , dove `(localdb)\ProjectsV12` `(localdb)\ProjectsV13` V12 è Local DB 2014 e V13 è Local DB 2016.

    - **Collega un file di database:** percorso fisico del file *MDF* primario.

    - **Nome logico**: il nome che si desidera utilizzare con il file.

3. Selezionare il **pulsante OK.**

4. Quando richiesto, selezionare il pulsante **Sì** per aggiornare il file.

    Il database viene aggiornato, collegato al motore di database Local DB e non è più compatibile con la versione precedente di Local DB.

È anche possibile modificare una connessione SQL Server Express per utilizzare Local DB aprendo il menu di scelta rapida per la connessione e quindi selezionando **Modifica connessione.** Nella finestra **di dialogo** Modifica connessione modificare il nome del server in `(LocalDB)\MSSQLLocalDB` . Nella finestra **di dialogo Proprietà** avanzate verificare che Istanza utente sia impostato su **False**. 

### <a name="to-upgrade-a-database-file-to-use-the-sql-server-express-version"></a>Per aggiornare un file di database per l'uso della SQL Server Express precedente

1. Scegliere Modifica connessione dal menu di scelta rapida per la connessione **al** database.

2. Nella finestra **di dialogo** Modifica connessione selezionare il **pulsante** Avanzate.

3. Nella finestra **di dialogo Proprietà** avanzate selezionare il pulsante **OK** senza modificare il nome del server.

    Il file di database viene aggiornato in modo che corrisponda alla versione corrente di SQL Server Express.

### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Per usare il database in Visual Studio ma mantenere la compatibilità con SQL Server Express

- In Visual Studio aprire il progetto senza aggiornarlo.

  - Per eseguire il progetto, premere **F5.**

  - Per modificare il database, aprire il file con estensione *mdf* in **Esplora soluzioni** ed espandere il nodo **in** Esplora server usare il database.

### <a name="to-make-sql-server-express-the-default-database-engine"></a>Per impostare SQL Server Express motore di database predefinito

1. Nella barra dei menu selezionare **Strumenti** > **Opzioni**.

2. Nella finestra **di** dialogo Opzioni espandere le opzioni **Strumenti di** database e quindi selezionare **Connessioni dati**.

3. Nella casella **SQL Server di** testo Nome istanza specificare il nome dell'istanza di SQL Server Express o Local DB da usare. Se l'istanza non è denominata, specificare `.\SQLEXPRESS or (LocalDB)\MSSQLLocalDB` .

4. Selezionare il **pulsante OK.**

    SQL Server Express sarà il motore di database predefinito per le applicazioni.

## <a name="see-also"></a>Vedi anche

- [Accesso ai dati in Visual Studio](accessing-data-in-visual-studio.md)
