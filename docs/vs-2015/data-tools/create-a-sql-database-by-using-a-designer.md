---
title: Creare un database SQL usando una finestra di progettazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- SQL Server Express
- local data
- LocalDB
- SQLEXPRESS
- data [Visual Studio], Local data
- SQL Express
- data [Visual Studio], walkthroughs
- databases, creating
- database files, creating
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
caps.latest.revision: 54
author: gewarren
ms.author: gewarren
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: f816095992379748b6d1888b5df54dc5433a8306
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436961"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Creare un database SQL usando una finestra di progettazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile esplorare le attività di base, ad esempio l'aggiunta di tabelle e definizione di colonne, tramite Visual Studio per creare e aggiornare un file di database locale in LocalDB di SQL Server Express. Dopo aver completato questa procedura dettagliata, sarà possibile individuare funzionalità più avanzate utilizzando il database locale come punto iniziale per le altre procedure dettagliate che la richiedono.  
  
 È anche possibile creare un database usando SQL Server Management Studio (un download separato) o istruzioni Transact-SQL nel **Esplora oggetti di SQL Server** finestra degli strumenti in Visual Studio.  
  
 Durante questa procedura dettagliata, verranno illustrate le seguenti attività:  
  
- [Creare un progetto e un file di database locale](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)  
  
- [Creare tabelle, colonne, chiavi primarie e chiavi esterne](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)  
  
- [Popolare le tabelle con dati](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, assicurarsi di aver installato SQL Server Data Tools. Nel **vista** menu, si noterà **Esplora oggetti di SQL Server**. Se non è presente, andare al **Aggiungi / Rimuovi programmi**, fare clic su **Visual Studio 2015**, selezionare **modifica**, quindi selezionare la casella accanto a **SQL Server Data Tools**.  
  
## <a name="BKMK_CreateNewSQLDB"></a> Creare un progetto e un file di database locale  
  
#### <a name="to-create-a-project-and-a-database-file"></a>Per creare un progetto e un file di database  
  
1. Creare un progetto Windows Form denominato `SampleDatabaseWalkthrough`.  
  
2. Nella barra dei menu, selezionare **Project** > **Aggiungi nuovo elemento**.  
  
3. Nell'elenco dei modelli di elemento, scorrere verso il basso e selezionare **Database basato sul servizio**.  
  
    ![Finestra di dialogo modelli di elemento](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")  
  
4. Assegnare un nome del database **SampleDatabase**, quindi selezionare il **Add** pulsante.  
  
5. Se il **Zdroje dat** finestra non è aperta, aprirlo selezionando i tasti Maiusc + Alt + D o, nella barra dei menu, selezionando **View** > **Other Windows**  >  **Zdroje dat**.  
  
6. Nel **Zdroje dat** finestra, seleziona la **Aggiungi nuova origine dati** collegamento.  
  
7. Nel **configurazione guidata origine dati**, selezionare la **successiva** quattro volte per accettare le impostazioni predefinite e quindi selezionare il **fine** pulsante.  
  
   Se si apre la finestra delle proprietà per il database, è possibile visualizzare la stringa di connessione relativa e il percorso del file primario con estensione mdf. Si noterà che il file di database sia nella cartella del progetto.  
  
- In Visual Studio, selezionare **View** > **Esplora oggetti di SQL Server** se tale finestra non è già aperta. Aprire la finestra Proprietà espandere la **connessioni dati** nodo, aprendo il menu di scelta rapida per SampleDatabase. mdf e quindi selezionando **proprietà**.  
  
- In alternativa, è possibile selezionare **View** > **Esplora Server**, se tale finestra non è già aperta. Aprire la finestra Proprietà espandere la **connessioni dati** nodo. Aprire il menu di scelta rapida per SampleDatabase. mdf e quindi selezionare **proprietà**.  
  
## <a name="BKMK_CreateNewTbls"></a> Creare tabelle, colonne, chiavi primarie e chiavi esterne  
 In questa sezione verranno create un paio di tabelle, una chiave primaria in ogni tabella e alcune righe di dati di esempio. Nella procedura dettagliata successiva verrà illustrata la modalità di visualizzazione delle informazioni in un'applicazione. Verrà creata anche una chiave esterna per specificare quali record di una tabella possono corrispondere ai record dell'altra tabella.  
  
#### <a name="to-create-the-customers-table"></a>Per creare la tabella Customers  
  
1. Nella **Esplora Server** o **Esplora oggetti di SQL Server**, espandere il **connessioni dati** nodo, quindi espandere il **SampleDatabase. mdf**nodo.  
  
2. Aprire il menu di scelta rapida **tabelle**, quindi selezionare **Aggiungi nuova tabella**.  
  
     Viene aperta la **Progettazione tabelle** e viene visualizzata una griglia con una riga predefinita che rappresenta una singola colonna della tabella che si sta creando. Aggiungendo righe alla griglia, vengono aggiunte colonne alla tabella.  
  
3. Nella griglia, aggiungere una riga per ognuna delle seguenti voci:  
  
    |Nome colonna|Tipo di dati|Consente valori null|  
    |-----------------|---------------|-----------------|  
    |`CustomerID`|`nchar(5)`|False (deselezionato)|  
    |`CompanyName`|`nvarchar(50)`|False (deselezionato)|  
    |`ContactName`|`nvarchar (50)`|True (selezionato)|  
    |`Phone`|`nvarchar (24)`|True (selezionato)|  
  
4. Aprire il menu di scelta rapida per il `CustomerID` riga e quindi selezionare **Imposta chiave primaria**.  
  
5. Aprire il menu di scelta rapida per la riga predefinita e quindi selezionare **Elimina**.  
  
6. Denominare la tabella Customers aggiornando la prima riga nel riquadro dello script in modo che corrisponda all'esempio seguente:  
  
    ```  
    CREATE TABLE [dbo].[Customers]  
    ```  
  
     Viene visualizzato un output simile al seguente:  
  
     ![Progettazione tabelle](../data-tools/media/raddata-table-designer.png "raddata Progettazione tabelle")  
  
7. Nell'angolo superiore sinistro della **Progettazione tabelle**, selezionare la **Update** pulsante.  
  
8. Nel **Anteprima aggiornamenti Database** finestra di dialogo, seleziona la **Update Database** pulsante.  
  
     Le modifiche vengono salvate nel file del database locale.  
  
#### <a name="to-create-the-orders-table"></a>Per creare la tabella Orders  
  
1. Aggiungere un'altra tabella, quindi aggiungere una riga per ogni voce nella tabella seguente:  
  
    |Nome colonna|Tipo di dati|Consente valori null|  
    |-----------------|---------------|-----------------|  
    |`OrderID`|`int`|False (deselezionato)|  
    |`CustomerID`|`nchar(5)`|False (deselezionato)|  
    |`OrderDate`|`datetime`|True (selezionato)|  
    |`OrderQuantity`|`int`|True (selezionato)|  
  
2. Impostare **OrderID** come chiave primaria e quindi eliminare la riga predefinita.  
  
3. Denominare la tabella Orders aggiornando la prima riga nel riquadro dello script in modo che corrisponda all'esempio seguente:  
  
    ```  
    CREATE TABLE [dbo].[Orders]  
    ```  
  
4. Nell'angolo superiore sinistro della **Progettazione tabelle**, selezionare la **Update** pulsante.  
  
5. Nel **Anteprima aggiornamenti Database** finestra di dialogo, seleziona la **Update Database** pulsante.  
  
     Le modifiche vengono salvate nel file del database locale.  
  
#### <a name="to-create-a-foreign-key"></a>Per creare una chiave esterna  
  
1. Nel riquadro contesto sul lato destro della griglia, aprire il menu di scelta rapida **chiavi esterne**, quindi selezionare **Aggiungi nuova chiave esterna**, come illustrato di seguito.  
  
     ![Aggiunta di una chiave esterna in Progettazione tabelle](../data-tools/media/foreignkey.png "perché ForeignKey")  
  
2. Nella casella di testo che viene visualizzato, sostituire **ToTable** con `Customers`.  
  
3. Nel riquadro T-SQL, aggiornare l'ultima riga affinché corrisponda all'esempio seguente:  
  
    ```  
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])  
    ```  
  
4. Nell'angolo superiore sinistro della **Progettazione tabelle**, selezionare la **Update** pulsante.  
  
5. Nel **Anteprima aggiornamenti Database** finestra di dialogo, seleziona la **Update Database** pulsante.  
  
     Le modifiche vengono salvate nel file del database locale.  
  
## <a name="BKMK_Populating"></a> Popolare le tabelle con dati  
  
#### <a name="to-populate-the-tables-with-data"></a>Per inserire dati nelle tabelle  
  
1. Nelle **Esplora Server** oppure **Esplora oggetti di SQL Server**, espandere il nodo per il database di esempio.  
  
2. Aprire il menu di scelta rapida per il **tabelle** nodo, seleziona **aggiornare**, quindi espandere il **tabelle** nodo.  
  
3. Aprire il menu di scelta rapida per la tabella Customers e quindi selezionare **Mostra dati tabella**.  
  
4. Aggiungere i dati desiderati per almeno tre clienti.  
  
     È possibile specificare tutti i cinque caratteri desiderati come ID cliente, ma sceglierne almeno uno da ricordare in un secondo momento per l'utilizzo in questa procedura.  
  
5. Aprire il menu di scelta rapida per la tabella Orders e quindi selezionare **Mostra dati tabella**.  
  
6. Aggiungere i dati per almeno tre ordini.  
  
    > [!IMPORTANT]
    > Verificare che tutti gli ID ordine e le quantità di ordini siano valori Integer e che ogni ID cliente corrisponda a un valore specificato nella colonna CustomerID della tabella Customers.  
  
7. Nella barra dei menu, selezionare **File** > **Salva tutto**.  
  
8. Nella barra dei menu, selezionare **File** > **Chiudi soluzione**.  
  
    > [!NOTE]
    > Come procedura consigliata, è possibile eseguire il backup del file del database appena creato copiandolo, quindi incollandolo in un altro percorso o assegnando alla copia un nome diverso.  
  
## <a name="next-steps"></a>Passaggi successivi  
 Ora che avete un file di database locale con alcuni dati di esempio, è possibile completare una delle procedure dettagliate che illustrano le attività di database.
