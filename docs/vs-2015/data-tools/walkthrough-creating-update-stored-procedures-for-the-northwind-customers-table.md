---
title: 'Procedura dettagliata: Creazione di aggiornamento Stored procedure per la tabella Customers di Northwind | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
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
- Northwind sample database
- stored procedures [Visual Studio]
- O/R Designer, stored procedures
ms.assetid: 6fd9e7e0-6862-44d3-9710-acc5a72d4ffd
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
robots: noindex,nofollow
ms.openlocfilehash: 4972c1341490f78bba03bdd390ac13903c55be84
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49204048"
---
# <a name="walkthrough-creating-update-stored-procedures-for-the-northwind-customers-table"></a>Procedura dettagliata: creazione delle stored procedure di aggiornamento per la tabella Customers Northwind
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Alcuni argomenti della Guida nel [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] documentazione necessarie stored procedure aggiuntive nel database di esempio Northwind per l'esecuzione di aggiornamenti (gli inserimenti, aggiornamenti ed eliminazioni) dei dati nella tabella Customers.  
  
 Questa procedura dettagliata illustra come creare le stored procedure aggiuntive nel database di esempio Northwind per [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Nella sezione Passaggi successivi, più avanti in questo argomento, sono disponibili collegamenti ad argomenti in cui viene illustrato l'uso delle stored procedure aggiuntive.  
  
 In questa procedura dettagliata si apprenderà come eseguire le attività seguenti:  
  
-   Creare una connessione dati al database di esempio Northwind.  
  
-   Creare le stored procedure.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere alla versione SQL Server del database di esempio Northwind. Per altre informazioni, vedere [procedura: installare database di esempio](../data-tools/how-to-install-sample-databases.md).  
  
## <a name="connecting-to-the-northwind-database"></a>Connessione al database Northwind  
 Questa procedura dettagliata richiede una connessione alla versione SQL Server del database Northwind. Nella procedura descritta di seguito vengono fornite le istruzioni per la creazione della connessione dati.  
  
> [!NOTE]
>  Se si dispone già di una connessione dati al database Northwind, è possibile passare alla sezione successiva, Creazione delle stored procedure.  
  
#### <a name="to-create-a-data-connection-to-the-northwind-sql-server-database"></a>Per creare una connessione dati al database di esempio Northwind  
  
1.  Nel **View** menu, fare clic su **Esplora Server**/**Esplora Database**.  
  
2.  Fare doppio clic su **connessioni dati** e fare clic su **Aggiungi connessione**.  
  
3.  Nel **Scegli origine dati** della finestra di dialogo fare clic su **Microsoft SQL Server**, quindi fare clic su **OK**.  
  
     Se il **Aggiungi connessione** verrà visualizzata la finestra di dialogo e il **zdroj dat** non **Microsoft SQL Server (SqlClient)**, fare clic su **modifica** per aprire la **Scegli/Modifica origine dati** finestra di dialogo, fare clic su **Microsoft SQL Server**, quindi fare clic su **OK**.  
  
4.  Fare clic su un **nome Server** nell'elenco a discesa elenco o digitare il nome del server in cui si trova il database Northwind.  
  
5.  In base ai requisiti del database o applicazione, fare clic su **usare l'autenticazione di Windows** oppure usare un nome utente specifico e una password per accedere al computer che esegue SQL Server (**l'autenticazionediSQLServer**).  
  
6.  Fare clic con il database Northwind nel **selezionare o immettere un nome di database** elenco.  
  
7.  Fare clic su **OK**.  
  
     La connessione dati viene aggiunto a **Esplora Server**/**Esplora Database**.  
  
## <a name="creating-the-stored-procedures"></a>Creazione delle stored procedure  
 Creare le stored procedure eseguendo lo script SQL fornito sul database Northwind mediante la [Visual Database Tools](http://msdn.microsoft.com/en-us/6b145922-2f00-47db-befc-bf351b4809a1) disponibile in **Esplora Server** /  **Esplora database**.  
  
#### <a name="to-create-the-stored-procedures-by-using-a-sql-script"></a>Per creare le stored procedure mediante uno script SQL  
  
1.  Espandere il database Northwind **Esplora Server**/**Esplora Database**.  
  
2.  Fare doppio clic il **Stored procedure** nodo e fare clic su **Aggiungi nuova Stored Procedure**.  
  
3.  Incollare il codice seguente nell'editor del codice, sostituendo il modello `CREATE PROCEDURE`:  
  
    ```  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'SelectCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.[SelectCustomers]  
    GO  
  
    CREATE PROCEDURE dbo.[SelectCustomers]  
    AS  
        SET NOCOUNT ON;  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM dbo.Customers  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'InsertCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.InsertCustomers  
    GO  
  
    CREATE PROCEDURE dbo.InsertCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24)  
    )  
    AS  
        SET NOCOUNT OFF;  
    INSERT INTO [dbo].[Customers] ([CustomerID], [CompanyName], [ContactName], [ContactTitle], [Address], [City], [Region], [PostalCode], [Country], [Phone], [Fax]) VALUES (@CustomerID, @CompanyName, @ContactName, @ContactTitle, @Address, @City, @Region, @PostalCode, @Country, @Phone, @Fax);  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'UpdateCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.UpdateCustomers  
    GO  
  
    CREATE PROCEDURE dbo.UpdateCustomers  
    (  
        @CustomerID nchar(5),  
        @CompanyName nvarchar(40),  
        @ContactName nvarchar(30),  
        @ContactTitle nvarchar(30),  
        @Address nvarchar(60),  
        @City nvarchar(15),  
        @Region nvarchar(15),  
        @PostalCode nvarchar(10),  
        @Country nvarchar(15),  
        @Phone nvarchar(24),  
        @Fax nvarchar(24),  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    UPDATE [dbo].[Customers] SET [CustomerID] = @CustomerID, [CompanyName] = @CompanyName, [ContactName] = @ContactName, [ContactTitle] = @ContactTitle, [Address] = @Address, [City] = @City, [Region] = @Region, [PostalCode] = @PostalCode, [Country] = @Country, [Phone] = @Phone, [Fax] = @Fax WHERE (([CustomerID] = @Original_CustomerID));  
  
    SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax FROM Customers WHERE (CustomerID = @CustomerID)  
    GO  
  
    IF EXISTS (SELECT * FROM sysobjects WHERE name = 'DeleteCustomers' AND user_name(uid) = 'dbo')  
        DROP PROCEDURE dbo.DeleteCustomers  
    GO  
  
    CREATE PROCEDURE dbo.DeleteCustomers  
    (  
        @Original_CustomerID nchar(5)  
    )  
    AS  
        SET NOCOUNT OFF;  
    DELETE FROM [dbo].[Customers] WHERE (([CustomerID] = @Original_CustomerID))  
    GO  
    ```  
  
4.  Selezionare tutto il testo nell'Editor del codice, fare clic sul testo selezionato e fare clic su **Esegui selezione**.  
  
     Verranno create le stored procedure SelectCustomers, InsertCustomers, UpdateCustomers e DeleteCustomers per il database Northwind.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Dopo aver creato le stored procedure, provare le procedure dettagliate seguenti, in cui viene illustrato come usare le stored procedure:  
  
 [Procedura: Assegnare stored procedure per eseguire aggiornamenti, inserimenti ed eliminazioni (O/R Designer)](../data-tools/how-to-assign-stored-procedures-to-perform-updates-inserts-and-deletes-o-r-designer.md)  
  
 [Procedura dettagliata: Creazione di classi LINQ to SQL (O-R Designer)](http://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233)  
  
 [Procedura dettagliata: personalizzazione del comportamento di inserimento, aggiornamento ed eliminazione delle classi di entità](../data-tools/walkthrough-customizing-the-insert-update-and-delete-behavior-of-entity-classes.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](http://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)   
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)