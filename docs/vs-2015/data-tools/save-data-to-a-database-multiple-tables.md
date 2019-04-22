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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 979c476068afb3f76d4561c4d93a8c02ce4e4187
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59648302"
---
# <a name="save-data-to-a-database-multiple-tables"></a>Salvare dati in un database (a più tabelle)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Uno degli scenari più comuni nello sviluppo di applicazioni è la visualizzazione di dati in un form in un'applicazione Windows, la modifica dei dati e l'invio dei dati aggiornati al database. In questa procedura dettagliata viene creato un form in cui sono visualizzati i dati di due tabelle correlate e viene illustrato come modificare i record e salvare le modifiche nel database. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind.  
  
 È possibile salvare nel database i dati dell'applicazione chiamando il metodo `Update` di un oggetto TableAdapter. Quando si trascinano tabelle dal **Zdroje dat** finestra in un form, il codice necessario per salvare i dati viene aggiunto automaticamente. Le tabelle aggiuntive che vengono aggiunti a un form richiedono l'aggiunta manuale di questo codice. In questa procedura dettagliata viene descritto come aggiungere il codice per salvare gli aggiornamenti da più di una tabella.  
  
> [!NOTE]
>  Finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o l'edizione in uso. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di una nuova **applicazioni Windows** progetto.  
  
-   Creazione e configurazione di un'origine dati nell'applicazione con il [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f).  
  
-   Impostazione dei controlli degli elementi di [finestra Origini dati](http://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992). Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
-   Creazione di controlli associati a dati con il trascinamento di elementi dalla finestra **Origini dati** nel form.  
  
-   Modifica di alcuni record in ogni tabella nel set di dati.  
  
-   Modifica del codice per inviare nuovamente al database i dati aggiornati nel set di dati.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.
  
## <a name="create-the-windows-application"></a>Creare l'applicazione di Windows  
 Il primo passaggio consiste nel creare un **applicazioni Windows**. L'assegnazione di un nome al progetto è facoltativa durante questo passaggio, ma viene assegnato un nome perché è comunque prevista salvandolo in un secondo momento.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Per creare il nuovo progetto applicazione Windows  
  
1.  Nel **File** menu, creare un nuovo progetto.  
  
2.  Denominare il progetto `UpdateMultipleTablesWalkthrough`.  
  
3.  Selezionare **applicazione di Windows**, quindi selezionare **OK**. Per altre informazioni, vedere [le applicazioni Client](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Il progetto **UpdateMultipleTablesWalkthrough** viene creato e aggiunto in **Esplora soluzioni**.  
  
## <a name="create-the-data-source"></a>Creare l'origine dati  
 Questo passaggio consente di creare un'origine dati dal database Northwind usando la **Configurazione guidata origine dati**. Per creare la connessione, è necessario avere accesso al database di esempio Northwind.
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Nel **Data** dal menu**Mostra origini dati**.  
  
2.  Nel **Zdroje dat** finestra, seleziona**Aggiungi nuova origine dati** per avviare la **configurazione guidata origine dati**.  
  
3.  Nel **scegliere un tipo di origine dati**schermata, seleziona **Database**e quindi selezionare **Next**.  
  
4.  Nel **scegliere la connessione dati**eseguire schermata una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         -oppure-  
  
    -   Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.  
  
5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi selezionare **successivo**.  
  
6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione**, selezionare **successivo**.  
  
7.  Nel **Scegli oggetti di Database**schermata, quindi espandere il **tabelle** nodo.  
  
8.  Selezionare il **clienti** e **ordini** tabelle e quindi selezionare **fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle vengono visualizzate nella finestra **Origini dati**.  
  
## <a name="set-the-controls-to-be-created"></a>Impostare i controlli da creare  
 Per i dati in questa procedura dettagliata il `Customers` la tabella è in un **dettagli** layout in cui i dati vengono visualizzati in singoli controlli. I dati dal `Orders` tabella si trova in un **griglia** layout che viene visualizzato in un <xref:System.Windows.Forms.DataGridView> controllo.  
  
#### <a name="to-set-the-drop-type-for-the-items-in-the-data-sources-window"></a>Per impostare il tipo di rilascio degli elementi della finestra Origini dati  
  
1.  Nel **Zdroje dat** finestra, espandere il **clienti** nodo.  
  
2.  Nel **clienti** nodo, seleziona **dettagli** dall'elenco di controllo per impostare il controllo della **clienti** tabella sui singoli controlli. Per altre informazioni, vedere [impostare il controllo da creare durante il trascinamento dalla finestra Origini dei dati](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).  
  
## <a name="create-the-data-bound-form"></a>Creare il form con associazione a dati  
 È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Per creare controlli associati a dati nel form  
  
1.  Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.  
  
     Il form mostra i controlli associati a dati con etichette descrittive e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
2.  Trascinare il nodo **Orders** correlato dalla finestra **Origini dati** in **Form1**.  
  
    > [!NOTE]
    >  Il nodo **Orders** correlato si trova sotto la colonna **Fax** ed è un nodo figlio del nodo **Customers**.  
  
     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Un oggetto OrdersTableAdapter e <xref:System.Windows.Forms.BindingSource> vengono visualizzati nella barra dei componenti.  
  
## <a name="addcode-to-update-the-database"></a>Addcode per aggiornare il database  
 È possibile aggiornare il database chiamando i metodi `Update` degli oggetti TableAdapter **Customers** e **Orders**. Per impostazione predefinita, un gestore eventi per il **salvare** pulsante del<xref:System.Windows.Forms.BindingNavigator> viene aggiunto al codice del modulo per inviare aggiornamenti al database. Questa procedura consente di modificare il codice per inviare gli aggiornamenti nell'ordine corretto. Ciò elimina la possibilità di generare errori di integrità referenziale. Il codice implementa anche la gestione degli errori eseguendo il wrapping della chiamata di aggiornamento in un blocco try-catch. È possibile modificare il codice per soddisfare le esigenze dell'applicazione.  
  
> [!NOTE]
>  Per maggiore chiarezza, questa procedura dettagliata non utilizza una transazione. Tuttavia, se si stanno aggiornando due o più tabelle correlate, includere tutta la logica di aggiornamento all'interno di una transazione. Una transazione è un processo che assicura che tutte le modifiche relative a un database vengano completate prima che eventuali modifiche vanno eseguito il commit. Per altre informazioni, vedere [transazioni e concorrenza](http://msdn.microsoft.com/library/f46570de-9e50-4fe6-8710-a8c31fa8569b).  
  
#### <a name="to-add-update-logic-to-the-application"></a>Per aggiungere la logica di aggiornamento all'applicazione  
  
1.  Selezionare il **salvare** pulsante la <xref:System.Windows.Forms.BindingNavigator>. Si aprirà l'Editor di codice per il `bindingNavigatorSaveItem_Click` gestore dell'evento.  
  
2.  Sostituire il codice nel gestore eventi per chiamare i metodi `Update` degli oggetti TableAdapter correlati. Il codice seguente crea innanzitutto tre tabelle dati temporanee in cui inserire le informazioni aggiornate per ogni <xref:System.Data.DataRowState> (<xref:System.Data.DataRowState>, <xref:System.Data.DataRowState> e <xref:System.Data.DataRowState>). Gli aggiornamenti vengono quindi eseguiti nell'ordine corretto. Il codice dovrebbe essere simile al seguente:  
  
     [!code-csharp[VbRaddataSaving#10](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form4.cs#10)]
     [!code-vb[VbRaddataSaving#10](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form4.vb#10)]  
  
## <a name="test-the-application"></a>Testare l'applicazione  
  
#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione  
  
1.  Selezionare **F5**.  
  
2.  Apportare alcune modifiche ai dati di uno o più record di ogni tabella.  
  
3.  Selezionare il pulsante **Salva**.  
  
4.  Controllare i valori presenti nel database per verificare che le modifiche siano state salvate.  
  
## <a name="next-steps"></a>Passaggi successivi  
 A seconda dei requisiti dell'applicazione, sono disponibili diversi passaggi, che si potrebbe voler eseguire dopo la creazione di un form con associazione a dati nell'applicazione Windows. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:  
  
-   Aggiunta di funzionalità di ricerca al form. Per altre informazioni, vedere [Procedura: Aggiungere una Query con parametri in una Windows Forms Application](http://msdn.microsoft.com/library/13db4ad3-56b9-4a0b-b3a5-6a4ff84d4416).  
  
-   Modifica dell'origine dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [Procedura: Modificare un set di dati](http://msdn.microsoft.com/library/f2dade5f-9c7a-4ddb-96a8-e0a39e50bfd3).  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
