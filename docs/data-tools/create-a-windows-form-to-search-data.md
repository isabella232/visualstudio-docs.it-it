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
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7b2a72306a3636bb5bca601f600afdaa175b4dd1
ms.sourcegitcommit: 3a11feebad45a0dd4ac45efcbfdf172fce46e1de
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39582421"
---
# <a name="create-a-windows-form-to-search-data"></a>Creare un Windows Form per la ricerca di dati

Uno scenario applicativo comune prevede la visualizzazione dei dati selezionati in un form, ad esempio gli ordini per un determinato cliente o i dettagli di un ordine specifico. In questo scenario un utente immette informazioni in un form, quindi viene eseguita una query che usa come parametro l'input dell'utente. Questo significa che i dati vengono selezionati in base a una query con parametri. La query restituisce solo i dati che soddisfano i criteri immessi dall'utente. Questa procedura dettagliata illustra come creare una query che restituisca i clienti di una determinata città e come modificare l'interfaccia utente in modo che gli utenti possano immettere il nome di una città e fare clic su un pulsante per eseguire la query.

L'uso di query con parametri rende più efficiente il funzionamento dell'applicazione, consentendo al database di eseguire in modo ottimale le operazioni di filtro rapido dei record. Al contrario, se richiesta un'intera tabella del database, trasferirlo in rete e quindi usare la logica dell'applicazione per trovare i record desiderati, l'applicazione può diventare lente e inefficiente.

È possibile aggiungere le query con parametri a qualsiasi oggetto TableAdapter e controlli per accettare i valori dei parametri ed eseguire la query, tramite il **generatore di criteri di ricerca** nella finestra di dialogo. Aprire la finestra di dialogo selezionando il **Aggiungi Query** comando le **dati** menu (o da qualsiasi oggetto TableAdapter smart tag).

Le attività illustrate nella procedura dettagliata sono le seguenti:

-   Creazione di una nuova **Windows Forms Application** progetto.

-   Creazione e configurazione dell'origine dati nell'applicazione con il **configurazione dell'origine dati** procedura guidata.

-   Impostare il tipo di rilascio degli elementi nel **Zdroje dat** finestra.

-   Creazione di controlli che visualizzano dati trascinando elementi dal **Zdroje dat** finestra in un form.

-   Aggiunta di controlli per la visualizzazione dei dati nel form.

-   Completare la **generatore di criteri di ricerca** nella finestra di dialogo.

-   Immissione dei parametri nel form e l'esecuzione della query con parametri.

## <a name="prerequisites"></a>Prerequisiti

Questa procedura dettagliata Usa SQL Server Express LocalDB e il database di esempio Northwind.

1.  Se non si dispone di SQL Server Express LocalDB, installarlo dal [pagina di download di SQL Server Express](https://www.microsoft.com/sql-server/sql-server-editions-express), o tramite il **programma di installazione di Visual Studio**. Nel **programma di installazione di Visual Studio**, è possibile installare SQL Server Express LocalDB come parte delle **elaborazione ed archiviazione dati** carico di lavoro, o come un singolo componente.

2.  Installare il database di esempio Northwind seguendo questa procedura:

    1. In Visual Studio, aprire il **Esplora oggetti di SQL Server** finestra. (Esplora oggetti di SQL Server viene installato come parte del **elaborazione ed archiviazione dati** carico di lavoro nel **programma di installazione di Visual Studio**.) Espandere la **SQL Server** nodo. Fare doppio clic sull'istanza di Local DB e selezionare **nuova Query**.

       Apre una finestra dell'editor di query.

    2. Copia il [script di Transact-SQL Northwind](https://github.com/MicrosoftDocs/visualstudio-docs/blob/master/docs/data-tools/samples/northwind.sql?raw=true) negli Appunti. Questo script T-SQL crea il database Northwind da zero e lo popola con i dati.

    3. Incollare lo script T-SQL nell'editor di query e quindi scegliere il **Execute** pulsante.

       Dopo un breve periodo di tempo, termina l'esecuzione di query e viene creato il database Northwind.

## <a name="create-the-windows-forms-application"></a>Creare l'applicazione Windows Form

Il primo passaggio consiste nel creare un'app Windows Form. Assegnazione di un nome per il progetto è facoltativa in questo passaggio, ma è possibile assegnargli un nome qui perché è possibile salvare il progetto in un secondo momento:

1. In Visual Studio sul **File** dal menu **New** > **progetto**.

2. Espandere la **Visual c#** oppure **Visual Basic** nel riquadro di sinistra, quindi selezionare **Windows Desktop**.

3. Nel riquadro centrale selezionare il **App di Windows. Forms** tipo di progetto.

4. Denominare il progetto **WindowsSearchForm**, quindi scegliere **OK**.

     Il **WindowsSearchForm** viene creato e aggiunto al progetto **Esplora soluzioni**.

## <a name="create-the-data-source"></a>Creare l'origine dati

Questo passaggio consente di creare un'origine dati da un database utilizzando la **configurazione dell'origine dati** guidata:

1.  Scegliere **Mostra origini dati** dal menu **Dati**.

2.  Nel **Zdroje dat** finestra, seleziona **Aggiungi nuova origine dati** per avviare la **configurazione dell'origine dati** procedura guidata.

3.  Selezionare **Database** nella pagina **Scegliere un tipo di origine dati** e scegliere **Avanti**.

4.  Nel **scegliere la connessione dati** eseguire pagina una delle operazioni seguenti:

    -   Selezionare la connessione dati al database di esempio Northwind nell'elenco a discesa, se presente.

    -   Selezionare **nuova connessione** per avviare la **Aggiungi/Modifica connessione** nella finestra di dialogo.

5.  Se il database richiede una password, selezionare l'opzione per includere dati sensibili e quindi fare clic su **successivo**.

6.  Nel **Salva stringa di connessione nel file di configurazione dell'applicazione** pagina, fare clic su **successivo**.

7.  Nel **Scegli oggetti di Database** , espandere il **tabelle** nodo.

8.  Selezionare il **clienti** tabella e quindi fare clic su **fine**.

     Il **NorthwindDataSet** viene aggiunto al progetto e il **clienti** inclusa nella tabella il **Zdroje dat** finestra.

## <a name="create-the-form"></a>Creazione di form

È possibile creare i controlli con associazione a dati trascinando elementi dal **Zdroje dat** finestra nei form:

1.  Espandere la **clienti** nodo il **Zdroje dat** finestra.

2.  Trascinare il **clienti** nodo dalle **Zdroje dat** finestra al form.

     Sul form vengono visualizzati un oggetto <xref:System.Windows.Forms.DataGridView> e un controllo Toolstrip (<xref:System.Windows.Forms.BindingNavigator>) per lo spostamento all'interno dei record. Oggetto [NorthwindDataSet](../data-tools/dataset-tools-in-visual-studio.md), CustomersTableAdapter <xref:System.Windows.Forms.BindingSource>, e <xref:System.Windows.Forms.BindingNavigator> vengono visualizzati nella barra dei componenti.

## <a name="add-parameterization-search-functionality-to-the-query"></a>Aggiungere la parametrizzazione (funzionalità di ricerca) per la query

È possibile aggiungere una clausola WHERE alla query originale utilizzando il **generatore di criteri di ricerca** nella finestra di dialogo:

1.  Selezionare il <xref:System.Windows.Forms.DataGridView> controllo e quindi scegliere **Aggiungi Query** sul **dati** menu.

2.  Tipo **FillByCity** nel **nuovo nome query** area di **generatore di criteri di ricerca** nella finestra di dialogo.

3.  Aggiungere `WHERE City = @City` alla query nella **testo della Query** area.

     La query dovrebbe essere simile alla seguente:

     ```sql
     SELECT CustomerID, CompanyName, ContactName, ContactTitle,
          Address, City, Region, PostalCode, Country, Phone, Fax
     FROM Customers
     WHERE City = @City
     ```

    > [!NOTE]
    > Origini dati Access e OLE DB usano il punto interrogativo ('? ') per indicare i parametri, pertanto la clausola WHERE risulterebbe simile al seguente: `WHERE City = ?`.

4.  Fare clic su **OK** per chiudere la **generatore di criteri di ricerca** nella finestra di dialogo.

     Oggetto **FillByCityToolStrip** viene aggiunto al form.

## <a name="test-the-application"></a>Testare l'applicazione

Esecuzione dell'applicazione consente di aprire il modulo e lo rende pronto ad accettare il parametro come input:

1.  Premere **F5** per eseguire l'applicazione.

2.  Tipo di **Londra** nel **City** casella di testo e quindi fare clic su **FillByCity**.

     La griglia dei dati viene popolata con i clienti che soddisfano i criteri. In questo esempio, la griglia dati vengono visualizzati solo i clienti che hanno un valore di **Londra** nel loro **City** colonna.

## <a name="next-steps"></a>Passaggi successivi

A seconda dei requisiti dell'applicazione, si potranno eseguire diverse operazioni una volta terminata la creazione di un form con parametri. È possibile apportare alcuni miglioramenti a questa procedura dettagliata, tra cui:

-   Aggiunta di controlli per la visualizzazione di dati correlati. Per altre informazioni, vedere [relazioni nei DataSet](relationships-in-datasets.md).

-   Modifica del set di dati per aggiungere o rimuovere oggetti di database. Per altre informazioni, vedere [Create and configure datasets](../data-tools/create-and-configure-datasets-in-visual-studio.md) (Creare e configurare set di dati).

## <a name="see-also"></a>Vedere anche

- [Associare controlli Windows Form ai dati in Visual Studio](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)