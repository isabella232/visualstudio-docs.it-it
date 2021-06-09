---
title: Aggiungere un'origine dati a un test delle prestazioni Web
description: Informazioni su come associare dati per fornire valori diversi allo stesso test, ad esempio per fornire valori diversi ai parametri di post del modulo.
ms.custom: SEO-VS-2020
ms.date: 10/03/2016
ms.topic: how-to
helpviewer_keywords:
- Web performance tests, walkthroughs
- Web performance tests, data binding (database)
ms.assetid: 2ada376d-f168-455d-9643-6acb535360c1
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.openlocfilehash: 71aa3dbf4657896093dae59451140f48f83f1622
ms.sourcegitcommit: 01a411cd7ae3488b7b979a947bca92fd296a98e9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/09/2021
ms.locfileid: "111761004"
---
# <a name="add-a-data-source-to-a-web-performance-test"></a>Aggiungere un'origine dati a un test delle prestazioni Web

Associare i dati per fornire valori diversi nello stesso test, ad esempio, per fornire valori diversi ai parametri Post 'per i form.

[!INCLUDE [web-load-test-deprecated](includes/web-load-test-deprecated.md)]

![Data binding a un test prestazioni Web](../test/media/web_test_databinding_conceptual.png)

Verrà usata un'applicazione ASP.NET di esempio, contenente tre pagine *ASPX*: la pagina predefinita, una pagina Red e una pagina Blue. La pagina predefinita contiene un pulsante di opzione per la scelta tra rosso e blu e un pulsante Submit. Le altre due pagine *ASPX* sono molto semplici. Una include un'etichetta denominata Red e l'altra un'etichetta denominata Blue. Quando si sceglie Submit nella pagina predefinita, viene visualizzata una delle altre pagine. È possibile scaricare l'esempio di [ColorWebApp](https://code.msdn.microsoft.com/Sample-ColorWebApp-76ff7506) o usare la propria applicazione Web.

![Esecuzione dell'applicazione Web da testare](../test/media/web_test_databinding_runwebapp.png)

La soluzione deve inoltre includere un test delle prestazioni Web che scorra le pagine dell'applicazione Web.

![Soluzione con test prestazioni Web](../test/media/web_test_databinding_solution.png)

## <a name="create-a-sql-database"></a>Creare un database SQL

::: moniker range="vs-2017"

1. Se Visual Studio Enterprise non è disponibile, scaricarlo dalla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download).

2. Creare un database SQL.

     ![Aggiungere un nuovo database SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Creare un progetto di database.

     ![Creare il nuovo progetto dal database](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Aggiungere una tabella al progetto di database.

     ![Aggiungere una nuova tabella al progetto di database](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Aggiungere campi alla tabella.

     ![Aggiungere campi alla tabella](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Pubblicare il progetto di database.

     ![Pubblicare il progetto di database in Esplora soluzioni](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Aggiungere dati ai campi.

     ![Aggiungere dati ai campi](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

::: moniker range=">=vs-2019"

1. Se Visual Studio Enterprise non è disponibile, scaricarlo dalla pagina dei [download di Visual Studio](https://visualstudio.microsoft.com/downloads).

2. Creare un database SQL.

     ![Aggiungere un nuovo database SQL](../test/media/web_test_databinding_sql_addnewdb.png)

3. Creare un progetto di database.

     ![Creare il nuovo progetto dal database](../test/media/web_test_databinding_sql_addnewdbproject.png)

4. Aggiungere una tabella al progetto di database.

     ![Aggiungere una nuova tabella al progetto di database](../test/media/web_test_databinding_sql_addnewdbtablename.png)

5. Aggiungere campi alla tabella.

     ![Aggiungere campi alla tabella](../test/media/web_test_databinding_sql_addnewdbaddfields.png)

6. Pubblicare il progetto di database.

     ![Pubblicare il progetto di database in Esplora soluzioni](../test/media/web_test_databinding_sql_addnewdbpublish.png)

7. Aggiungere dati ai campi.

     ![Aggiungere dati ai campi](../test/media/web_test_databinding_sql_addnewfieldsadddata.png)

::: moniker-end

## <a name="add-the-data-source"></a>Aggiungere l'origine dati

1. Aggiungere un'origine dati.

     ![Aggiungere un'origine dati al test prestazioni Web](../test/media/web_test_databinding_sql_adddatasource.png)

2. Scegliere il tipo di origine dati e denominarlo.

     ![Denominare l'origine database](../test/media/web_test_databinding_sql_adddatasourcedialog.png)

3. Creare una connessione.

     ![Scegliere la nuova connessione](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

     Immettere i dettagli della connessione.

     ![Immettere le proprietà di connessione del database SQL](../test/media/web_test_databinding_sql_adddatasourcedialogconnection.png)

4. Selezionare la tabella che si desidera utilizzare per il test.

     ![Aggiungere la tabella Color all'origine dati](../test/media/web_test_databinding_sql_adddatasourcedialogaddtable.png)

     La tabella è associata al test.

     ![Nodo Origini dati aggiunto al test prestazioni Web](../test/media/web_test_databinding_requestnodeadded_mdb.png)

5. Salvare il test.

## <a name="bind-the-data"></a>Associare i dati

1. Associare il campo **ColorName**.

     ![Associare il campo ColorName al valore RadioButtonList1](../test/media/web_test_databinding_sql_binddatasource.png)

2. Aprire il file *Local.testsettings* in **Esplora soluzione** e selezionare l'opzione **Una esecuzione per riga origine dati**.

     ![Modificare il file di impostazioni di test.](../test/media/web_test_databinding_sql_testsettings.png)

3. Salvare il test delle prestazioni Web.

## <a name="run-the-test-with-the-data"></a>Eseguire il test con i dati

1. Eseguire il test.

     ![Eseguire il test prestazioni Web per verificare l'associazione](../test/media/web_test_databinding_sql_runtest.png)

     Le due esecuzioni vengono visualizzate per ogni riga di dati. L'esecuzione 1 invia una richiesta per la pagina *Red.aspx* e l'esecuzione 2 invia una richiesta per la pagina *Blue.aspx*.

     ![Risultati delle esecuzioni dei test](../test/media/web_test_databinding_sql_runresults.png)

     Quando si esegue l'associazione a un'origine dati, è possibile violare la regola dell'URL di risposta predefinito. In questo caso l'errore nell'esecuzione 2 è causato dalla regola che prevede la pagina *Red.aspx* dalla registrazione originale del test, ma il data binding ora la indirizza alla pagina *Blue.aspx*.

2. Correggere l'errore di convalida eliminando la regola di convalida dell'**URL di risposta** ed eseguendo nuovamente il test.

     ![Eliminare la regola di convalida dell'URL di risposta](../test/media/web_test_databinding_sql_deleteresponseurl.png)

     Il test delle prestazioni Web ha ora esito positivo tramite l'associazione dati.

     ![Test superati usando l'associazione dati](../test/media/web_test_databinding_sql_deleteresponseurlrunresults.png)

## <a name="q--a"></a>Domande e risposte

### <a name="q-what-databases-can-i-use-as-a-data-source"></a>D. Quali database è possibile utilizzare come origine dati?

**R.** È possibile usare:

- Microsoft SQL Azure.

- Qualsiasi versione di Microsoft SQL Server 2005 o versione successiva.

- File di database di Microsoft SQL Server (incluso SQL Express).

- Microsoft ODBC.

- File di Microsoft Access che utilizzano il provider .NET Framework per OLE DB.

- Oracle 7.3, 8i, 9i o 10g.

### <a name="q-how-do-i-use-a-comma-separated-value-csv-text-file-as-a-data-source"></a>D. È possibile utilizzare un file di testo CSV (con valori delimitati da virgole) come origine dati?

**R.** Ecco come fare:

1. Creare una cartella per organizzare gli elementi del database dei progetti e aggiungere un elemento.

     ![Aggiungere un nuovo elemento alla cartella Dati](../test/media/web_test_databinding_foldernewitem.png)

2. Creare un file di testo.

     ![Denominare il nuovo file ColorData.csv](../test/media/web_test_databinding_foldernewitemtextfile.png)

3. Modificare il file di testo e aggiungere quanto segue:

    ```text
    ColorId, ColorName
    0,Red
    1,Blue
    ```

4. Usare i passaggi descritti in [Aggiungere l'origine dati](#add-the-data-source), ma scegliere File CSV come origine dati.

     ![Immettere un nome e scegliere un file CSV](../test/media/web_test_databinding_adddatasourcedialog.png)

### <a name="q-what-if-my-existing-csv-file-does-not-contain-column-headers"></a>D. Quali operazioni si devono eseguire se il file CSV esistente non contiene intestazioni di colonna?

**R.** Se non è possibile aggiungere intestazioni di colonna, usare un file di descrizione dello schema per gestire il file CSV come database.

1. Aggiungere un nuovo file di testo denominato *schema.ini*.

     ![Aggiungere un file schema.ini](../test/media/web_test_databinding_schemafile.png)

2. Modificare il file *schema.ini* per aggiungere le informazioni che descrivono la struttura dei dati. Ad esempio, un file di schema in cui è descritto il file CSV potrebbe essere simile al seguente:

    ```text
    [testdata.csv]
    ColNameHeader=False
    ```

3. Aggiungere un'origine dati al test.

     ![Aggiungere un'origine dati al test prestazioni Web](../test/media/web_test_databinding_sql_adddatasource.png)

4. Se si usa un file *schema.ini*, scegliere **Database** (non File CSV) come origine dati e denominarlo.

     ![Aggiungere l'origine dati di un database](../test/media/web_test_databinding_adddatasourcecolortext.png)

5. Crea una nuova connessione.

     ![Scegliere la nuova connessione](../test/media/web_test_databinding_sql_adddatasourcedialogconnectionnew.png)

6. Selezionare il provider di dati .NET Framework per OLE DB.

     ![Selezionare il provider di dati OLE DB di .NET Framework](../test/media/web_test_databinding_adddatasourcecolortext2.png)

7. Scegliere **Avanzate**.

     ![Scegliere Avanzate](../test/media/web_test_databinding_advanced.png)

8. Per la proprietà Provider, selezionare Microsoft.Jet.OLEDB.4.0, quindi impostare **Proprietà estese** su Text;HDR=NO.

     ![Applicare le proprietà avanzate](../test/media/web_test_databinding_advancedproperties.png)

9. Digitare il nome della cartella contenente il file di schema e verificare la connessione.

     ![Immettere il percorso della cartella dei dati](../test/media/web_test_databinding_adddatasourcecolortext5.png)

10. Selezionare il file CVS che si desidera utilizzare.

     ![Selezionare il file di testo](../test/media/web_test_databinding_adddatasourcecolortext6.png)

     Al termine, il file CSV viene visualizzato come tabella.

     ![L'origine dati aggiunta al test](../test/media/web_test_databinding_adddatasourcecolortext7.png)

### <a name="q-how-do-i-use-an-xml-file-as-a-data-source"></a>D. Come si utilizza un file XML come origine dati?

**R:** Sì.

1. Creare una cartella per organizzare gli elementi del database dei progetti e aggiungere un elemento.

     ![Aggiungere un nuovo elemento alla cartella Dati](../test/media/web_test_databinding_foldernewitem.png)

2. Creare un file XML.

     ![Aggiungere il file ColorData.xml](../test/media/web_test_databinding_additemxmlfile.png)

3. Modificare il file XML e aggiungere i dati:

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <ColorData>
        <Color>
            <ColorId>0</ColorId>
            <ColorName>Red</ColorName>
        </Color>
        <Color>
            <ColorId>1</ColorId>
            <ColorName>Blue</ColorName>
        </Color>
    </ColorData>
    ```

4. Usare i passaggi descritti in [Aggiungere l'origine dati](#add-the-data-source), ma scegliere File XML come origine dati.

     ![Immettere un nome e scegliere un file XML](../test/media/web_test_databinding_adddatasourcedialogxml.png)

### <a name="q-can-i-add-data-binding-to-a-web-service-request-that-uses-soap"></a>D. È possibile aggiungere un data binding a una richiesta di servizio Web che utilizza SOAP?

**R.** Sì, è necessario modificare manualmente il codice XML SOAP.

1. Scegliere la richiesta di servizio Web nell'albero delle richieste e nella finestra Proprietà scegliere il pulsante con i puntini di sospensione (...) nella proprietà Corpo stringa.

     ![Modificare il corpo della stringa del servizio Web](../test/media/web_test_databinding_webservicerequest.png)

2. Sostituire i valori nel corpo SOAP con i valori associati ai dati usando la sintassi seguente:

    ```xml
    {{DataSourceName.TableName.ColumnName}}
    ```

    Si supponga, ad esempio, di avere il codice seguente:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>string</userName> <password>string</password> <orderID>int</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

    Questo codice può essere modificato nel modo seguente:

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <soap:Envelope xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
        <soap:Body>
            <CheckStatus xmlns="http://tempuri.org/">
                <userName>{{DataSourceName.Users.Name}}</userName> <password>{{DataSourceName.Users.Password}}</password> <orderID>{{DataSourceName.Orders.OrderID}}</orderID>
            </CheckStatus>
        </soap:Body>
    </soap:Envelope>
    ```

3. Salvare il test.
