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
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 07bd9e469d090ffb97e166ce943397b51aedd497
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59647675"
---
# <a name="save-data-in-a-transaction"></a>Salvare i dati in una transazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Questa procedura dettagliata illustra come salvare i dati in una transazione usando il <xref:System.Transactions> dello spazio dei nomi. Questo esempio usa le tabelle `Customers` e `Orders` del database di esempio Northwind.  
  
## <a name="prerequisites"></a>Prerequisiti  
 La procedura dettagliata richiede l'accesso al database di esempio Northwind.
  
## <a name="create-a-windows-application"></a>Creare un'applicazione Windows  
 Il primo passaggio consiste nel creare un **applicazioni Windows**.  
  
#### <a name="to-create-the-new-windows-project"></a>Per creare il nuovo progetto Windows  
  
1.  In Visual Studio sul **File** menu, creare un nuovo **progetto**.  
  
2.  Denominare il progetto **SavingDataInATransactionWalkthrough**.  
  
3.  Selezionare **applicazione di Windows**, quindi selezionare **OK**. Per altre informazioni, vedere [le applicazioni Client](http://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).  
  
     Il progetto **SavingDataInATransactionWalkthrough** viene creato e aggiunto a **Esplora soluzioni**.  
  
## <a name="create-a-database-data-source"></a>Creare un'origine dati del database  
 Questo passaggio Usa la [configurazione guidata origine dati](http://msdn.microsoft.com/library/c4df7de5-5da0-4064-940c-761dd6d9e28f) per creare un'origine dati basata sulle `Customers` e `Orders` tabelle nel database di esempio Northwind.  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Nel **Data** dal menu**Mostra origini dati**.  
  
2.  Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Nel **scegliere un tipo di origine dati**schermata, seleziona **Database**e quindi selezionare **Next**.  
  
4.  Nel **scegliere la connessione dati**eseguire schermata una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
         -oppure-  
  
    -   Selezionare **Nuova connessione** per avviare la finestra di dialogo **Aggiungi/Modifica connessione** e creare una connessione al database Northwind.  
  
5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi selezionare **successivo**.  
  
6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** schermata, seleziona **successivo**.  
  
7.  Nel **Scegli oggetti di Database** schermata, quindi espandere il **tabelle** nodo.  
  
8.  Selezionare il `Customers` e `Orders` tabelle e quindi selezionare **fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e le tabelle `Customers` e `Orders` vengono visualizzate nella finestra **Origini dati**.  
  
## <a name="addcontrols-to-the-form"></a>Addcontrols al form  
 È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.  
  
#### <a name="to-create-data-bound-controls-on-the-windows-form"></a>Per creare dati associati a controlli nel form di Windows  
  
-   Nel **Zdroje dat** finestra, espandere il **clienti** nodo.  
  
-   Trascinare il nodo **Customers** principale dalla finestra **Origini dati** in **Form1**.  
  
     Nel form vengono visualizzati un controllo <xref:System.Windows.Forms.DataGridView> e un controllo ToolStrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
-   Trascinare i relativi **ordini** nodo (non principale **ordini** nodo, ma il nodo della tabella figlio correlata riportato di seguito il **Fax** colonna) nel form sotto la  **CustomersDataGridView**.  
  
     Nel form verrà visualizzato un oggetto <xref:System.Windows.Forms.DataGridView>. Un oggetto OrdersTableAdapter e <xref:System.Windows.Forms.BindingSource> vengono visualizzati nella barra dei componenti.  
  
## <a name="add-a-reference-to-the-systemtransactions-assembly"></a>Aggiungere un riferimento all'assembly System. Transactions  
 Le transazioni usano lo spazio dei nomi <xref:System.Transactions>. Un riferimento progetto all'assembly System. Transactions non viene aggiunto per impostazione predefinita, pertanto è necessario aggiungerlo manualmente.  
  
#### <a name="to-add-a-reference-to-the-systemtransactions-dll-file"></a>Per aggiungere un riferimento al file DLL System.Transactions.  
  
1.  Nel **Project** dal menu**Aggiungi riferimento**.  
  
2.  Selezionare **System. Transactions**(nelle **.NET** scheda), quindi selezionare **OK**.  
  
     Al progetto viene aggiunto un riferimento a **System.Transactions**.  
  
## <a name="modifythe-code-in-the-bindingnavigators-saveitem-button"></a>Codice Modifythe nel pulsante SaveItem di BindingNavigator  
 Per la prima tabella rilasciata nel form, viene aggiunto codice per impostazione predefinita per il `click` pulsante eventi del salvataggio il <xref:System.Windows.Forms.BindingNavigator>. È necessario aggiungere manualmente il codice per aggiornare eventuali tabelle aggiuntive. In questa procedura dettagliata è effettuare il refactoring del codice dal salvataggio di salvataggio gestore dell'evento click del pulsante. Si crea anche altri metodi per fornire funzionalità di aggiornamento specifico basata sul fatto che la riga debba essere aggiunti o eliminati.  
  
#### <a name="to-modify-the-auto-generated-save-code"></a>Per modificare il codice di salvataggio autogenerato  
  
1. Selezionare il **salvare** pulsante il **CustomersBindingNavigator** (il pulsante con icona del disco floppy).  
  
2. Sostituire il metodo `CustomersBindingNavigatorSaveItem_Click` con il codice seguente:  
  
    [!code-csharp[VbRaddataSaving#4](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#4)]
    [!code-vb[VbRaddataSaving#4](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#4)]  
  
   L'ordine di riconciliazione delle modifiche ai dati correlati è il seguente:  
  
-   Eliminare i record figlio. (In questo caso, eliminare i record di `Orders` tabella.)  
  
-   Eliminare i record padre. (In questo caso, eliminare i record di `Customers` tabella.)  
  
-   Inserire i record padre. (In questo caso, inserire i record nella `Customers` tabella.)  
  
-   Inserire i record figlio. (In questo caso, inserire i record nella `Orders` tabella.)  
  
#### <a name="to-delete-existing-orders"></a>Per eliminare gli ordini esistenti  
  
-   Aggiungere il metodo `DeleteOrders` seguente in **Form1**:  
  
     [!code-csharp[VbRaddataSaving#5](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#5)]
     [!code-vb[VbRaddataSaving#5](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#5)]  
  
#### <a name="to-delete-existing-customers"></a>Per eliminare i clienti esistenti  
  
-   Aggiungere il metodo `DeleteCustomers` seguente in **Form1**:  
  
     [!code-csharp[VbRaddataSaving#6](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#6)]
     [!code-vb[VbRaddataSaving#6](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#6)]  
  
#### <a name="to-add-new-customers"></a>Per aggiungere nuovi clienti  
  
-   Aggiungere il metodo `AddNewCustomers` seguente in **Form1**:  
  
     [!code-csharp[VbRaddataSaving#7](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#7)]
     [!code-vb[VbRaddataSaving#7](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#7)]  
  
#### <a name="to-add-new-orders"></a>Per aggiungere nuovi ordini  
  
-   Aggiungere il metodo `AddNewOrders` seguente in **Form1**:  
  
     [!code-csharp[VbRaddataSaving#8](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataSaving/CS/Form2.cs#8)]
     [!code-vb[VbRaddataSaving#8](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataSaving/VB/Form2.vb#8)]  
  
## <a name="run-the-application"></a>Esecuzione dell'applicazione  
  
#### <a name="to-run-the-application"></a>Per eseguire l'applicazione  
  
-   Selezionare **F5** per eseguire l'applicazione.  
  
## <a name="see-also"></a>Vedere anche  
 [Salvare i dati di nuovo nel database](../data-tools/save-data-back-to-the-database.md)
