---
title: Creare un database SQL usando uno script | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
ms.assetid: 36f913c0-f5a7-4831-83a0-baba721ac95c
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3bef7c4be2f38d0f50b2a13c7745cb212204769b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72670086"
---
# <a name="create-a-sql-database-by-using-a-script"></a>Creare un database SQL usando uno script
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata viene usato Visual Studio per creare un database di piccole dimensioni che contiene il codice di esempio per [creare un'applicazione dati semplice usando ADO.NET](../data-tools/create-a-simple-data-application-by-using-adonet.md).

 **Contenuto dell'argomento**

- [Creare uno script contenente uno schema del database](../data-tools/create-a-sql-database-by-using-a-script.md#CreateScript)

- [Creare un progetto di database e importare uno schema](../data-tools/create-a-sql-database-by-using-a-script.md#CreateProject)

- [Distribuire il database](../data-tools/create-a-sql-database-by-using-a-script.md#DeployDatabase)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, è necessario disporre di SQL Server Express database locale o di un altro database SQL installato.

## <a name="create-a-script-that-contains-a-database-schema"></a><a name="CreateScript"></a> Creare uno script contenente uno schema di database

#### <a name="to-create-a-script-from-which-you-can-import-a-schema"></a>Per creare uno script da cui sia possibile importare uno schema

1. Nella [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] barra dei menu di scegliere **file**  >  **nuovo**  >  **file**.

     Verrà visualizzata la finestra di dialogo **Nuovo file** .

2. Nell'elenco **categorie** selezionare **generale**.

3. Nell'elenco **modelli** selezionare **file SQL**, quindi fare clic sul pulsante **Apri** .

     Verrà aperto l'editor Transact-SQL.

4. Copiare il codice Transact-SQL seguente e incollarlo nell'editor Transact-SQL.

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

5. Nella barra dei menu selezionare **file**  >  **Salva SqlQuery_1. SQL come**.

     Verrà visualizzata la finestra **di dialogo Salva file con nome** .

6. Nella casella **nome file** immettere `SampleImportScript.sql` , prendere nota del percorso in cui verrà salvato il file, quindi selezionare il pulsante **Salva** .

7. Sulla barra dei menu selezionare **file**  >  **Chiudi soluzione**.

     Successivamente, creare un progetto di database e quindi importare lo schema dallo script creato.

## <a name="create-a-database-project-and-import-a-schema"></a><a name="CreateProject"></a> Creare un progetto di database e importare uno schema

#### <a name="to-create-a-database-project"></a>Per creare un progetto di database

1. Nella barra dei menu selezionare **file**  >  **nuovo**  >  **progetto**.

     Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

2. In **installato**espandere il nodo **modelli** , espandere il nodo **altri linguaggi** , selezionare la categoria **SQL Server** , quindi selezionare il modello di **progetto di database SQL Server** .

    > [!NOTE]
    > Il nodo **altri linguaggi** non viene visualizzato in tutte le installazioni di Visual Studio.

3. Nella casella **nome** immettere `Small Database` .

4. Se non è già selezionata, selezionare la casella **di controllo Crea directory per soluzione** .

5. Deselezionare la casella **di controllo Aggiungi al controllo del codice sorgente** , se non è già deselezionata, quindi selezionare il pulsante **OK** .

     Il progetto di database viene creato e visualizzato in **Esplora soluzioni**.

     Importare quindi lo schema del database dallo script.

#### <a name="to-import-a-database-schema-from-a-script"></a>Per importare uno schema del database da uno script

1. Nella barra dei menu selezionare **progetto**  >  **Importa**  >  **script**.

2. Nella pagina di **benvenuto** esaminare il testo e quindi fare clic sul pulsante **Avanti** .

3. Selezionare il pulsante di opzione **file singolo** , quindi selezionare il pulsante **Sfoglia** .

     Verrà visualizzata la finestra di dialogo **Importa script SQL** .

4. Aprire la cartella in cui è stato salvato il file SampleImportScript. SQL, selezionare il file e quindi fare clic sul pulsante **Apri** .

5. Selezionare il pulsante **fine** per chiudere la finestra di dialogo **Importa script SQL** .

     Lo script viene importato e gli oggetti definiti dallo script vengono aggiunti al progetto di database.

6. Esaminare il riepilogo, quindi fare clic sul pulsante **fine** per chiudere la finestra di dialogo **Importa file script SQL** .

7. In **Esplora soluzioni**espandere le cartelle vendite, script e sicurezza del progetto e verificare che contengano file con estensione SQL.

8. In **Esplora oggetti di SQL Server**verificare che il database venga visualizzato sotto il nodo **progetti** .

     A questo punto, il database contiene solo oggetti di sistema, ad esempio tabelle e stored procedure. Dopo aver distribuito il database, conterrà le tabelle utente e le stored procedure definite dagli script.

## <a name="deploy-the-database"></a><a name="DeployDatabase"></a> Distribuire il database
 Quando si preme il tasto **F5** , per impostazione predefinita si distribuisce (o si pubblica) il database in un database del database locale. È possibile distribuire il database in un percorso diverso aprendo la pagina delle proprietà per il progetto, selezionando la scheda **debug** e quindi modificando la stringa di connessione.
