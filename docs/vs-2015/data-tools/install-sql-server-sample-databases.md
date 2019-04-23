---
title: Installare SQL Server database di esempio | Microsoft Docs
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.date: 11/15/2016
ms.topic: conceptual
ms.assetid: 38840167-c3f8-4cb3-8d15-8af04a0a20a1
caps.latest.revision: 14
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: afc99ba7d5b7a6b5cf9fc0e610160213dec5d2e8
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59654503"
---
# <a name="install-sql-server-sample-databases"></a>Installare SQL Server database di esempio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Database di esempio sono utili per la sperimentazione con query SQL e LINQ, Data Binding, la modellazione di Entity Framework e così via.  Ogni prodotto di database ha un proprio database di esempio. Northwind e AdventureWorks sono due database di esempio di SQL Server più diffusi.  
  
 **AdventureWorks** è il database corrente di esempio fornito per i prodotti SQL Server. È possibile scaricarlo come file con estensione mdf dal [AdventureWorks pagina sul sito Codeplex](http://msftdbprodsamples.codeplex.com/). Sono disponibili versioni (LT) regolari e leggere del database qui. Per la maggior parte degli scenari, la versione LT è preferibile perché è meno complessa.  
  
 **Northwind** è un database di SQL Server relativamente semplice che è stato usato da molti anni. È possibile scaricarlo come file con estensione bak dal [pagina del database Northwind in CodePlex](https://northwinddatabase.codeplex.com/). Per evitare problemi relativi alle autorizzazioni, decomprimere il file in una nuova cartella che non è presente nella cartella dell'utente.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-visual-studio"></a>Per ripristinare un database da un file con estensione bak in Visual Studio  
  
1.  Quando si esegue il backup di un database Microsoft SQL Server, il risultato è un file con estensione bak. Per rendere l'estensione bak file utilizzabile nuovamente come un file di database, deve essere *ripristinato*. Nel menu principale, selezionare **View** > **Esplora oggetti di SQL Server**. Se non è visualizzata, è necessario installarlo. Passare a **Pannello di controllo** > **programmi e funzionalità**, trovare Microsoft Visual Studio 2015 e scegliere il **modifica** pulsante. Nella finestra del programma di installazione venga visualizzato l'elenco dei componenti installati, selezionare la **Esplora oggetti di SQL Server** casella di controllo e quindi continuare con l'installazione.  
  
2.  In Esplora oggetti di SQL Server, fare doppio clic su qualsiasi motore di database di SQL Server (ad esempio, database locale) e selezionare**nuova Query**.  
  
     ![SQL Server oggetto Explorer nuova Query](../data-tools/media/raddata-sql-server-object-explorer-new-query.png "raddata SQL Server oggetto Explorer nuova Query")  
  
3.  È necessario in primo luogo, i nomi logici dei file di database e log all'interno del file con estensione bak. Per ottenerlo, immettere la query nell'Editor di Query SQL e quindi selezionare il colore verde **eseguire** nella parte superiore della finestra. Se necessario in modo da puntare al file con estensione bak, modificare il percorso del file.  
  
    ```  
    RESTORE FILELISTONLY  
    FROM DISK = 'C:\nw\northwind.bak'  
    GO  
    ```  
  
     Annotare i nomi logici che vengono visualizzati nella finestra dei risultati.  Per il database Northwind, i due nomi logici sono Northwind e Northwind_log.  
  
4.  A questo punto eseguire la query per creare il database. Sostituire i percorsi di origine e di destinazione, i nomi di database logico e nomi di file fisici per Northwind come appropriato. Mantenere il file con estensione mdf e ldf delle estensioni di file.  
  
    ```  
    RESTORE DATABASE Northwind  
    FROM DISK = 'c:\nw\northwind.bak'  
    WITH MOVE 'Northwind' TO 'c:\nw\northwind.mdf',  
    MOVE 'Northwind_log' TO 'c:\nw\northwind.ldf'  
    ```  
  
5.  In Esplora oggetti di SQL Server, fare clic sui **database** nodo, verrà visualizzato il nodo del database Northwind. In caso contrario, quindi fare clic sul database e selezionare **Aggiungi nuovo Database**. Immettere il nome e il percorso del file con estensione mdf che appena creato.  
  
6.  Il database è ora pronto per l'uso come origine dati in Visual Studio.  
  
#### <a name="to-restore-a-database-from-a-bak-file-in-sql-server-management-studio"></a>Per ripristinare un database da un file con estensione bak in SQL Server Management Studio  
  
1.  Scaricare SQL Server Management Studio dal sito di download.  
  
2.  In SSMS **Esplora oggetti** finestra, fare doppio clic sui **database** nodo, seleziona**Restore Database**e specificare il percorso del file con estensione bak.  
  
     ![Ripristina Database di SQL Server Management Studio](../data-tools/media/raddata-ssms-restore-database.png "raddata Ripristina Database di SQL Server Management Studio")
