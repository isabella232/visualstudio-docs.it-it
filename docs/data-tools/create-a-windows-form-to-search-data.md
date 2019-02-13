---
title: Creare un Windows Form per la ricerca di dati
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Windows Forms, searching data
- Windows Forms, displaying data
- parameters, displaying filtered data
- data [Visual Studio], parameterizing queries
- data [Visual Studio], searching
ms.assetid: 65ca79a9-7458-466c-af55-978cd24c549e
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 3c73ab24cd2b50efd26f9a5b3ac1105325345033
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945068"
---
# <a name="create-a-windows-form-to-search-data"></a>Creare un Windows Form per la ricerca di dati

Uno scenario applicativo comune prevede la visualizzazione dei dati selezionati in un form, ad esempio gli ordini per un determinato cliente o i dettagli di un ordine specifico. In questo scenario un utente immette informazioni in un form, quindi viene eseguita una query che usa come parametro l'input dell'utente. Questo significa che i dati vengono selezionati in base a una query con parametri. La query restituisce solo i dati che soddisfano i criteri immessi dall'utente. Questa procedura dettagliata illustra come creare una query che restituisca i clienti di una determinata città e come modificare l'interfaccia utente in modo che gli utenti possano immettere il nome di una città e fare clic su un pulsante per eseguire la query.

L'uso di query con parametri rende più efficiente il funzionamento dell'applicazione, consentendo al database di eseguire in modo ottimale le operazioni di filtro rapido dei record. La richiesta invece di un'intera tabella del database, il relativo trasferimento in rete e l'uso della logica dell'applicazione per trovare i record desiderati possono comportare una riduzione della velocità e dell'efficienza dell'applicazione.

È possibile aggiungere le query con parametri a qualsiasi oggetto TableAdapter e controlli per accettare i valori dei parametri ed eseguire la query, tramite il **generatore di criteri di ricerca** nella finestra di dialogo. Per aprire la finestra di dialogo, scegliere **Aggiungi query** nel menu **Dati** o da qualsiasi smart tag di TableAdapter.

Le attività illustrate nella procedura dettagliata sono le seguenti:

-   Creazione di una nuova **Windows Forms Application** progetto.

-   Creazione e configurazione dell'origine dati nell'applicazione con il **configurazione dell'origine dati** procedura guidata.

-   Impostare il tipo di rilascio degli elementi nel **Zdroje dat** finestra.

-   Creazione di controlli per la visualizzazione dei dati mediante il trascinamento di elementi dalla finestra **Origini dati** in un form.

-   Aggiunta di controlli per la visualizzazione dei dati nel form.

-   Completare la **generatore di criteri di ricerca** nella finestra di dialogo.

-   Immissione dei parametri nel form e l'esecuzione della query con parametri.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare LocalDB di SQL Server Express come parte delle **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte del **elaborazione ed archiviazione dati** carico di lavoro nel **programma di installazione di Visual Studio**.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="create-the-windows-forms-application"></a>Creare l'applicazione Windows Form

Il primo passaggio consiste nel creare un'app Windows Form. Assegnazione di un nome per il progetto è facoltativa in questo passaggio, ma è possibile assegnargli un nome qui perché è possibile salvare il progetto in un secondo momento:

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual C#**  oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Desktop di Windows**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **WindowsSearchForm**, quindi scegliere **OK**.

     Il progetto **WindowsSearchForm** viene creato e aggiunto a **Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati

Questo passaggio consente di creare un'origine dati da un database usando la **Configurazione guidata origine dati**:

1.  Per aprire la **Zdroje dat** finestra via il **Data** dal menu fare clic su **Mostra origini dati**.

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

È possibile creare i controlli associati a dati trascinando elementi dalla finestra **Origini dati** nel form:

1.  Espandere il nodo **Customers** nella finestra **Origini dati**.

2.  Trascinare il nodo **Customers** dalla finestra **Origini dati** al form.

     Sul form vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Nella barra dei componenti vengono visualizzati gli oggetti [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter, <xref:System.Windows.Forms.BindingSource> e <xref:System.Windows.Forms.BindingNavigator>.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Aggiungere la parametrizzazione (funzionalità di ricerca) per la query

È possibile aggiungere una clausola WHERE alla query originale utilizzando il **generatore di criteri di ricerca** nella finestra di dialogo:

1.  Selezionare il controllo <xref:System.Windows.Forms.DataGridView> e quindi scegliere **Aggiungi query** dal menu **Dati**.

2.  Tipo **FillByCity** nel **nuovo nome query** area di **generatore di criteri di ricerca** nella finestra di dialogo.

3.  Aggiungere `WHERE City = @City` alla query nell'area **Testo della query**.

     La query dovrebbe essere simile alla seguente:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Origini dati Access e OLE DB usano il punto interrogativo ('? ') per indicare i parametri, pertanto la clausola WHERE risulterebbe simile al seguente: `WHERE City = ?`.

4.  Fare clic su **OK** per chiudere la finestra di dialogo **Generatore di criteri per la ricerca**.

     Al form viene aggiunto un elemento **FillByCityToolStrip**.

## <a name="test-the-application"></a>Testare l'applicazione

Esecuzione dell'applicazione consente di aprire il modulo e lo rende pronto ad accettare il parametro come input:

1.  Premere **F5** per eseguire l'applicazione.

2.  Digitare **London** nella casella di testo **City**, quindi fare clic su **FillByCity**.

     La griglia dei dati viene popolata con i clienti che soddisfano i criteri. In questo esempio nella griglia dei dati vengono visualizzati solo i clienti nella cui colonna **City** è presente un valore **London**.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta terminata la creazione di un form con parametri. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

-   Aggiunta di controlli per la visualizzazione di dati correlati. Per altre informazioni, vedere [relazioni nei DataSet](relationships-in-datasets.md).

-   Modifica del set di dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
