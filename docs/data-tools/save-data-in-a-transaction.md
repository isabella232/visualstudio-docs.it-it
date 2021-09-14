---
title: 'Procedura dettagliata: Salvare dati in una transazione'
description: In questa procedura dettagliata viene illustrato come salvare i dati in una transazione usando lo spazio dei nomi System.Transactions in Visual Studio.
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
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 3cc1516eb083f6446a30adba8a0973878cd99654
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631187"
---
# <a name="walkthrough-save-data-in-a-transaction"></a>Procedura dettagliata: Salvare dati in una transazione

Questa procedura dettagliata illustra come salvare i dati in una transazione usando lo spazio <xref:System.Transactions> dei nomi . In questa procedura dettagliata si creerà un'Windows Forms. Si userà la Configurazione guidata origine dati per creare un set di dati per due tabelle nel database di esempio Northwind. Si aggiungeranno controlli associati a dati a un form Windows e si modificherà il codice per il pulsante Di salvataggio di BindingNavigator per aggiornare il database all'interno di un transactionscope.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata usa SQL Server Express Local DB e il database di esempio Northwind.

1. Se non si dispone di SQL Server Express Local DB, installarlo dalla pagina di [download](https://www.microsoft.com/sql-server/sql-server-editions-express)SQL Server Express oppure tramite il Programma di installazione di Visual Studio **.** Nel Programma di installazione di Visual Studio, SQL Server Express Local DB può essere installato come parte del carico di lavoro **sviluppo di desktop .NET** o come singolo componente.

2. Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio aprire la **finestra** SQL Server Esplora oggetti. (SQL Server Esplora oggetti viene installato come parte  del carico di lavoro Archiviazione ed elaborazione dati nel Programma di installazione di Visual Studio. Espandere il **SQL Server** nodo. Fare clic con il pulsante destro del mouse Local DB'istanza di query e **scegliere Nuova query**.

       Verrà visualizzata una finestra dell'editor di query.

    2. Copiare [lo script Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere **il pulsante** Esegui.

       Dopo un breve periodo di tempo, l'esecuzione della query viene completata e viene creato il database Northwind.

## <a name="create-a-windows-forms-application"></a>Creare un'applicazione Windows Forms Application

Il primo passaggio consiste nel creare **un'Windows Forms.**

1. Nel menu **File** in Visual Studio selezionare **Nuovo** > **Progetto**.

2. Espandere **Visual C#** o **Visual Basic** nel riquadro a sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il tipo di **progetto Windows'app** Forms.

4. Assegnare al **progetto il nome SavingDataInATransactionWalkthrough** e quindi scegliere **OK.**

     Il progetto **SavingDataInATransactionWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="create-a-database-data-source"></a>Creare un'origine dati di database

Questo passaggio usa la **Configurazione guidata origine dati** per creare un'origine dati basata sulle tabelle e nel database di esempio `Customers` `Orders` Northwind.

1. Per aprire la **finestra Origini** dati, **scegliere** Mostra origini dati dal menu **Dati**.

2. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Nella schermata **Scegliere un tipo di origine dati** selezionare **Database** e quindi **Selezionare Avanti.**

4. Nella schermata **Scegliere la connessione dati** eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         -oppure-

    - Selezionare **Nuova connessione** per avviare la finestra di dialogo **Aggiungi/Modifica connessione** e creare una connessione al database Northwind.

5. Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi selezionare **Avanti.**

6. Nella schermata **Salva stringa di connessione nel file di configurazione dell'applicazione** selezionare **Avanti.**

7. Nella schermata **Scegliere gli oggetti di database** espandere il **nodo** Tabelle.

8. Selezionare le `Customers` tabelle e e quindi selezionare `Orders` **Fine**.

     **NorthwindDataSet viene** aggiunto al progetto e le tabelle `Customers` e vengono visualizzate nella finestra `Orders` **Origini** dati .

## <a name="add-controls-to-the-form"></a>Aggiungere controlli al form

È possibile creare i controlli associati a dati trascinando gli elementi dalla **finestra Origini** dati nel form.

1. Nella finestra **Origini dati** espandere il **nodo** Clienti.

2. Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.

   Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), `CustomersTableAdapter` , e vengono visualizzati nella barra dei <xref:System.Windows.Forms.BindingSource> <xref:System.Windows.Forms.BindingNavigator> componenti.

3. Trascinare il nodo **Orders** correlato (non il nodo **Orders** principale, ma il nodo tabella figlio correlato sotto la colonna **Fax)** nel form sotto **CustomersDataGridView**.

   Nel form verrà visualizzato un oggetto <xref:System.Windows.Forms.DataGridView>. E `OrdersTableAdapter` <xref:System.Windows.Forms.BindingSource> vengono visualizzati nella barra dei componenti.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Aggiungere un riferimento all'assembly System.Transactions

Le transazioni usano lo spazio dei nomi <xref:System.Transactions>. Un riferimento di progetto all'assembly system.transactions non viene aggiunto per impostazione predefinita. Pertanto, è necessario aggiungerlo manualmente.

### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Per aggiungere un riferimento al file DLL System.Transactions.

1. Scegliere **Aggiungi riferimento** dal menu **Progetto**.

2. Selezionare **System.Transactions** (nella scheda **.NET)** e quindi **selezionare OK**.

     Al progetto viene aggiunto un riferimento a **System.Transactions**.

## <a name="modify-the-code-in-the-bindingnavigators-saveitem-button"></a>Modificare il codice nel pulsante SaveItem di BindingNavigator

Per la prima tabella rilasciata nel form, il codice viene aggiunto per impostazione predefinita all'evento del pulsante `click` Salva in <xref:System.Windows.Forms.BindingNavigator> . È necessario aggiungere manualmente il codice per aggiornare eventuali tabelle aggiuntive. Per questa procedura dettagliata, il refactoring del codice di salvataggio esistente viene creato dal gestore dell'evento Click del pulsante Di salvataggio. Vengono anche creati altri metodi per fornire funzionalità di aggiornamento specifiche a seconda che la riga deve essere aggiunta o eliminata.

### <a name="to-modify-the-auto-generated-save-code"></a>Per modificare il codice di salvataggio autogenerato

1. Selezionare il **pulsante Salva** in **CustomersBindingNavigator** (il pulsante con l'icona del disco floppy).

2. Sostituire il metodo `CustomersBindingNavigatorSaveItem_Click` con il codice seguente:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet4":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet4":::

L'ordine di riconciliazione delle modifiche ai dati correlati è il seguente:

- Eliminare i record figlio. In questo caso, eliminare i record dalla `Orders` tabella.

- Eliminare i record padre. In questo caso, eliminare i record dalla `Customers` tabella.

- Inserire i record padre. In questo caso, inserire record nella `Customers` tabella.

- Inserire record figlio. In questo caso, inserire record nella `Orders` tabella.

### <a name="to-delete-existing-orders"></a>Per eliminare gli ordini esistenti

- Aggiungere il metodo `DeleteOrders` seguente in **Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet5":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet5":::

### <a name="to-delete-existing-customers"></a>Per eliminare i clienti esistenti

- Aggiungere il metodo `DeleteCustomers` seguente in **Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet6":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet6":::

### <a name="to-add-new-customers"></a>Per aggiungere nuovi clienti

- Aggiungere il metodo `AddNewCustomers` seguente in **Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet7":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet7":::

### <a name="to-add-new-orders"></a>Per aggiungere nuovi ordini

- Aggiungere il metodo `AddNewOrders` seguente in **Form1**:

     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb" id="Snippet8":::
     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs" id="Snippet8":::

## <a name="run-the-application"></a>Eseguire l'applicazione

Premere **F5 per** eseguire l'applicazione.

## <a name="see-also"></a>Vedi anche

- [Procedura: salvare dati usando una transazione](../data-tools/save-data-by-using-a-transaction.md)
- [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
