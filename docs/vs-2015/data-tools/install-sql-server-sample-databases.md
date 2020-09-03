---
title: Installare SQL Server database di esempio | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3915351bff74f35ceb5fc462cb29dfd2f322fb6a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "74299628"
---
# <a name="install-sql-server-sample-databases"></a>Installare i database di esempio di SQL Server
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

I database di esempio sono utili per sperimentare query SQL e LINQ, associazione dati, Entity Framework modellazione e così via.  Ogni prodotto di database dispone di propri database di esempio. Northwind e AdventureWorks sono due comuni database di esempio SQL Server.

 **AdventureWorks** è il database di esempio corrente fornito per SQL Server Products. È possibile scaricarlo come file con estensione MDF dalla [pagina AdventureWorks su CodePlex](https://archive.codeplex.com/?p=msftdbprodsamples). Sono disponibili versioni normali e Lightweight (LT) del database. Per la maggior parte degli scenari, è preferibile la versione LT perché è meno complessa.

 **Northwind** è un database SQL Server relativamente semplice che è stato utilizzato per molti anni. È possibile scaricarlo come file con estensione bak dalla [pagina del database Northwind sul sito CodePlex](https://northwinddatabase.codeplex.com/). Per evitare problemi relativi alle autorizzazioni, decomprimere il file in una nuova cartella che non si trova nella cartella dell'utente.

#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Per ripristinare un database da un file con estensione bak in Visual Studio

1. Quando si esegue il backup di un database di Microsoft SQL Server, il risultato è un file con estensione bak. Per rendere il file con estensione bak utilizzabile di nuovo come file di database, è necessario *ripristinarlo*. Nel menu principale selezionare **Visualizza**  >  **Esplora oggetti di SQL Server**. Se non viene visualizzato, potrebbe essere necessario installarlo. Passare a **Pannello di controllo**  >  **programmi e funzionalità**, trovare Microsoft Visual Studio 2015, quindi fare clic sul pulsante **Cambia** . Quando viene visualizzato l'elenco dei componenti installati nella finestra del programma di installazione, selezionare la casella di controllo **Esplora oggetti di SQL Server** , quindi continuare l'installazione.

2. In Esplora oggetti di SQL Server fare clic con il pulsante destro del mouse su un motore di database SQL Server (ad esempio, local DB) e scegliere**nuova query**.

     ![Esplora oggetti di SQL Server nuova query](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata Esplora oggetti di SQL Server nuova query")

3. In primo luogo, sono necessari i nomi logici del database e i file di log all'interno del file con estensione bak. Per ottenerlo, immettere la query nell'editor di query SQL e quindi selezionare il pulsante verde **Esegui** nella parte superiore della finestra. Modificare il percorso del file, se necessario, per puntare al file con estensione bak.

    ```
    RESTORE FILELISTONLY
    FROM DISK = 'C:\nw\northwind.bak'
    GO
    ```

     Annotare i nomi logici visualizzati nella finestra risultati.  Per il database Northwind, i due nomi logici sono Northwind e Northwind_log.

4. A questo punto, eseguire la query per creare il database. Sostituire i percorsi di origine e di destinazione, i nomi di database logici e i nomi di file fisici per Northwind nel modo appropriato. Mantieni le estensioni di file con estensione MDF e ldf.

    ```
    RESTORE DATABASE Northwind
    FROM DISK = 'c:\nw\northwind.bak'
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'
    ```

5. In Esplora oggetti di SQL Server fare clic con il pulsante destro del mouse sul nodo **database** . verrà visualizzato il nodo database Northwind. In caso contrario, fare clic con il pulsante destro del mouse su database e scegliere **Aggiungi nuovo database**. Immettere il nome e il percorso del file con estensione MDF appena creato.

6. Il database è ora pronto per essere utilizzato come origine dati in Visual Studio.

#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Per ripristinare un database da un file con estensione bak in SQL Server Management Studio

1. Scaricare SQL Server Management Studio dal sito di download.

2. Nella finestra di **Esplora oggetti** di SSMS fare clic con il pulsante destro del mouse sul nodo **database** , scegliere**Ripristina database**e specificare il percorso del file con estensione bak.

     ![Database di ripristino di SSMS](../data-tools/media/raddata-ssms-restore-database.png "Database di ripristino raddata SSMS")
