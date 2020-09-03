---
title: Creare un database SQL tramite una finestra di progettazione | Microsoft Docs
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
author: jillre
ms.author: jillfra
manager: jillfra
robots: noindex,nofollow
ms.openlocfilehash: 33b97050f04fd23a9fa3b6c3c641faa5dfe4802f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651055"
---
# <a name="create-a-sql-database-by-using-a-designer"></a>Creare un database SQL usando una finestra di progettazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile esplorare le attività di base, ad esempio l'aggiunta di tabelle e la definizione di colonne, tramite Visual Studio per creare e aggiornare un file di database locale nel SQL Server Express database locale. Dopo aver completato questa procedura dettagliata, sarà possibile individuare funzionalità più avanzate utilizzando il database locale come punto iniziale per le altre procedure dettagliate che la richiedono.

 È inoltre possibile creare un database utilizzando SQL Server Management Studio (un download separato) o istruzioni Transact-SQL nella finestra degli strumenti **Esplora oggetti di SQL Server** in Visual Studio.

 Durante questa procedura dettagliata, verranno illustrate le seguenti attività:

- [Creare un progetto e un file di database locale](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewSQLDB)

- [Creazione di tabelle, colonne, chiavi primarie e chiavi esterne](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_CreateNewTbls)

- [Popola le tabelle con i dati](../data-tools/create-a-sql-database-by-using-a-designer.md#BKMK_Populating)

## <a name="prerequisites"></a>Prerequisiti
 Per completare questa procedura dettagliata, assicurarsi che SQL Server Data Tools sia installato. Dal menu **Visualizza** verrà visualizzato **Esplora oggetti di SQL Server**. Se non è presente, passare a **Installazione applicazioni**, fare clic su **Visual Studio 2015**, selezionare **modifica**e selezionare la casella accanto a **SQL Server Data Tools**.

## <a name="create-a-project-and-a-local-database-file"></a><a name="BKMK_CreateNewSQLDB"></a> Creazione di un progetto e di un file di database locale

#### <a name="to-create-a-project-and-a-database-file"></a>Per creare un progetto e un file di database

1. Creare un progetto Windows Forms denominato `SampleDatabaseWalkthrough` .

2. Nella barra dei menu selezionare **progetto**  >  **Aggiungi nuovo elemento**.

3. Nell'elenco dei modelli di elemento scorrere verso il basso e selezionare **database basato su servizi**.

    ![Finestra di dialogo Modelli di elemento](../data-tools/media/raddata-vsitemtemplates.png "raddata VSItemTemplates")

4. Denominare il database **SampleDatabase**, quindi selezionare il pulsante **Aggiungi** .

5. Se la finestra **origini dati** non è aperta, aprirla selezionando i tasti MAIUSC + ALT + D oppure, sulla barra dei menu, selezionando **Visualizza**  >  **altre**  >  **origini dati**di Windows.

6. Nella finestra **origini dati** selezionare il collegamento **Aggiungi nuova origine dati** .

7. Nella **Configurazione guidata origine dati**selezionare il pulsante **Avanti** quattro volte per accettare le impostazioni predefinite, quindi selezionare il pulsante **fine** .

   Se si apre la finestra delle proprietà per il database, è possibile visualizzare la stringa di connessione relativa e il percorso del file primario con estensione mdf. Si noterà che il file di database si trova nella cartella del progetto.

- In Visual Studio selezionare **Visualizza**  >  **Esplora oggetti di SQL Server** se tale finestra non è già aperta. Aprire la finestra Proprietà espandendo il nodo **connessioni dati** , aprendo il menu di scelta rapida per SampleDatabase. mdf e quindi selezionando **Proprietà**.

- In alternativa, è possibile selezionare **Visualizza**  >  **Esplora server**, se tale finestra non è già aperta. Aprire la finestra Proprietà espandendo il nodo **connessioni dati** . Aprire il menu di scelta rapida per SampleDatabase. MDF, quindi selezionare **Proprietà**.

## <a name="create-tables-columns-primary-keys-and-foreign-keys"></a><a name="BKMK_CreateNewTbls"></a> Creazione di tabelle, colonne, chiavi primarie e chiavi esterne
 In questa sezione verranno create un paio di tabelle, una chiave primaria in ogni tabella e alcune righe di dati di esempio. Nella procedura dettagliata successiva verrà illustrata la modalità di visualizzazione delle informazioni in un'applicazione. Verrà creata anche una chiave esterna per specificare quali record di una tabella possono corrispondere ai record dell'altra tabella.

#### <a name="to-create-the-customers-table"></a>Per creare la tabella Customers

1. In **Esplora server** o **Esplora oggetti di SQL Server**espandere il nodo **connessioni dati** , quindi espandere il nodo **SampleDatabase. MDF** .

2. Aprire il menu di scelta rapida per **tabelle**, quindi selezionare **Aggiungi nuova tabella**.

     Viene aperta la **Progettazione tabelle** e viene visualizzata una griglia con una riga predefinita che rappresenta una singola colonna della tabella che si sta creando. Aggiungendo righe alla griglia, vengono aggiunte colonne alla tabella.

3. Nella griglia, aggiungere una riga per ognuna delle seguenti voci:

    |Nome colonna|Tipo di dati|Consente valori null|
    |-----------------|---------------|-----------------|
    |`CustomerID`|`nchar(5)`|False (deselezionato)|
    |`CompanyName`|`nvarchar(50)`|False (deselezionato)|
    |`ContactName`|`nvarchar (50)`|True (selezionato)|
    |`Phone`|`nvarchar (24)`|True (selezionato)|

4. Aprire il menu di scelta rapida per la `CustomerID` riga, quindi selezionare **Imposta chiave primaria**.

5. Aprire il menu di scelta rapida per la riga predefinita, quindi selezionare **Elimina**.

6. Denominare la tabella Customers aggiornando la prima riga nel riquadro dello script in modo che corrisponda all'esempio seguente:

    ```
    CREATE TABLE [dbo].[Customers]
    ```

     L'output dovrebbe essere simile al seguente:

     ![Progettazione tabelle](../data-tools/media/raddata-table-designer.png "Progettazione tabelle raddata")

7. Nell'angolo superiore sinistro del **Progettazione tabelle**selezionare il pulsante **Aggiorna** .

8. Nella finestra di dialogo **Anteprima aggiornamenti database** selezionare il pulsante **Aggiorna database** .

     Le modifiche vengono salvate nel file del database locale.

#### <a name="to-create-the-orders-table"></a>Per creare la tabella Orders

1. Aggiungere un'altra tabella, quindi aggiungere una riga per ogni voce nella tabella seguente:

    |Nome colonna|Tipo di dati|Consente valori null|
    |-----------------|---------------|-----------------|
    |`OrderID`|`int`|False (deselezionato)|
    |`CustomerID`|`nchar(5)`|False (deselezionato)|
    |`OrderDate`|`datetime`|True (selezionato)|
    |`OrderQuantity`|`int`|True (selezionato)|

2. Impostare **OrderID** come chiave primaria, quindi eliminare la riga predefinita.

3. Denominare la tabella Orders aggiornando la prima riga nel riquadro dello script in modo che corrisponda all'esempio seguente:

    ```
    CREATE TABLE [dbo].[Orders]
    ```

4. Nell'angolo superiore sinistro del **Progettazione tabelle**selezionare il pulsante **Aggiorna** .

5. Nella finestra di dialogo **Anteprima aggiornamenti database** selezionare il pulsante **Aggiorna database** .

     Le modifiche vengono salvate nel file del database locale.

#### <a name="to-create-a-foreign-key"></a>Per creare una chiave esterna

1. Nel riquadro del contesto sul lato destro della griglia, aprire il menu di scelta rapida per **chiavi esterne**, quindi selezionare **Aggiungi nuova chiave esterna**, come illustrato nella figura seguente.

     ![Aggiunta di una chiave esterna in Progettazione tabelle](../data-tools/media/foreignkey.png "ForeignKey")

2. Nella casella di testo che viene visualizzata, sostituire **ToTable** con `Customers` .

3. Nel riquadro T-SQL aggiornare l'ultima riga in modo che corrisponda all'esempio seguente:

    ```
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. Nell'angolo superiore sinistro del **Progettazione tabelle**selezionare il pulsante **Aggiorna** .

5. Nella finestra di dialogo **Anteprima aggiornamenti database** selezionare il pulsante **Aggiorna database** .

     Le modifiche vengono salvate nel file del database locale.

## <a name="populate-the-tables-with-data"></a><a name="BKMK_Populating"></a> Popola le tabelle con i dati

#### <a name="to-populate-the-tables-with-data"></a>Per inserire dati nelle tabelle

1. In **Esplora server** o **Esplora oggetti di SQL Server**espandere il nodo per il database di esempio.

2. Aprire il menu di scelta rapida per il nodo **tabelle** , selezionare **Aggiorna**, quindi espandere il nodo **tabelle** .

3. Aprire il menu di scelta rapida per la tabella Customers, quindi selezionare **Mostra dati tabella**.

4. Aggiungere i dati desiderati per almeno tre clienti.

     È possibile specificare tutti i cinque caratteri desiderati come ID cliente, ma sceglierne almeno uno da ricordare in un secondo momento per l'utilizzo in questa procedura.

5. Aprire il menu di scelta rapida per la tabella Orders, quindi selezionare **Mostra dati tabella**.

6. Aggiungere i dati per almeno tre ordini.

    > [!IMPORTANT]
    > Verificare che tutti gli ID ordine e le quantità di ordini siano valori Integer e che ogni ID cliente corrisponda a un valore specificato nella colonna CustomerID della tabella Customers.

7. Nella barra dei menu selezionare **file**  >  **Salva tutto**.

8. Sulla barra dei menu selezionare **file**  >  **Chiudi soluzione**.

    > [!NOTE]
    > Come procedura consigliata, è possibile eseguire il backup del file del database appena creato copiandolo, quindi incollandolo in un altro percorso o assegnando alla copia un nome diverso.

## <a name="next-steps"></a>Passaggi successivi
 Ora che si dispone di un file di database locale con alcuni dati di esempio, è possibile completare le procedure dettagliate che illustrano le attività del database.
