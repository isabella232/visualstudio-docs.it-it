---
title: Aggiornare i file con estensione mdf | Microsoft Docs
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
- SQL Server Express
- SQL Server LocalDB
- LocalDB
- SQLEXPRESS
- upgrading SQLExpress to SQLExpress
- upgrading to LocalDB
ms.assetid: 14ca6f76-f80e-4926-8020-3fee2d802b75
caps.latest.revision: 36
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 773f88e34c111b44f92080c3117eb7e2e42dd70c
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527647"
---
# <a name="upgrade-mdf-files"></a>Aggiornare i file con estensione mdf
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [aggiornare i file con estensione mdf](https://docs.microsoft.com/visualstudio/data-tools/upgrade-dot-mdf-files).  
  
  
In questo argomento descrive le opzioni per l'aggiornamento del file di database (mdf) dopo aver installato una versione più recente di Visual Studio. Sono incluse istruzioni per le attività seguenti:  
  
-   Eseguire l'aggiornamento di un file di database per usare una versione più recente di SQL Server Express LocalDB  
  
-   Eseguire l'aggiornamento di un file di database per usare una versione più recente di SQL Server Express  
  
-   Usare un file di database in Visual Studio, ma conservare la compatibilità con una versione precedente di SQL Server Express o LocalDB  
  
-   Assicurarsi di SQL Server Express il motore di database predefinito  
  
 È possibile usare Visual Studio per aprire un progetto che contiene un file di database (mdf) che è stato creato utilizzando una versione precedente di SQL Server Express o LocalDB. Tuttavia, per continuare a sviluppare il progetto in Visual Studio, è necessario tale versione di SQL Server Express o LocalDB installata nello stesso computer di Visual Studio, oppure è necessario aggiornare il file di database. Se si aggiorna il file di database, sarà possibile accedervi con le versioni precedenti di SQL Server Express o LocalDB.  
  
 Può anche chiesto di aggiornare un file di database che sia stato creato con una versione precedente di SQL Server Express o LocalDB se la versione del file non è compatibile con l'istanza di SQL Server Express o LocalDB attualmente installato. Per risolvere il problema, Visual Studio verrà richiesto di aggiornare il file.  
  
> [!IMPORTANT]
>  È consigliabile eseguire il backup del file di database prima di aggiornarlo.  
  
> [!WARNING]
>  Se si aggiorna un file con estensione mdf che è stato creato in LocalDB 2014 (V12) a 32 bit a LocalDB 2016 (V13), non sarà in grado di aprire il file nuovo nella versione a 32 bit di LocalDB.  In Update 2, LocalDB V13 è solo a 64 bit.  
  
 Prima di aggiornare un database, considerare i criteri seguenti:  
  
-   Non eseguire l'aggiornamento se si desidera lavorare sul progetto in una versione precedente sia una versione più recente di Visual Studio.  
  
-   Non eseguire l'aggiornamento se l'applicazione verrà utilizzato in ambienti che usano SQL Server Express anziché LocalDB.  
  
-   Non eseguire l'aggiornamento se l'applicazione usa le connessioni remote, perché non accettarle LocalDB.  
  
-   Non aggiornare l'applicazione si basa su Internet Information Services (IIS).  
  
-   Se si desidera testare le applicazioni di database in un ambiente sandbox, ma non si desidera amministrare un database, prendere in considerazione l'aggiornamento.  
  
### <a name="to-upgrade-a-database-file"></a>Per eseguire l'aggiornamento di un file di database  
  
1.  Nelle **Esplora Server**, selezionare la **Connetti al Database** pulsante.  
  
2.  Nel **Aggiungi connessione** finestra di dialogo, specificare le informazioni seguenti:  
  
    -   **Zdroj dat**: `Microsoft SQL Server (SqlClient)`  
  
    -   **Nome del server**:  
  
        -   Usare la versione predefinita: `(localdb)\MSSQLLocalDB`.  Si specificherà ProjectV12 o ProjectV13, a seconda di quale versione di Visual Studio viene installata e quando è stata creata la prima istanza di Local DB. Il **MSSQLLocalDB** nodo **Esplora oggetti di SQL Server** mostra quale versione fa riferimento a.  
  
        -   Per usare una versione specifica: `(localdb)\ProjectsV12` o `(localdb)\ProjectsV13`, dove V12 è LocalDB 2014 e V13 è LocalDB 2016.  
  
    -   **Collegare un file di database**: il percorso fisico del file mdf primario.  
  
    -   **Nome logico**: il nome che si desidera utilizzare con il file.  
  
3.  Selezionare il pulsante **OK** .  
  
4.  Quando richiesto, selezionare la **Sì** pulsante per aggiornare il file.  
  
 Il database viene aggiornato, è collegato al motore di database LocalDB e non è più compatibile con la versione precedente del database locale.  
  
 È inoltre possibile modificare una connessione di SQL Server Express per usare LocalDB, aprire il menu di scelta rapida per la connessione e quindi selezionando **Modifica connessione**. Nel **Modifica connessione** finestra di dialogo, modificare il nome del server a `(LocalDB)\MSSQLLocalDB`. Nel **delle proprietà avanzate** finestra di dialogo, assicurarsi che **User Instance** è impostata su **False**.  
  
### <a name="to-upgrade-to-a-newer-version-of-sql-server-express"></a>Eseguire l'aggiornamento a una versione più recente di SQL Server Express  
  
1.  Menu di scelta rapida per la connessione al database, selezionare **Modifica connessione**.  
  
2.  Nel **Modifica connessione** finestra di dialogo, seleziona la **avanzate** pulsante.  
  
3.  Nel **delle proprietà avanzate** finestra di dialogo, seleziona la **OK** pulsante senza modificare il nome del server.  
  
 Il file di database in modo da corrispondere alla versione corrente di SQL Server Express.  
  
### <a name="to-work-with-the-database-in-visual-studio-but-retain-compatibility-with-sql-server-express"></a>Per funzionare con il database in Visual Studio, mantenendo la compatibilità con SQL Server Express  
  
-   In Visual Studio, aprire il progetto senza l'aggiornamento.  
  
    -   Per eseguire il progetto, selezionare il tasto F5.  
  
    -   Per modificare il database, aprire il file con estensione mdf in **Esplora soluzioni**, espandere il nodo nel **Esplora Server** per lavorare con il database.  
  
### <a name="to-make-sql-server-express-the-default-database-engine"></a>Per rendere SQL Server Express il motore di database predefinito  
  
1.  Nella barra dei menu, selezionare **degli strumenti** > **opzioni**.  
  
2.  Nel **opzioni** finestra di dialogo espandere il **Data Tools** opzioni e quindi selezionare il **connessioni dati** nodo.  
  
3.  Nel **nome dell'istanza di SQL Server** testo, specificare il nome dell'istanza di SQL Server Express o LocalDB che si desidera utilizzare. Se l'istanza non è denominato, specificare `.\SQLEXPRESS or (localdb)\MSSQLLocalDB`.  
  
4.  Selezionare il pulsante **OK** .  
  
 SQL Server Express è il motore di database predefinito per le applicazioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica dei dati locali](../data-tools/local-data-overview.md)   
 [Procedura dettagliata: connessione ai dati in un file di database lodale (Windows Form)](../data-tools/walkthrough-connecting-to-data-in-a-local-database-file-windows-forms.md)
