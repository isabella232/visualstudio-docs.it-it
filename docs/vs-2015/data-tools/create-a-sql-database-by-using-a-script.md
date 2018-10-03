---
title: Creare un database SQL usando uno script | Microsoft Docs
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
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f9a2e3fdeccf8e3b094bd5fb1519d740cee7ce41
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517490"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Creare un database SQL usando uno script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [creare un database SQL usando uno script](https://docs.microsoft.com/visualstudio/data-tools/create-a-sql-database-by-using-a-script).  
  
  
In questa procedura dettagliata, si usa Visual Studio per creare un database di piccole dimensioni che contiene il codice di esempio per [creare un'applicazione dati semplice usando ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).  
  
 **Contenuto dell'argomento**  
  
-   [Creare uno script contenente uno schema di database](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)  
  
-   [Creare un progetto di database e importare uno schema](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)  
  
-   [Distribuire il database](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario disporre di SQL Server Express LocalDB, o un altro database SQL, installato.  
  
##  <a name="CreateScript"></a> Creare uno script contenente uno schema di database  
  
#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Per creare uno script da cui è possibile importare uno schema  
  
1.  Nelle [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], nella barra dei menu, selezionare **File** > **New** > **File**.  
  
     Il **nuovo File** verrà visualizzata la finestra di dialogo.  
  
2.  Nel **categorie** elenco, selezionare **generali**.  
  
3.  Nel **modelli** elenco, selezionare **Sql File**e quindi selezionare il **Open** pulsante.  
  
     Si apre l'editor Transact-SQL.  
  
4.  Copiare il codice Transact-SQL seguente e incollarlo nell'editor Transact-SQL.  
  
    ```  
    PRINT N'Creating Sales...';  
    GO  
    CREATE SCHEMA [Sales]  
        AUTHORIZATION [dbo];  
    GO  
    PRINT N'Creating Sales.Customer...';  
    GO  
    CREATE TABLE [Sales].[Customer] (  
        [CustomerID]   INT           IDENTITY (1, 1) NOT NULL,  
        [CustomerName] NVARCHAR (40) NOT NULL,  
        [YTDOrders]    INT           NOT NULL,  
        [YTDSales]     INT           NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Orders...';  
    GO  
    CREATE TABLE [Sales].[Orders] (  
        [CustomerID] INT      NOT NULL,  
        [OrderID]    INT      IDENTITY (1, 1) NOT NULL,  
        [OrderDate]  DATETIME NOT NULL,  
        [FilledDate] DATETIME NULL,  
        [Status]     CHAR (1) NOT NULL,  
        [Amount]     INT      NOT NULL  
    );  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDOrders...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDOrders] DEFAULT 0 FOR [YTDOrders];  
    GO  
    PRINT N'Creating Sales.Def_Customer_YTDSales...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [Def_Customer_YTDSales] DEFAULT 0 FOR [YTDSales];  
    GO  
    PRINT N'Creating Sales.Def_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_OrderDate] DEFAULT GetDate() FOR [OrderDate];  
    GO  
    PRINT N'Creating Sales.Def_Orders_Status...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [Def_Orders_Status] DEFAULT 'O' FOR [Status];  
    GO  
    PRINT N'Creating Sales.PK_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Customer]  
        ADD CONSTRAINT [PK_Customer_CustID] PRIMARY KEY CLUSTERED ([CustomerID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.PK_Orders_OrderID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [PK_Orders_OrderID] PRIMARY KEY CLUSTERED ([OrderID] ASC) WITH (ALLOW_PAGE_LOCKS = ON, ALLOW_ROW_LOCKS = ON, PAD_INDEX = OFF, IGNORE_DUP_KEY = OFF, STATISTICS_NORECOMPUTE = OFF);  
    GO  
    PRINT N'Creating Sales.FK_Orders_Customer_CustID...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [FK_Orders_Customer_CustID] FOREIGN KEY ([CustomerID]) REFERENCES [Sales].[Customer] ([CustomerID]) ON DELETE NO ACTION ON UPDATE NO ACTION;  
    GO  
    PRINT N'Creating Sales.CK_Orders_FilledDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_FilledDate] CHECK ((FilledDate >= OrderDate) AND (FilledDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.CK_Orders_OrderDate...';  
    GO  
    ALTER TABLE [Sales].[Orders]  
        ADD CONSTRAINT [CK_Orders_OrderDate] CHECK ((OrderDate > '01/01/2005') and (OrderDate < '01/01/2020'));  
    GO  
    PRINT N'Creating Sales.uspCancelOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspCancelOrder]  
    @OrderID INT  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'X'  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders - @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspFillOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspFillOrder]  
    @OrderID INT, @FilledDate DATETIME  
    AS  
    BEGIN  
    DECLARE @Delta INT, @CustomerID INT  
    BEGIN TRANSACTION  
        SELECT @Delta = [Amount], @CustomerID = [CustomerID]  
         FROM [Sales].[Orders] WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Orders]  
       SET [Status] = 'F',  
           [FilledDate] = @FilledDate  
    WHERE [OrderID] = @OrderID;  
  
    UPDATE [Sales].[Customer]  
       SET  
       YTDSales = YTDSales + @Delta  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    END  
    GO  
    PRINT N'Creating Sales.uspNewCustomer...';  
    GO  
    CREATE PROCEDURE [Sales].[uspNewCustomer]  
    @CustomerName NVARCHAR (40),  
    @CustomerID INT OUTPUT  
    AS  
    BEGIN  
    INSERT INTO [Sales].[Customer] (CustomerName) VALUES (@CustomerName);  
    SET @CustomerID = SCOPE_IDENTITY();  
    RETURN @@ERROR  
    END  
    GO  
    PRINT N'Creating Sales.uspPlaceNewOrder...';  
    GO  
    CREATE PROCEDURE [Sales].[uspPlaceNewOrder]  
    @CustomerID INT, @Amount INT, @OrderDate DATETIME, @Status CHAR (1)='O'  
    AS  
    BEGIN  
    DECLARE @RC INT  
    BEGIN TRANSACTION  
    INSERT INTO [Sales].[Orders] (CustomerID, OrderDate, FilledDate, Status, Amount)   
         VALUES (@CustomerID, @OrderDate, NULL, @Status, @Amount)  
    SELECT @RC = SCOPE_IDENTITY();  
    UPDATE [Sales].[Customer]  
       SET  
       YTDOrders = YTDOrders + @Amount  
        WHERE [CustomerID] = @CustomerID  
    COMMIT TRANSACTION  
    RETURN @RC  
    END  
    GO  
    CREATE PROCEDURE [Sales].[uspShowOrderDetails]  
    @CustomerID INT=0  
    AS  
    BEGIN  
    SELECT [C].[CustomerName], CONVERT(date, [O].[OrderDate]), CONVERT(date, [O].[FilledDate]), [O].[Status], [O].[Amount]  
      FROM [Sales].[Customer] AS C  
      INNER JOIN [Sales].[Orders] AS O  
         ON [O].[CustomerID] = [C].[CustomerID]  
      WHERE [C].[CustomerID] = @CustomerID  
    END  
    GO  
    ```  
  
5.  Nella barra dei menu, selezionare **File** > **Salva Sqlquery_1.SQL**.  
  
     Il **Salva File con nome** verrà visualizzata la finestra di dialogo.  
  
6.  Nel **nome File** casella, immettere `SampleImportScript.sql`, prendere nota della posizione in cui verrà salvare il file e quindi selezionare il **salvare** pulsante.  
  
7.  Nella barra dei menu, selezionare **File** > **Chiudi soluzione**.  
  
     Successivamente, creare un progetto di database e quindi importare lo schema dallo script creato.  
  
##  <a name="CreateProject"></a> Creare un progetto di database e importare uno schema  
  
#### <a name="to-create-a-database-project"></a>Per creare un progetto di database  
  
1.  Nella barra dei menu selezionare **File** > **Nuovo** > **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .  
  
2.  Sotto **Installed**, espandere il **modelli** nodo, espandere il **altri linguaggi** nodo, seleziona il **SQL Server** categoria e quindi Selezionare il **progetto di Database di SQL Server** modello.  
  
    > [!NOTE]
    >  Il **altri linguaggi** nodo non viene visualizzata in tutte le installazioni di Visual Studio.  
  
3.  Nel **Name** immettere `Small Database`.  
  
4.  Selezionare il **Crea directory per soluzione** casella di controllo se non è già selezionato.  
  
5.  Cancella il **aggiungere al controllo del codice sorgente** casella di controllo se non è già deselezionata, quindi fare clic il **OK** pulsante.  
  
     Il progetto di database viene creato e visualizzato nel **Esplora soluzioni**.  
  
     Successivamente, importare lo schema del database dallo script.  
  
#### <a name="to-import-a-database-schema-from-a-script"></a>Per importare uno schema di database da uno script  
  
1.  Nella barra dei menu, selezionare **Project** > **importazione** > **Script**.  
  
2.  Nel **benvenuto** pagina, esaminare il testo e quindi selezionare la **successivo** pulsante.  
  
3.  Selezionare il **File singolo** pulsante di opzione e quindi selezionare la **Sfoglia** pulsante.  
  
     Il **Importa Script SQL** verrà visualizzata la finestra di dialogo.  
  
4.  Aprire la cartella in cui è stato salvato il file SampleImportScript. SQL, selezionare il file e quindi selezionare il **aperto** pulsante.  
  
5.  Selezionare il **Finish** per chiudere la **Importa Script SQL** nella finestra di dialogo.  
  
     Lo script viene importato e gli oggetti che definisce lo script vengono aggiunti al progetto di database.  
  
6.  Esaminare il riepilogo e quindi fare clic sul **Finish** per chiudere la **Importa File di Script SQL** nella finestra di dialogo.  
  
7.  Nelle **Esplora soluzioni**, espandere le vendite, script e sicurezza cartelle del progetto e verificare che contengano file SQL.  
  
8.  Nelle **Esplora oggetti di SQL Server**, verificare che il database viene visualizzato sotto il **progetti** nodo.  
  
     A questo punto, il database contiene solo gli oggetti di sistema, ad esempio tabelle e stored procedure. Dopo aver distribuito il database, conterrà le tabelle utente e stored procedure che definiscono gli script.  
  
##  <a name="DeployDatabase"></a> Distribuire il database  
 Quando si preme il **F5** chiave, si distribuisce (o si pubblica) del database in un database LocalDB per impostazione predefinita. È possibile distribuire il database in una posizione diversa, aprire la pagina delle proprietà per il progetto, selezionare la **Debug** scheda e quindi modificando la stringa di connessione.

