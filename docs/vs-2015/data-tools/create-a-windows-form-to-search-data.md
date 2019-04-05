---
title: Creare un modulo di Windows per cercare i dati | Microsoft Docs
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
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
caps.latest.revision: 31
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cd800e5d31189487689781c1f04cd82479893dfa
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966466"
---
# <a name="create-a-windows-form-to-search-data"></a>Creare un Windows Form per la ricerca di dati
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Uno scenario applicativo comune prevede la visualizzazione dei dati selezionati in un form, ad esempio gli ordini per un determinato cliente o i dettagli di un ordine specifico. In questo scenario un utente immette informazioni in un form, quindi viene eseguita una query che usa come parametro l'input dell'utente. Questo significa che i dati vengono selezionati in base a una query con parametri. La query restituisce solo i dati che soddisfano i criteri immessi dall'utente. Questa procedura dettagliata illustra come creare una query che restituisca i clienti di una determinata città e come modificare l'interfaccia utente in modo che gli utenti possano immettere il nome di una città e fare clic su un pulsante per eseguire la query.  
  
 L'uso di query con parametri rende più efficiente il funzionamento dell'applicazione, consentendo al database di eseguire in modo ottimale le operazioni di filtro rapido dei record. La richiesta invece di un'intera tabella del database, il relativo trasferimento in rete e l'uso della logica dell'applicazione per trovare i record desiderati possono comportare una riduzione della velocità e dell'efficienza dell'applicazione.  
  
 È possibile aggiungere le query con parametri a qualsiasi oggetto TableAdapter e controlli per accettare i valori dei parametri ed eseguire la query, tramite il **generatore di criteri di ricerca** nella finestra di dialogo. Per aprire la finestra di dialogo, scegliere **Aggiungi query** nel menu **Dati** o da qualsiasi smart tag di TableAdapter.  
  
 Le attività illustrate nella procedura dettagliata sono le seguenti:  
  
-   Creazione di un nuovo progetto Windows Forms Application.  
  
-   Creazione e configurazione dell'origine dati nell'applicazione con il **configurazione dell'origine dati** procedura guidata.  
  
-   Impostare il tipo di rilascio degli elementi nel **Zdroje dat** finestra.  
  
-   Creazione di controlli per la visualizzazione dei dati mediante il trascinamento di elementi dalla finestra **Origini dati** in un form.  
  
-   Aggiunta di controlli per la visualizzazione dei dati nel form.  
  
-   Completare la **generatore di criteri di ricerca** nella finestra di dialogo.  
  
-   Immissione dei parametri nel form e l'esecuzione della query con parametri.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per completare questa procedura dettagliata, è necessario:  
  
-   Accedere al database di esempio Northwind.  
  
## <a name="create-the-windows-application"></a>Creare l'applicazione di Windows  
 Il primo passaggio consiste nel creare un **applicazioni Windows**. L'assegnazione di un nome per il progetto è facoltativa in questo passaggio, ma è possibile assegnargli un nome qui perché verranno salvati in un secondo momento.  
  
#### <a name="to-create-the-new-windows-application-project"></a>Per creare il nuovo progetto Applicazione Windows  
  
1.  Dal **File** menu, creare un nuovo progetto.  
  
2.  Denominare il progetto `WindowsSearchForm`.  
  
3.  Selezionare **applicazione di Windows** e fare clic su **OK**.  
  
     Il progetto **WindowsSearchForm** viene creato e aggiunto a **Esplora soluzioni**.  
  
## <a name="create-the-data-source"></a>Creare l'origine dati  
 Questo passaggio consente di creare un'origine dati da un database utilizzando la **configurazione dell'origine dati** procedura guidata. Per creare la connessione, è necessario avere accesso al database di esempio Northwind. Per informazioni sulla configurazione di database di esempio Northwind, vedere [i database di esempio di installazione di SQL Server](../data-tools/install-sql-server-sample-databases.md).  
  
#### <a name="to-create-the-data-source"></a>Per creare l'origine dati  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  
  
2.  Nella finestra **Origini dati** selezionare **Aggiungi nuova origine dati** per avviare la **Configurazione guidata origine dati**.  
  
3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.  
  
4.  Nella pagina **Seleziona connessione dati** eseguire una delle operazioni seguenti:  
  
    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.  
  
    -   Selezionare **Nuova connessione** per aprire la finestra di dialogo **Aggiungi/Modifica connessione**.  
  
5.  Se il database in uso richiede una password, selezionare l'opzione che consente di includere dati sensibili, quindi scegliere **Avanti**.  
  
6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.  
  
7.  Espandere il nodo **Tables** nella pagina **Seleziona oggetti di database**.  
  
8.  Selezionare la tabella **Customers**, quindi fare clic su **Fine**.  
  
     L'oggetto **NorthwindDataSet** viene aggiunto al progetto e la tabella **Customers** viene visualizzata nella finestra **Origini dati**.  
  
## <a name="create-the-form"></a>Creazione di form  
 È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form.  
  
#### <a name="to-create-data-bound-controls-on-the-form"></a>Per creare controlli associati a dati nel form  
  
1.  Espandere il nodo **Customers** nella finestra **Origini dati**.  
  
2.  Trascinare il nodo **Customers** dalla finestra **Origini dati** al form.  
  
     Sul form vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.  
  
## <a name="addparameterization-search-functionality-to-the-query"></a>Addparameterization (funzionalità di ricerca) per la query  
 È possibile aggiungere una clausola WHERE alla query originale utilizzando il **generatore di criteri di ricerca** nella finestra di dialogo.  
  
#### <a name="to-create-a-parameterized-query-and-controls-to-enter-the-parameters"></a>Per creare una query con parametri e controlli per l'immissione dei parametri  
  
1.  Selezionare il controllo <xref:System.Windows.Forms.DataGridView> e quindi scegliere **Aggiungi query** dal menu **Dati**.  
  
2.  Tipo `FillByCity` nella **nuovo nome query** area il **generatore di criteri di ricerca** nella finestra di dialogo.  
  
3.  Aggiungere `WHERE City = @City` alla query nell'area **Testo della query**.  
  
     La query dovrebbe essere simile alla seguente:  
  
     `SELECT CustomerID, CompanyName, ContactName, ContactTitle, Address, City, Region, PostalCode, Country, Phone, Fax`  
  
     `FROM Customers`  
  
     `WHERE City = @City`  
  
    > [!NOTE]
    >  Origini dati Access e OLE DB usano il punto interrogativo ('? ') per indicare i parametri, pertanto la clausola WHERE risulterebbe simile al seguente: `WHERE City = ?`.  
  
4.  Fare clic su **OK** per chiudere la finestra di dialogo **Generatore di criteri per la ricerca**.  
  
     Al form viene aggiunto un elemento **FillByCityToolStrip**.  
  
## <a name="testing-the-application"></a>Test dell'applicazione  
 Quando l'applicazione viene eseguita, il form viene aperto ed è pronto ad accettare il parametro come input.  
  
#### <a name="to-test-the-application"></a>Per eseguire il test dell'applicazione  
  
1.  Premere F5 per eseguire l'applicazione.  
  
2.  Digitare **London** nella casella di testo **City**, quindi fare clic su **FillByCity**.  
  
     La griglia dei dati viene popolata con i clienti che soddisfano i criteri. In questo esempio nella griglia dei dati vengono visualizzati solo i clienti nella cui colonna **City** è presente un valore **London**.  
  
## <a name="next-steps"></a>Passaggi successivi  
 A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta terminata la creazione di un form con parametri. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:  
  
-   Aggiunta di controlli per la visualizzazione di dati correlati.  
  
-   Modifica del set di dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).  
  
## <a name="see-also"></a>Vedere anche  
 [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
