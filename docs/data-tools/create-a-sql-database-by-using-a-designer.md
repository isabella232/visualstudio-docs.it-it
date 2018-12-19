---
title: Creare un file di database e usare Progettazione tabelle
description: Esercitazione descrive come aggiungere tabelle e le chiavi esterne in un database tramite Progettazione tabelle in Visual Studio. Viene inoltre illustrato come aggiungere dati tramite l'interfaccia grafica.
ms.date: 11/03/2017
ms.topic: conceptual
helpviewer_keywords:
- database tables, creating
- database files, creating
- table designer
ms.assetid: 99c2b06f-47aa-414e-8057-a3453712fd23
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: c071daeaa1ffe10aa9de995b375e33b76b358da7
ms.sourcegitcommit: 0cdd8e8a53fb4fd5e869f07c35204419fa12783d
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2018
ms.locfileid: "53159867"
---
# <a name="create-a-database-and-add-tables-in-visual-studio"></a>Creare un database e aggiungere tabelle in Visual Studio

È possibile usare Visual Studio per creare e aggiornare un file di database locale in LocalDB di SQL Server Express. È anche possibile creare un database tramite l'esecuzione di istruzioni Transact-SQL nel **Esplora oggetti di SQL Server** finestra degli strumenti in Visual Studio. In questo argomento, si creerà un' *mdf* file e aggiungere tabelle e le chiavi utilizzando Progettazione tabelle.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario disporre di facoltativo **elaborazione ed archiviazione dati** carico di lavoro sia installato in Visual Studio. Per installarlo, aprire **programma di installazione di Visual Studio** e scegliere il **carichi di lavoro** scheda. Sotto **Web e Cloud**, scegliere **elaborazione ed archiviazione dati**. Scegliere il **Modify** pulsante per aggiungere il carico di lavoro per Visual Studio.

## <a name="create-a-project-and-a-local-database-file"></a>Creare un progetto e un file di database locale

1. Creare un progetto Windows Form denominato **SampleDatabaseWalkthrough**.

2. Nella barra dei menu, selezionare **Project** > **Aggiungi nuovo elemento**.

3. Nell'elenco dei modelli di elemento, scorrere verso il basso e selezionare **Database basato sul servizio**.

     ![Finestra di dialogo Modelli di elemento](../data-tools/media/raddata-vsitemtemplates.png)

4. Assegnare un nome del database **SampleDatabase**, quindi selezionare il **Add** pulsante.

### <a name="add-a-data-source"></a>Aggiungere un'origine dati

1. Se il **Zdroje dat** finestra non è aperta, aprirla premendo **MAIUSC**+**Alt**+**1!d** o selezione **View** > **Other Windows** > **Zdroje dat** nella barra dei menu.

1. Nel **Zdroje dat** finestra, seleziona la **Aggiungi nuova origine dati** collegamento.

   Viene avviata la **Configurazione guidata origine dati**.

1. Nel **scegliere un tipo di origine dati** pagina, scegliere **Database** e quindi scegliere **Next**.

1. Nel **scegliere un modello di Database** pagina, scegliere **successivo** per accettare il valore predefinito (set di dati).

1. Nel **Seleziona connessione dati** pagina, selezionare la **SampleDatabase. mdf** file nell'elenco a discesa elenco e quindi scegliere **Avanti**.

1. Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, scegliere **successivo**.

1. Uno di **Scegli oggetti di Database** pagina, verrà visualizzato un messaggio che indica il database che non contiene alcun oggetto. Scegliere **Fine**.

### <a name="view-properties-of-the-data-connection"></a>Visualizzare le proprietà della connessione dati

È possibile visualizzare la stringa di connessione per il *SampleDatabase. mdf* file aprendo la finestra delle proprietà della connessione dati:

- In Visual Studio, selezionare **View** > **Esplora oggetti di SQL Server** se tale finestra non è già aperta. Aprire la finestra Proprietà espandere la **connessioni dati** nodo, aprire il menu di scelta rapida *SampleDatabase. mdf*e quindi selezionando **proprietà**.

- In alternativa, è possibile selezionare **View** > **Esplora Server**, se tale finestra non è già aperta. Aprire la finestra Proprietà espandere la **connessioni dati** nodo. Aprire il menu di scelta rapida *SampleDatabase. mdf*, quindi selezionare **proprietà**.

## <a name="create-tables-and-keys-by-using-table-designer"></a>Creare tabelle e le chiavi tramite Progettazione tabelle

In questa sezione si creerà due tabelle, una chiave primaria in ogni tabella e alcune righe di dati di esempio. Si creerà inoltre una chiave esterna per specificare come i record in una tabella corrispondono ai record di altra tabella.

### <a name="create-the-customers-table"></a>Creare la tabella Customers

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

    ```sql
    CREATE TABLE [dbo].[Customers]
    ```

    Viene visualizzato un output simile al seguente:

    ![Progettazione tabelle](../data-tools/media/raddata-table-designer.png)

7. Nell'angolo superiore sinistro della **Progettazione tabelle**, selezionare la **Update** pulsante.

8. Nel **Anteprima aggiornamenti Database** finestra di dialogo, seleziona la **Update Database** pulsante.

    Le modifiche vengono salvate nel file del database locale.

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

4. Nell'angolo superiore sinistro della **Progettazione tabelle**, selezionare la **Update** pulsante.

5. Nel **Anteprima aggiornamenti Database** finestra di dialogo, seleziona la **Update Database** pulsante.

    Le modifiche vengono salvate nel file del database locale.

### <a name="create-a-foreign-key"></a>Creare una chiave esterna

1. Nel riquadro contesto sul lato destro della griglia, aprire il menu di scelta rapida **chiavi esterne**, quindi selezionare **Aggiungi nuova chiave esterna**, come illustrato di seguito.

     ![Aggiunta di una chiave esterna in Progettazione tabelle](../data-tools/media/foreignkey.png)

2. Nella casella di testo visualizzata sostituire **ToTable** con **Customers**.

3. Nel riquadro T-SQL, aggiornare l'ultima riga affinché corrisponda all'esempio seguente:

    ```sql
    CONSTRAINT [FK_Orders_Customers] FOREIGN KEY ([CustomerID]) REFERENCES [Customers]([CustomerID])
    ```

4. Nell'angolo superiore sinistro della **Progettazione tabelle**, selezionare la **Update** pulsante.

5. Nel **Anteprima aggiornamenti Database** finestra di dialogo, seleziona la **Update Database** pulsante.

    Le modifiche vengono salvate nel file del database locale.

## <a name="populate-the-tables-with-data"></a>Popolare le tabelle con dati

1. Nelle **Esplora Server** oppure **Esplora oggetti di SQL Server**, espandere il nodo per il database di esempio.

2. Aprire il menu di scelta rapida per il **tabelle** nodo, seleziona **aggiornare**, quindi espandere il **tabelle** nodo.

3. Aprire il menu di scelta rapida per la tabella Customers e quindi selezionare **Mostra dati tabella**.

4. Aggiungere i dati desiderati per alcuni clienti.

    È possibile specificare tutti i cinque caratteri desiderati come ID cliente, ma sceglierne almeno uno da ricordare in un secondo momento per l'utilizzo in questa procedura.

5. Aprire il menu di scelta rapida per la tabella Orders e quindi selezionare **Mostra dati tabella**.

6. Aggiungere i dati per alcuni ordini.

    > [!IMPORTANT]
    > Verificare che tutti gli ID ordine e le quantità di ordini siano valori Integer e che ogni ID cliente corrisponda a un valore specificato nella colonna **CustomerID** della tabella Customers.

7. Nella barra dei menu, selezionare **File** > **Salva tutto**.

## <a name="see-also"></a>Vedere anche

- [Accesso ai dati in Visual Studio](accessing-data-in-visual-studio.md)