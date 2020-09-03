---
title: Salvare i dati in una transazione | Microsoft Docs
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
- System.Transactions namespace
- data [Visual Studio], saving in a transaction
- transactions, saving data
- Transactions namespace
- saving data
ms.assetid: 80260118-08bc-4b37-bfe5-9422ee7a1e4e
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b30f51da001c62166a97c954b1416e35fd8b540f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72671085"
---
# <a name="save-data-in-a-transaction"></a>Salvare i dati in una transazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In questa procedura dettagliata viene illustrato come salvare i dati in una transazione utilizzando lo <xref:System.Transactions> spazio dei nomi. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind.

## <a name="prerequisites"></a>Prerequisiti
 La procedura dettagliata richiede l'accesso al database di esempio Northwind.

## <a name="create-a-windows-application"></a>Creare un'applicazione Windows
 Il primo passaggio consiste nel creare un' **applicazione Windows**.

#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows

1. In Visual Studio, nel menu **file** , creare un nuovo **progetto**.

2. Denominare il progetto **SavingDataInATransactionWalkthrough**.

3. Selezionare **applicazione Windows**e quindi fare clic su **OK**. Per ulteriori informazioni, vedere [applicazioni client](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Il progetto **SavingDataInATransactionWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="create-a-database-data-source"></a>Creare un'origine dati del database
 In questo passaggio viene utilizzata la [Configurazione guidata origine dati](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) per creare un'origine dati basata `Customers` sulle `Orders` tabelle e nel database di esempio Northwind.

#### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Scegliere**Mostra origini dati**dal menu **dati** .

2. Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Nella schermata **scegliere un tipo di origine dati**selezionare **database**, quindi fare clic su **Avanti**.

4. Nella schermata **Seleziona connessione dati**eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         -oppure-

    - Selezionare **Nuova connessione** per avviare la finestra di dialogo **Aggiungi/Modifica connessione** e creare una connessione al database Northwind.

5. Se il database richiede una password, selezionare l'opzione per includere i dati sensibili, quindi selezionare **Avanti**.

6. Nella schermata **Salva stringa di connessione nel file di configurazione dell'applicazione** selezionare **Avanti**.

7. Nella schermata **Seleziona oggetti di database** espandere il nodo **tabelle** .

8. Selezionare le `Customers` `Orders` tabelle e, quindi fare clic su **fine**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le `Customers` `Orders` tabelle e vengono visualizzate nella finestra **origini dati** .

## <a name="addcontrols-to-the-form"></a>Addcontrols al form
 È possibile creare i controlli associati a dati trascinando gli elementi dalla finestra **origini dati** nel form.

#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Per creare controlli associati a dati in Windows Form

- Nella finestra **origini dati** espandere il nodo **Customers** .

- Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.

     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

- Trascinare il nodo **Orders** correlato, non il nodo **Orders** principale, ma il nodo della tabella figlio correlato al di sotto della colonna **Fax** , nel form sotto **customersDataGridView**.

     Nel form verrà visualizzato un oggetto <xref:System.Windows.Forms.DataGridView>. Un OrdersTableAdapter e <xref:System.Windows.Forms.BindingSource> vengono visualizzati nella barra dei componenti.

## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Aggiungere un riferimento all'assembly System. Transactions
 Le transazioni usano lo spazio dei nomi <xref:System.Transactions>. Un riferimento di progetto all'assembly System. Transactions non viene aggiunto per impostazione predefinita, pertanto è necessario aggiungerlo manualmente.

#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Per aggiungere un riferimento al file DLL System.Transactions.

1. Scegliere**Aggiungi riferimento**dal menu **progetto** .

2. Selezionare **System. Transactions**nella scheda **.NET** e quindi fare clic su **OK**.

     Al progetto viene aggiunto un riferimento a **System.Transactions**.

## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Codice Modifythe nel pulsante SaveItem di BindingNavigator
 Per la prima tabella rilasciata nel form, il codice viene aggiunto per impostazione predefinita all' `click` evento del pulsante Salva in <xref:System.Windows.Forms.BindingNavigator> . È necessario aggiungere manualmente il codice per aggiornare eventuali tabelle aggiuntive. Per questa procedura dettagliata viene effettuato il refactoring del codice di salvataggio esistente dal gestore dell'evento click del pulsante Salva. Vengono inoltre creati altri metodi per fornire funzionalità di aggiornamento specifiche a seconda che la riga debba essere aggiunta o eliminata.

#### <a name="to-modify-the-auto-generated-save-code"></a>Per modificare il codice di salvataggio autogenerato

1. Selezionare il pulsante **Salva** in **CustomersBindingNavigator** (il pulsante con l'icona del disco floppy).

2. Sostituire il metodo `CustomersBindingNavigatorSaveItem_Click` con il codice seguente:

    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]

   L'ordine di riconciliazione delle modifiche ai dati correlati è il seguente:

- Elimina i record figlio. (In questo caso, eliminare i record dalla `Orders` tabella).

- Elimina i record padre. (In questo caso, eliminare i record dalla `Customers` tabella).

- Inserire i record padre. (In questo caso, inserire i record nella `Customers` tabella).

- Inserire i record figlio. (In questo caso, inserire i record nella `Orders` tabella).

#### <a name="to-delete-existing-orders"></a>Per eliminare gli ordini esistenti

- Aggiungere il metodo `DeleteOrders` seguente in **Form1**:

     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]

#### <a name="to-delete-existing-customers"></a>Per eliminare i clienti esistenti

- Aggiungere il metodo `DeleteCustomers` seguente in **Form1**:

     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]

#### <a name="to-add-new-customers"></a>Per aggiungere nuovi clienti

- Aggiungere il metodo `AddNewCustomers` seguente in **Form1**:

     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]

#### <a name="to-add-new-orders"></a>Per aggiungere nuovi ordini

- Aggiungere il metodo `AddNewOrders` seguente in **Form1**:

     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]

## <a name="run-the-application"></a>Eseguire l'applicazione

#### <a name="to-run-the-application"></a>Per eseguire l'applicazione

- Selezionare **F5** per eseguire l'applicazione.

## <a name="see-also"></a>Vedere anche
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
