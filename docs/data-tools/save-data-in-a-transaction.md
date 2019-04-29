---
title: 'Procedura dettagliata: Salvare i dati in una transazione'
ms.date: 09/08/2017
ms.topic: conceptual
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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: ea312ca2858a02bc8a70c3e41dbb525c9d222adc
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565717"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Procedura dettagliata: Salvare i dati in una transazione

Questa procedura dettagliata illustra come salvare i dati in una transazione usando il <xref:System.Transactions> dello spazio dei nomi. In questa procedura dettagliata, si creerà un'applicazione Windows Form. Si userà la configurazione guidata origine dati per creare un set di dati per le due tabelle nel database di esempio Northwind. Si aggiungeranno dati controlli associati a un modulo di Windows, e si modificherà il codice di BindingNavigator pulsante Salva aggiornare il database all'interno di un ambito di transazione.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel programma di installazione di Visual Studio Express LocalDB di SQL Server può essere installato come parte del **sviluppo di applicazioni desktop .NET** carico di lavoro, o come un singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte di **elaborazione ed archiviazione dati** carico di lavoro in Visual Studio Installer.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Forms Application

Il primo passaggio consiste nel creare un **Windows Forms Application**.

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **SavingDataInATransactionWalkthrough**, quindi scegliere **OK**.

     Il progetto **SavingDataInATransactionWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="create-a-database-data-source"></a>Creare un'origine dati del database

Questo passaggio Usa la **configurazione guidata origine dati** per creare un'origine dati basata sulle `Customers` e `Orders` tabelle nel database di esempio Northwind.

1. Per aprire la **Zdroje dat** finestra via il **Data** dal menu **Mostra origini dati**.

2. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Nel **scegliere un tipo di origine dati** schermata, seleziona **Database**e quindi selezionare **Next**.

4. Nel **scegliere la connessione dati** eseguire schermata una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         -oppure-

    - Selezionare **Nuova connessione** per avviare la finestra di dialogo **Aggiungi/Modifica connessione** e creare una connessione al database Northwind.

5. Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi selezionare **successivo**.

6. Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** schermata, seleziona **successivo**.

7. Nel **Scegli oggetti di Database** schermata, quindi espandere il **tabelle** nodo.

8. Selezionare il `Customers` e `Orders` tabelle e quindi selezionare **fine**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle `Customers` e `Orders` vengono visualizzate nella finestra **Origini dati**.

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form

È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.

1. Nel **Zdroje dat** finestra, espandere il **clienti** nodo.

2. Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.

   Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter`, <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

3. Trascinare i relativi **ordini** nodo (non principale **ordini** nodo, ma il nodo della tabella figlio correlata riportato di seguito il **Fax** colonna) nel form sotto la  **CustomersDataGridView**.

   Nel form verrà visualizzato un oggetto <xref:System.Windows.Forms.DataGridView>. Un' `OrdersTableAdapter` e <xref:System.Windows.Forms.BindingSource> vengono visualizzati nella barra dei componenti.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Aggiungere un riferimento all'assembly System. Transactions

Le transazioni usano lo spazio dei nomi <xref:System.Transactions>. Un riferimento di progetto all'assembly system.transactions non viene aggiunto per impostazione predefinita. Pertanto, è necessario aggiungerlo manualmente.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Per aggiungere un riferimento al file DLL System.Transactions.

1. Nel **Project** dal menu **Aggiungi riferimento**.

2. Selezionare **System. Transactions** (nelle **.NET** scheda), quindi selezionare **OK**.

     Al progetto viene aggiunto un riferimento a **System.Transactions**.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modificare il codice nel pulsante SaveItem di BindingNavigator

Per la prima tabella rilasciata nel form, viene aggiunto codice per impostazione predefinita per il `click` pulsante eventi del salvataggio il <xref:System.Windows.Forms.BindingNavigator>. È necessario aggiungere manualmente il codice per aggiornare eventuali tabelle aggiuntive. In questa procedura dettagliata è effettuare il refactoring del codice dal salvataggio di salvataggio gestore dell'evento click del pulsante. Si crea anche altri metodi per fornire funzionalità di aggiornamento specifico basata sul fatto che la riga debba essere aggiunti o eliminati.

### <a name="to-modify-the-auto-generated-save-code"></a>Per modificare il codice di salvataggio autogenerato

1. Selezionare il **salvare** pulsante il **CustomersBindingNavigator** (il pulsante con icona del disco floppy).

2. Sostituire il metodo `CustomersBindingNavigatorSaveItem_Click` con il codice seguente:

     [!code-vb[VbRaddataSaving#4](../data-tools/codesnippet/VisualBasic/save-data-in-a-transaction_1.vb)]
     [!code-csharp[VbRaddataSaving#4](../data-tools/codesnippet/CSharp/save-data-in-a-transaction_1.cs)]

L'ordine di riconciliazione delle modifiche ai dati correlati è il seguente:

- Eliminare i record figlio. (In questo caso, eliminare i record di `Orders` tabella.)

- Eliminare i record padre. (In questo caso, eliminare i record di `Customers` tabella.)

- Inserire i record padre. (In questo caso, inserire i record nella `Customers` tabella.)

- Inserire i record figlio. (In questo caso, inserire i record nella `Orders` tabella.)

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

## <a name="run-the-application"></a>Esecuzione dell'applicazione

Premere **F5** per eseguire l'applicazione.

## <a name="see-also"></a>Vedere anche

- [Procedura: salvare dati usando una transazione](../data-tools/save-data-by-using-a-transaction.md)
- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)