---
title: Creazione di un file di database e utilizzo di progettazione tabelle
description: Esercitazione che descrive come aggiungere tabelle e chiavi esterne a un database usando Progettazione tabelle in Visual Studio. Viene inoltre illustrato come aggiungere dati tramite l'interfaccia grafica.
ms.date: 09/19/2019
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 595b8ea35799effd36e4a8599c61b3ab42efb940
ms.sourcegitcommit: a1e899248adaf104697fa7dea32a36e69e9cc119
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/20/2019
ms.locfileid: "71159912"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Creazione di un database e aggiunta di tabelle in Visual Studio

È possibile utilizzare Visual Studio per creare e aggiornare un file di database locale in SQL Server Express database locale. È inoltre possibile creare un database eseguendo istruzioni Transact-SQL nella finestra degli strumenti **Esplora oggetti di SQL Server** in Visual Studio. In questo argomento si creerà un file con *estensione MDF* e si aggiungeranno tabelle e chiavi usando il progettazione tabelle.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, saranno necessari i carichi di lavoro sviluppo di applicazioni **desktop .NET** e **archiviazione dati e elaborazione** in Visual Studio. Per installarli, aprire **programma di installazione di Visual Studio** e scegliere **modifica** (o **altre** > **modifiche**) accanto alla versione di Visual Studio che si desidera modificare.

## <a name="create-a-project-and-a-local-database-file"></a>Creare un progetto e un file di database locale

1. Creare un nuovo progetto di **App Windows Forms** e denominarlo **SampleDatabaseWalkthrough**.

2. Nella barra dei menu selezionare **progetto** > **Aggiungi nuovo elemento**.

3. Nell'elenco dei modelli di elemento scorrere verso il basso e selezionare **database basato su servizi**.

   ![Finestra di dialogo Modelli di elemento](../data-tools/media/raddata-vsitemtemplates.png)

4. Denominare il database **SampleDatabase**, quindi fare clic su **Aggiungi**.

### <a name="add-a-data-source"></a>Aggiungere un'origine dati

1. Se la finestra **origini dati** non è aperta, aprirla premendo **MAIUSC**+**ALT**+**D** o selezionando **Visualizza** > **altre** > **origini dati** di Windows in barra dei menu.

1. Nella finestra **origini dati** selezionare **Aggiungi nuova origine dati**.

   ![Aggiungere una nuova origine dati in Visual Studio](media/add-new-data-source.png)

   Viene avviata la **Configurazione guidata origine dati**.

1. Nella pagina **scegliere un tipo di origine dati** scegliere **database** , quindi fare clic su **Avanti**.

1. Nella pagina **scegliere un modello di database** fare clic su **Avanti** per accettare il valore predefinito (set di dati).

1. Nella pagina **Seleziona connessione dati** selezionare il file **SampleDatabase. MDF** nell'elenco a discesa, quindi scegliere **Avanti**.

1. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione** scegliere **Avanti**.

1. Nella pagina **Seleziona oggetti di database** viene visualizzato un messaggio che indica che il database non contiene oggetti. Scegliere **Fine**.

### <a name="view-properties-of-the-data-connection"></a>Visualizzare le proprietà della connessione dati

È possibile visualizzare la stringa di connessione per il file *SampleDatabase. MDF* aprendo il finestra proprietà della connessione dati:

- Selezionare **Visualizza** > **Esplora oggetti di SQL Server** per aprire la finestra di **Esplora oggetti di SQL Server** . Espandere **(local DB) \MSSQLLocalDB** > **databases**, quindi fare clic con il pulsante destro del mouse su *SampleDatabase. MDF* e scegliere **Proprietà**.

- In alternativa, è possibile selezionare **Visualizza** > **Esplora server**, se tale finestra non è già aperta. Aprire il Finestra Proprietà espandendo il nodo **connessioni dati** , facendo clic con il pulsante destro del mouse su *SampleDatabase. MDF*e quindi scegliendo **proprietà**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Creare tabelle e chiavi utilizzando Progettazione tabelle

In questa sezione verranno create due tabelle, una chiave primaria in ogni tabella e alcune righe di dati di esempio. Verrà inoltre creata una chiave esterna per specificare il modo in cui i record di una tabella corrispondono ai record dell'altra tabella.

### <a name="create-the-customers-table"></a>Creare la tabella Customers

1. In **Esplora server**espandere il nodo **connessioni dati** , quindi espandere il nodo **SampleDatabase. MDF** .

2. Fare clic con il pulsante destro del mouse su **tabelle** e scegliere **Aggiungi nuova tabella**.

   Il Progettazione tabelle viene aperto e viene visualizzata una griglia con una riga predefinita, che rappresenta una singola colonna della tabella che si sta creando. Aggiungendo righe alla griglia, vengono aggiunte colonne alla tabella.

3. Nella griglia, aggiungere una riga per ognuna delle seguenti voci:

   |Nome colonna|Tipo di dati|Consente valori null|
   |-----------------|---------------|-----------------|
   |`CustomerID`|`nchar(5)`|False (deselezionato)|
   |`CompanyName`|`nvarchar(50)`|False (deselezionato)|
   |`ContactName`|`nvarchar (50)`|True (selezionato)|
   |`Phone`|`nvarchar (24)`|True (selezionato)|

4. Fare clic con il pulsante `CustomerID` destro del mouse sulla riga e quindi scegliere **Imposta chiave primaria**.

5. Fare clic con il pulsante destro del mouse`Id`sulla riga predefinita (), quindi scegliere **Elimina**.

6. Denominare la tabella Customers aggiornando la prima riga nel riquadro dello script in modo che corrisponda all'esempio seguente:

   ```sql
   CREATE TABLE [dbo].[Customers]
   ```

   Viene visualizzato un output simile al seguente:

   ![Progettazione tabelle](../data-tools/media/table-designer.png)

7. Nell'angolo in alto a sinistra di **Progettazione tabelle**selezionare **Aggiorna**.

8. Nella finestra di dialogo **Anteprima aggiornamenti database** selezionare **Aggiorna database**.

   La tabella Customers viene creata nel file di database locale.

### <a name="create-the-orders-table"></a>Creazione della tabella Orders

1. Aggiungere un'altra tabella, quindi aggiungere una riga per ogni voce nella tabella seguente:

   |Nome colonna|Tipo di dati|Consente valori null|
   |-----------------|---------------|-----------------|
   |`OrderID`|`int`|False (deselezionato)|
   |`CustomerID`|`nchar(5)`|False (deselezionato)|
   |`OrderDate`|`datetime`|True (selezionato)|
   |`OrderQuantity`|`int`|True (selezionato)|

2. Impostare **OrderID** come chiave primaria, quindi eliminare la riga predefinita.

3. Denominare la tabella Orders aggiornando la prima riga nel riquadro dello script in modo che corrisponda all'esempio seguente:

   ```sql
   CREATE TABLE [dbo].[Orders]
   ```

4. Nell'angolo superiore sinistro del **Progettazione tabelle**selezionare **Aggiorna**.

5. Nella finestra di dialogo **Anteprima aggiornamenti database** selezionare **Aggiorna database**.

   La tabella Orders viene creata nel file di database locale. Se si espande il nodo **tabelle** in Esplora server, vengono visualizzate le due tabelle seguenti:

   ![Nodo tabelle espanso in Esplora server](media/server-explorer-tables-node.png)

### <a name="create-a-foreign-key"></a>Creare una chiave esterna

1. Nel riquadro del contesto sul lato destro della griglia Progettazione tabelle per la tabella Orders, fare clic con il pulsante destro del mouse su **chiavi esterne** e scegliere **Aggiungi nuova chiave esterna**.

   ![Aggiungere una chiave esterna in Progettazione tabelle in Visual Studio](../data-tools/media/add-foreign-key.png)

2. Nella casella di testo visualizzata sostituire il testo **ToTable** con **Customers**.

3. Nel riquadro T-SQL aggiornare l'ultima riga in modo che corrisponda all'esempio seguente:

   ```sql
   CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
   ```

4. Nell'angolo superiore sinistro del **Progettazione tabelle**selezionare **Aggiorna**.

5. Nella finestra di dialogo **Anteprima aggiornamenti database** selezionare **Aggiorna database**.

   Viene creata la chiave esterna.

## <a name="populate-the-tables-with-data"></a>Popola le tabelle con i dati

1. In **Esplora server** o **Esplora oggetti di SQL Server**espandere il nodo per il database di esempio.

2. Aprire il menu di scelta rapida per il nodo **tabelle** , selezionare **Aggiorna**, quindi espandere il nodo **tabelle** .

3. Aprire il menu di scelta rapida per la tabella Customers, quindi selezionare **Mostra dati tabella**.

4. Aggiungere i dati desiderati ad alcuni clienti.

    È possibile specificare tutti i cinque caratteri desiderati come ID cliente, ma sceglierne almeno uno da ricordare in un secondo momento per l'utilizzo in questa procedura.

5. Aprire il menu di scelta rapida per la tabella Orders, quindi selezionare **Mostra dati tabella**.

6. Aggiungere dati per alcuni ordini.

    > [!IMPORTANT]
    > Verificare che tutti gli ID ordine e le quantità di ordini siano valori Integer e che ogni ID cliente corrisponda a un valore specificato nella colonna **CustomerID** della tabella Customers.

7. Nella barra dei menu selezionare **file** > **Salva tutto**.

## <a name="see-also"></a>Vedere anche

- [Accesso ai dati in Visual Studio](accessing-data-in-visual-studio.md)
