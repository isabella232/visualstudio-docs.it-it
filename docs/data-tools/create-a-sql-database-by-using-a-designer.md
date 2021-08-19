---
title: Creare un file di database e usare Progettazione tabelle
description: Esercitazione che descrive come aggiungere tabelle e chiavi esterne a un database usando Progettazione tabelle in Visual Studio. Viene inoltre illustrato come aggiungere dati tramite l'interfaccia grafica.
ms.date: 09/19/2019
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: cecf47d023b98ce8ad3cf67799e4bdfff66f45fa
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122037148"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Creare un database e aggiungere tabelle in Visual Studio

È possibile usare Visual Studio per creare e aggiornare un file di database locale in SQL Server Express Local DB. È anche possibile creare un database eseguendo istruzioni Transact-SQL nella finestra SQL Server Esplora oggetti strumenti di Visual Studio.  In questo argomento si creerà un file con estensione *mdf* e si aggiungeranno tabelle e chiavi usando il Progettazione tabelle.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, sono necessari  i carichi di lavoro Sviluppo per **desktop .NET** e Archiviazione ed elaborazione dati installati in Visual Studio. Per installarli, **aprire Programma di installazione di Visual Studio** e **scegliere** Modifica (o Altro modifica) accanto alla versione Visual Studio che si vuole   >  modificare.

> [!NOTE]
> Le procedure descritte in questo articolo si applicano solo .NET Framework Windows progetti Forms, non ai progetti .NET Core Windows Forms.

## <a name="create-a-project-and-a-local-database-file"></a>Creare un progetto e un file di database locale

1. Creare un nuovo **progetto Windows Forms App (.NET Framework)** e deno assegnare al progetto il nome **SampleDatabaseWalkthrough.**

2. Nella barra dei menu selezionare **Project**  >  **Aggiungi nuovo elemento**.

3. Nell'elenco dei modelli di elemento scorrere verso il basso e selezionare **Database basato su servizio.**

   ![Finestra di dialogo Modelli di elemento](../data-tools/media/raddata-vsitemtemplates.png)

4. Assegnare al database **il nome SampleDatabase** e quindi fare clic **su Aggiungi**.

### <a name="add-a-data-source"></a>Aggiungere un'origine dati

1. Se la **finestra Origini** dati non è aperta, aprirla premendo MAIUSC ALT D o selezionando Visualizza altre Windows dati sulla +  +  barra   >    >   dei menu.

1. Nella finestra **Origini dati** selezionare Aggiungi nuova **origine dati**.

   ![Aggiungere una nuova origine dati in Visual Studio](media/add-new-data-source.png)

   Verrà **visualizzata la Configurazione guidata origine** dati.

1. Nella pagina **Scegliere un tipo di origine dati** scegliere **Database** e quindi scegliere **Avanti.**

1. Nella pagina **Scegliere un modello di database** scegliere Avanti **per** accettare il valore predefinito (Set di dati).

1. Nella pagina **Scegli connessione dati** selezionare il file **SampleDatabase.mdf** nell'elenco a discesa e quindi scegliere **Avanti.**

1. Nella pagina **Salva la stringa di connessione nel file di configurazione dell'applicazione** scegliere **Avanti.**

1. Nella pagina **Scegliere gli oggetti di** database verrà visualizzato un messaggio che indica che il database non contiene oggetti. Scegliere **Fine**.

### <a name="view-properties-of-the-data-connection"></a>Visualizzare le proprietà della connessione dati

È possibile visualizzare la stringa di connessione per il file *SampleDatabase.mdf* aprendo il Finestra Proprietà della connessione dati:

- Selezionare **Visualizza**  >  **SQL Server Esplora oggetti** per aprire la **SQL Server Esplora oggetti** predefinita. Espandere **(localdb)\MSSQLLocalDB** Databases , quindi fare clic con il pulsante destro del mouse  >   *su SampleDatabase.mdf* e **scegliere Proprietà**.

- In alternativa, è possibile **selezionare**  >  **Visualizza Esplora server**, se la finestra non è già aperta. Aprire il Finestra Proprietà espandere il nodo **Connessioni** dati, fare clic con il pulsante destro del mouse su *SampleDatabase.mdf* e quindi **scegliere Proprietà.**

  > [!TIP]
  > Se non è possibile espandere il nodo Connessioni dati o se la connessione SampleDatabase.mdf non è elencata, selezionare il pulsante Connessione **al** database nella barra degli strumenti Esplora server dati. Nella finestra **di dialogo** Aggiungi connessione verificare che sia selezionato Microsoft SQL Server File di **database** in Origine dati **e** quindi individuare e selezionare il file SampleDatabase.mdf. Completare l'aggiunta della connessione selezionando **OK.**

## <a name="create-tables-and-keys-by-using-table-designer"></a>Creare tabelle e chiavi usando Progettazione tabelle

In questa sezione verranno create due tabelle, una chiave primaria in ogni tabella e alcune righe di dati di esempio. Si creerà anche una chiave esterna per specificare il modo in cui i record in una tabella corrispondono ai record nell'altra tabella.

### <a name="create-the-customers-table"></a>Creare la tabella Customers

1. In **Esplora server** espandere il **nodo Connessioni dati** e quindi espandere il nodo **SampleDatabase.mdf.**

   Se non è possibile espandere il nodo Connessioni dati o se la connessione SampleDatabase.mdf non è elencata, selezionare il pulsante Connessione **al** database nella barra degli strumenti Esplora server dati. Nella finestra **di dialogo** Aggiungi connessione verificare che sia selezionato Microsoft SQL Server File di **database** in Origine dati **e** quindi individuare e selezionare il file SampleDatabase.mdf. Completare l'aggiunta della connessione selezionando **OK.**

2. Fare clic con il pulsante destro **del mouse su** Tabelle e scegliere Aggiungi nuova **tabella.**

   Verrà aperta Progettazione tabelle e verrà visualizzata una griglia con una riga predefinita, che rappresenta una singola colonna della tabella che si sta creando. Aggiungendo righe alla griglia, vengono aggiunte colonne alla tabella.

3. Nella griglia, aggiungere una riga per ognuna delle seguenti voci:

   |Nome colonna|Tipo di dati|Consente valori null|
   |-----------------|---------------|-----------------|
   |`CustomerID`|`nchar(5)`|False (deselezionato)|
   |`CompanyName`|`nvarchar(50)`|False (deselezionato)|
   |`ContactName`|`nvarchar (50)`|True (selezionato)|
   |`Phone`|`nvarchar (24)`|True (selezionato)|

4. Fare clic con il pulsante destro `CustomerID` del mouse sulla riga e quindi scegliere Imposta chiave **primaria**.

5. Fare clic con il pulsante destro del mouse sulla riga predefinita ( `Id` ) e quindi scegliere **Elimina.**

6. Denominare la tabella Customers aggiornando la prima riga nel riquadro dello script in modo che corrisponda all'esempio seguente:

   ```sql
   CREATE TABLE [dbo].[Customers]
   ```

   L'output dovrebbe essere simile al seguente:

   ![Progettazione tabelle](../data-tools/media/table-designer.png)

7. Nell'angolo superiore sinistro della **Progettazione tabelle** selezionare **Aggiorna.**

8. Nella finestra **di dialogo Anteprima aggiornamenti** database selezionare Aggiorna **database**.

   La tabella Customers viene creata nel file di database locale.

### <a name="create-the-orders-table"></a>Creare la tabella Orders

1. Aggiungere un'altra tabella, quindi aggiungere una riga per ogni voce nella tabella seguente:

   |Nome colonna|Tipo di dati|Consente valori null|
   |-----------------|---------------|-----------------|
   |`OrderID`|`int`|False (deselezionato)|
   |`CustomerID`|`nchar(5)`|False (deselezionato)|
   |`OrderDate`|`datetime`|True (selezionato)|
   |`OrderQuantity`|`int`|True (selezionato)|

2. Impostare **OrderID** come chiave primaria e quindi eliminare la riga predefinita.

3. Denominare la tabella Orders aggiornando la prima riga nel riquadro dello script in modo che corrisponda all'esempio seguente:

   ```sql
   CREATE TABLE [dbo].[Orders]
   ```

4. Nell'angolo superiore sinistro del **Progettazione tabelle** selezionare **Aggiorna.**

5. Nella finestra **di dialogo Anteprima aggiornamenti** database selezionare Aggiorna **database**.

   La tabella Orders viene creata nel file di database locale. Se si espande il **nodo** Tabelle in Esplora server, vengono visualizzati le due tabelle:

   ![Nodo Tabelle espanso in Esplora server](media/server-explorer-tables-node.png)

### <a name="create-a-foreign-key"></a>Creare una chiave esterna

1. Nel riquadro contestuale sul lato destro della griglia Progettazione tabelle per la tabella Orders fare clic con il pulsante destro del mouse su **Chiavi** esterne e scegliere **Aggiungi nuova chiave esterna.**

   ![Aggiungere una chiave esterna in Progettazione tabelle in Visual Studio](../data-tools/media/add-foreign-key.png)

2. Nella casella di testo visualizzata sostituire il testo **ToTable** con **Customers**.

3. Nel riquadro T-SQL aggiornare l'ultima riga in modo che corrisponda all'esempio seguente:

   ```sql
   CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
   ```

4. Nell'angolo superiore sinistro del **Progettazione tabelle** selezionare **Aggiorna.**

5. Nella finestra **di dialogo Anteprima aggiornamenti** database selezionare Aggiorna **database**.

   Viene creata la chiave esterna.

## <a name="populate-the-tables-with-data"></a>Popolare le tabelle con i dati

1. In **Esplora server** o **SQL Server Esplora oggetti** espandere il nodo per il database di esempio.

2. Aprire il menu di scelta rapida **per il nodo** Tabelle , selezionare **Aggiorna**, quindi espandere il **nodo** Tabelle .

3. Aprire il menu di scelta rapida per la tabella Customers e quindi **selezionare Mostra dati tabella**.

4. Aggiungere i dati desiderati per alcuni clienti.

    È possibile specificare tutti i cinque caratteri desiderati come ID cliente, ma sceglierne almeno uno da ricordare in un secondo momento per l'utilizzo in questa procedura.

5. Aprire il menu di scelta rapida per la tabella Orders e quindi **selezionare Mostra dati tabella**.

6. Aggiungere dati per alcuni ordini.

    > [!IMPORTANT]
    > Assicurarsi che tutti gli ID ordine e le quantità degli ordini siano numeri interi e che ogni ID cliente corrisponda a un valore specificato nella **colonna CustomerID** della tabella Customers.

7. Sulla barra dei menu selezionare **File**  >  **Salva tutto.**

## <a name="see-also"></a>Vedi anche

- [Accesso ai dati in Visual Studio](accessing-data-in-visual-studio.md)
