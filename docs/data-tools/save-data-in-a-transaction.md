---
title: 'Procedura dettagliata: Salvare dati in una transazione'
description: In questa procedura dettagliata, vedere come salvare i dati in una transazione usando lo spazio dei nomi System. Transactions in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/08/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 62175e33949b2c6311fba8e9255b237cd8b43e01
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99858475"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Procedura dettagliata: Salvare dati in una transazione

In questa procedura dettagliata viene illustrato come salvare i dati in una transazione utilizzando lo <xref:System.Transactions> spazio dei nomi. In questa procedura dettagliata verrà creato un Windows Forms Application. Si utilizzerà la configurazione guidata origine dati per creare un set di dati per due tabelle nel database di esempio Northwind. Si aggiungono controlli con associazione a dati a un Windows Form e si modificherà il codice per il pulsante Salva di BindingNavigator per aggiornare il database all'interno di un TransactionScope.

## <a name="prerequisites"></a>Prerequisiti

In questa procedura dettagliata vengono utilizzati SQL Server Express database locale e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express database locale, installarlo dalla [pagina di download SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express)o tramite il **programma di installazione di Visual Studio**. Nel Programma di installazione di Visual Studio SQL Server Express database locale può essere installato come parte del carico di lavoro sviluppo di applicazioni **desktop .NET** o come singolo componente.

2. Installare il database di esempio Northwind attenendosi alla procedura seguente:

    1. In Visual Studio aprire la finestra **Esplora oggetti di SQL Server** . Esplora oggetti di SQL Server viene installato come parte del carico di lavoro di **elaborazione e archiviazione dei dati** nel programma di installazione di Visual Studio. Espandere il nodo **SQL Server** . Fare clic con il pulsante destro del mouse sull'istanza del database locale e scegliere **nuova query**.

       Si apre una finestra dell'editor di query.

    2. Copiare lo [script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query, quindi scegliere il pulsante **Execute (Esegui** ).

       Dopo un breve periodo di tempo, viene completata l'esecuzione della query e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Forms Application

Il primo passaggio consiste nel creare un' **applicazione Windows Form**.

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **desktop di Windows**.

3. Nel riquadro centrale selezionare il tipo di progetto **App Windows Form** .

4. Denominare il progetto **SavingDataInATransactionWalkthrough**, quindi scegliere **OK**.

     Il progetto **SavingDataInATransactionWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="create-a-database-data-source"></a>Creare un'origine dati del database

In questo passaggio viene utilizzata la **Configurazione guidata origine dati** per creare un'origine dati basata `Customers` sulle `Orders` tabelle e nel database di esempio Northwind.

1. Per aprire la finestra **origini dati** , scegliere **Mostra origini dati** dal menu **dati** .

2. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Nella schermata **scegliere un tipo di origine dati** selezionare **database**, quindi fare clic su **Avanti**.

4. Nella schermata **Seleziona connessione dati** eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         -oppure-

    - Selezionare **Nuova connessione** per avviare la finestra di dialogo **Aggiungi/Modifica connessione** e creare una connessione al database Northwind.

5. Se il database richiede una password, selezionare l'opzione per includere i dati sensibili, quindi selezionare **Avanti**.

6. Nella schermata **Salva stringa di connessione nel file di configurazione dell'applicazione** selezionare **Avanti**.

7. Nella schermata **Seleziona oggetti di database** espandere il nodo **tabelle** .

8. Selezionare le `Customers` `Orders` tabelle e, quindi fare clic su **fine**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le `Customers` `Orders` tabelle e vengono visualizzate nella finestra **origini dati** .

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form

È possibile creare i controlli associati a dati trascinando gli elementi dalla finestra **origini dati** nel form.

1. Nella finestra **origini dati** espandere il nodo **Customers** .

2. Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.

   Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Un [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , <xref:System.Windows.Forms.BindingSource> e viene <xref:System.Windows.Forms.BindingNavigator> visualizzato nella barra dei componenti.

3. Trascinare il nodo **Orders** correlato, non il nodo **Orders** principale, ma il nodo della tabella figlio correlato al di sotto della colonna **Fax** , nel form sotto **customersDataGridView**.

   Nel form verrà visualizzato un oggetto <xref:System.Windows.Forms.DataGridView>. `OrdersTableAdapter`E <xref:System.Windows.Forms.BindingSource> vengono visualizzati nella barra dei componenti.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Aggiungere un riferimento all'assembly System. Transactions

Le transazioni usano lo spazio dei nomi <xref:System.Transactions>. Un riferimento di progetto all'assembly system.transactions non viene aggiunto per impostazione predefinita. Pertanto, è necessario aggiungerlo manualmente.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Per aggiungere un riferimento al file DLL System.Transactions.

1. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

2. Selezionare **System. Transactions** nella scheda **.NET** e quindi fare clic su **OK**.

     Al progetto viene aggiunto un riferimento a **System.Transactions**.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modificare il codice nel pulsante SaveItem di BindingNavigator

Per la prima tabella rilasciata nel form, il codice viene aggiunto per impostazione predefinita all' `click` evento del pulsante Salva in <xref:System.Windows.Forms.BindingNavigator> . È necessario aggiungere manualmente il codice per aggiornare eventuali tabelle aggiuntive. Per questa procedura dettagliata viene effettuato il refactoring del codice di salvataggio esistente dal gestore dell'evento click del pulsante Salva. Vengono inoltre creati altri metodi per fornire funzionalità di aggiornamento specifiche a seconda che la riga debba essere aggiunta o eliminata.

### <a name="to-modify-the-auto-generated-save-code"></a>Per modificare il codice di salvataggio autogenerato

1. Selezionare il pulsante **Salva** in **CustomersBindingNavigator** (il pulsante con l'icona del disco floppy).

2. Sostituire il metodo `CustomersBindingNavigatorSaveItem_Click` con il codice seguente:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

L'ordine di riconciliazione delle modifiche ai dati correlati è il seguente:

- Elimina i record figlio. (In questo caso, eliminare i record dalla `Orders` tabella).

- Elimina i record padre. (In questo caso, eliminare i record dalla `Customers` tabella).

- Inserire i record padre. (In questo caso, inserire i record nella `Customers` tabella).

- Inserire i record figlio. (In questo caso, inserire i record nella `Orders` tabella).

### <a name="to-delete-existing-orders"></a>Per eliminare gli ordini esistenti

- Aggiungere il metodo `DeleteOrders` seguente in **Form1**:

     [!code-vb[VbRaddataSaving#5](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_2.vb)]
     [!code-csharp[VbRaddataSaving#5](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_2.cs)]

### <a name="to-delete-existing-customers"></a>Per eliminare i clienti esistenti

- Aggiungere il metodo `DeleteCustomers` seguente in **Form1**:

     [!code-vb[VbRaddataSaving#6](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_3.vb)]
     [!code-csharp[VbRaddataSaving#6](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_3.cs)]

### <a name="to-add-new-customers"></a>Per aggiungere nuovi clienti

- Aggiungere il metodo `AddNewCustomers` seguente in **Form1**:

     [!code-vb[VbRaddataSaving#7](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_4.vb)]
     [!code-csharp[VbRaddataSaving#7](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_4.cs)]

### <a name="to-add-new-orders"></a>Per aggiungere nuovi ordini

- Aggiungere il metodo `AddNewOrders` seguente in **Form1**:

     [!code-vb[VbRaddataSaving#8](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_5.vb)]
     [!code-csharp[VbRaddataSaving#8](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_5.cs)]

## <a name="run-the-application"></a>Eseguire l'applicazione

Premere **F5** per eseguire l'applicazione.

## <a name="see-also"></a>Vedi anche

- [Procedura: salvare dati usando una transazione](../data-tools/save-data-by-using-a-transaction.md)
- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
