---
title: Salvare i dati in un database (più tabelle) | Microsoft Docs
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
- updating datasets, walkthroughs
- data [Visual Studio], saving
- saving data, walkthroughs
- data [Visual Studio], updating
ms.assetid: 7ebe03da-ce8c-4cbc-bac0-a2fde4ae4d07
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c5c4d5fc73660c97bcb69957a93d2ff08f64e31c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655453"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Salvare dati in un database (a più tabelle)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uno degli scenari più comuni nello sviluppo di applicazioni è la visualizzazione di dati in un form in un'applicazione Windows, la modifica dei dati e l'invio dei dati aggiornati al database. In questa procedura dettagliata viene creato un form in cui sono visualizzati i dati di due tabelle correlate e viene illustrato come modificare i record e salvare le modifiche nel database. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind.

 È possibile salvare nel database i dati dell'applicazione chiamando il metodo `Update` di un oggetto TableAdapter. Quando si trascinano le tabelle dalla finestra **origini dati** in un form, il codice necessario per salvare i dati viene aggiunto automaticamente. Qualsiasi tabella aggiuntiva aggiunta a un modulo richiede l'aggiunta manuale di questo codice. In questa procedura dettagliata viene descritto come aggiungere il codice per salvare gli aggiornamenti da più di una tabella.

> [!NOTE]
> Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti**. Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

 Le attività illustrate nella procedura dettagliata sono le seguenti:

- Creazione di un nuovo progetto di **applicazione Windows** .

- Creazione e configurazione di un'origine dati nell'applicazione con la [Configurazione guidata origine dati](https://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).

- Impostazione dei controlli degli elementi nella [finestra Origini dati](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

- Creazione di controlli associati a dati con il trascinamento di elementi dalla finestra **Origini dati** nel form.

- Modifica di alcuni record in ogni tabella del set di dati.

- Modifica del codice per inviare nuovamente al database i dati aggiornati nel set di dati.

## <a name="prerequisites"></a>Prerequisites
 Per completare questa procedura dettagliata, è necessario:

- Accedere al database di esempio Northwind.

## <a name="create-the-windows-application"></a>Creare l'applicazione Windows
 Il primo passaggio consiste nel creare un' **applicazione Windows**. L'assegnazione di un nome al progetto è facoltativa durante questo passaggio, ma verrà assegnato un nome perché si prevede di salvarlo in un secondo momento.

#### <a name="to-create-the-new-windows-application-project"></a>Per creare il nuovo progetto di applicazione Windows

1. Scegliere Crea nuovo progetto dal menu **file** .

2. Denominare il progetto `UpdateMultipleTablesWalkthrough`.

3. Selezionare **applicazione Windows**e quindi fare clic su **OK**. Per ulteriori informazioni, vedere [applicazioni client](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     Il progetto **UpdateMultipleTablesWalkthrough** viene creato e aggiunto in **Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati
 Questo passaggio consente di creare un'origine dati dal database Northwind usando la **Configurazione guidata origine dati**. Per creare la connessione, è necessario avere accesso al database di esempio Northwind.

#### <a name="to-create-the-data-source"></a>Per creare l'origine dati

1. Scegliere**Mostra origini dati**dal menu **dati** .

2. Nella finestra **origini dati** selezionare**Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.

3. Nella schermata **scegliere un tipo di origine dati**selezionare **database**, quindi fare clic su **Avanti**.

4. Nella schermata **Seleziona connessione dati**eseguire una delle operazioni seguenti:

    - Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

         oppure

    - Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.

5. Se il database richiede una password, selezionare l'opzione per includere i dati sensibili, quindi selezionare **Avanti**.

6. Nella pagina **Salva stringa di connessione nel file di configurazione dell'applicazione**selezionare **Avanti**.

7. Nella schermata **Seleziona oggetti di database**espandere il nodo **tabelle** .

8. Selezionare le tabelle **Customers** e **Orders** e quindi fare clic su **Finish**.

     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle vengono visualizzate nella finestra **Origini dati**.

## <a name="set-the-controls-to-be-created"></a>Impostare i controlli da creare
 Per questa procedura dettagliata, i dati nella tabella `Customers` si trova in un layout **Dettagli** in cui i dati vengono visualizzati nei singoli controlli. I dati della tabella `Orders` si trova in un layout di **griglia** visualizzato in un controllo <xref:System.Windows.Forms.DataGridView>.

#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Per impostare il tipo di rilascio degli elementi della finestra Origini dati

1. Nella finestra **origini dati** espandere il nodo **Customers** .

2. Nel nodo **Customers** selezionare **Details** dall'elenco di controllo per modificare il controllo della tabella **Customers** in singoli controlli. Per ulteriori informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="create-the-data-bound-form"></a>Creare il form con associazione a dati
 È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.

#### <a name="to-create-data-bound-controls-on-the-form"></a>Per creare controlli associati a dati nel form

1. Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.

     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

2. Trascinare il nodo **Orders** correlato dalla finestra **Origini dati** in **Form1**.

    > [!NOTE]
    > Il nodo **Orders** correlato si trova sotto la colonna **Fax** ed è un nodo figlio del nodo **Customers**.

     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati OrdersTableAdapter e <xref:System.Windows.Forms.BindingSource>.

## <a name="addcode-to-update-the-database"></a>AddCode per aggiornare il database
 È possibile aggiornare il database chiamando i metodi `Update` degli oggetti TableAdapter **Customers** e **Orders**. Per impostazione predefinita, un gestore eventi per il pulsante **Salva** del <xref:System.Windows.Forms.BindingNavigator> viene aggiunto al codice del form per inviare gli aggiornamenti al database. Questa procedura modifica il codice per inviare gli aggiornamenti nell'ordine corretto. In questo modo si elimina la possibilità di generare errori di integrità referenziale. Il codice implementa anche la gestione degli errori eseguendo il wrapping della chiamata di aggiornamento in un blocco try-catch. È possibile modificare il codice per soddisfare le esigenze dell'applicazione.

> [!NOTE]
> Per maggiore chiarezza, in questa procedura dettagliata non viene utilizzata alcuna transazione. Tuttavia, se si stanno aggiornando due o più tabelle correlate, includere tutta la logica di aggiornamento all'interno di una transazione. Una transazione è un processo che garantisce che tutte le modifiche correlate a un database abbiano esito positivo prima del commit delle modifiche. Per ulteriori informazioni, vedere [transazioni e concorrenza](https://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).

#### <a name="to-add-update-logic-to-the-application"></a>Per aggiungere la logica di aggiornamento all'applicazione

1. Selezionare il pulsante **Salva** sul <xref:System.Windows.Forms.BindingNavigator>. verrà aperto l'editor di codice per il gestore dell'evento `bindingNavigatorSaveItem_Click`.

2. Sostituire il codice nel gestore eventi per chiamare i metodi `Update` degli oggetti TableAdapter correlati. Il codice seguente crea innanzitutto tre tabelle dati temporanee in cui inserire le informazioni aggiornate per ogni <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> e <xref:System.Data.DataRowState>). Gli aggiornamenti vengono quindi eseguiti nell'ordine corretto. Il codice dovrebbe essere simile al seguente:

     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]

## <a name="test-the-application"></a>Testare l'applicazione

#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione

1. Selezionare **F5**.

2. Apportare alcune modifiche ai dati di uno o più record di ogni tabella.

3. Selezionare il pulsante **Salva**.

4. Controllare i valori presenti nel database per verificare che le modifiche siano state salvate.

## <a name="next-steps"></a>Passaggi successivi
 A seconda dei requisiti dell'applicazione, è possibile eseguire diversi passaggi dopo la creazione di un form associato a dati nell'applicazione Windows. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

- Aggiunta di funzionalità di ricerca al form. Per altre informazioni, vedere [procedura: aggiungere una query con parametri a un'applicazione Windows Forms](https://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).

- Modifica dell'origine dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [procedura: modificare un set di dati](https://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).

## <a name="see-also"></a>Vedere anche
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
