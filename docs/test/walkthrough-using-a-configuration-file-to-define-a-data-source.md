---
title: Usare un file di configurazione per definire l'origine dati
description: Informazioni su come usare un'origine dati definita in un file app.config per gli unit test, a partire dalla creazione di un file app.config che definisce un'origine dati.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- configuration files [Visual Studio ALM], defining data sources
- unit tests, walkthrough
- data sources, defining with configuration files
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
ms.openlocfilehash: 425eb19e516dc166c041203bd6139ee9f953d6b5b5feb32df94ceb49870a6c01
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121384561"
---
# <a name="walkthrough-using-a-configuration-file-to-define-a-data-source"></a>Procedura dettagliata: Uso di un file di configurazione per definire un'origine dati

Questa procedura dettagliata illustra come usare un'origine dati definita in un file *app.config* per gli unit test. Viene spiegato come creare un file *app.config* che definisce un'origine dati che può essere usata dalla classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>. Le attività incluse nella procedura dettagliata sono le seguenti:

- Creazione di un file *app.config*.

- Definizione di una sezione di configurazione personalizzata.

- Definizione di stringhe di connessione.

- Definizione di origini dati.

- Accesso alle origini dati tramite la classe <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute>.

## <a name="prerequisites"></a>Prerequisiti

Per completare questa procedura dettagliata, è necessario:

- Visual Studio Enterprise

- Microsoft Access o Microsoft Excel per fornire dati per almeno uno dei metodi di test.

- Soluzione Visual Studio contenente un progetto di test.

## <a name="add-an-appconfig-file-to-the-project"></a>Aggiungere un file app.config al progetto

1. Se per il progetto di test esiste già un file *app.config*, passare a [Definire una sezione di configurazione personalizzata](#define-a-custom-configuration-section).

2. Fare clic con il pulsante destro del mouse sul progetto di test in **Esplora soluzioni** e quindi selezionare **Aggiungi** > **Nuovo elemento**.

     Verrà visualizzata la finestra **Aggiungi nuovo elemento**.

3. Selezionare il modello **File di configurazione dell'applicazione** e fare clic su **Aggiungi**.

## <a name="define-a-custom-configuration-section"></a>Definire una sezione di configurazione personalizzata

Esaminare il file *app.config*. Il file contiene almeno la dichiarazione XML e un elemento radice.

### <a name="to-add-the-custom-configuration-section-to-the-appconfig-file"></a>Per aggiungere la sezione di configurazione personalizzata nel file app. config

1. L'elemento radice di *app.config* deve essere l'elemento **configuration**. Creare un elemento **configSections** all'interno dell'elemento **configuration**. **configSections** deve essere il primo elemento nel file *app.config*.

2. All'interno dell'elemento **configSections** creare un elemento **section**.

3. Nell'elemento **section** aggiungere un attributo denominato `name` e assegnare all'attributo il valore `microsoft.visualstudio.testtools`. Aggiungere un altro attributo denominato `type` e assegnare il valore `Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions`.

L'elemento **section** dovrebbe essere simile al seguente:

```xml
<section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
```

> [!NOTE]
> Il nome dell'assembly deve corrispondere alla versione in uso.

## <a name="define-connection-strings"></a>Definire le stringhe di connessione

Le stringhe di connessione definiscono informazioni specifiche del provider per l'accesso alle origini dati. Le stringhe di connessione definite nei file di configurazione forniscono informazioni sui provider di dati riutilizzabili nell'ambito di un'applicazione. In questa sezione vengono create due stringhe di connessione che verranno usate dalle origini dati definite nella sezione di configurazione personalizzata.

### <a name="to-define-connection-strings"></a>Per definire le stringhe di connessione

1. Dopo l'elemento **configSections** creare un elemento **connectionStrings**.

2. All'interno dell'elemento **connectionStrings** creare due elementi **add**.

3. Nel primo elemento **add** creare i seguenti attributi e valori per una connessione a un database di Microsoft Access:

|Attributo|Valori|
|-|------------|
|`name`|`"MyJetConn"`|
|`connectionString`|`"Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;"`|
|`providerName`|`"System.Data.OleDb"`|

Nel secondo elemento **add** creare i seguenti attributi e valori per una connessione a un foglio di calcolo di Microsoft Excel:

|Attributo|Valori|
|-|-|
|`name`|`"MyExcelConn"`|
|`connectionString`|`"Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5"`|
|`providerName`|`"System.Data.Odbc"`|

L'elemento **connectionStrings** dovrebbe essere simile al seguente:

```xml
<connectionStrings>
    <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
    <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
</connectionStrings>
```

## <a name="define-data-sources"></a>Definire le origini dati

La sezione relativa alle origini dati contiene quattro attributi usati dal motore di test per recuperare i dati da un'origine dati.

- `name` definisce l'identità usata da <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> per specificare l'origine dati da usare.

- `connectionString` identifica la stringa di connessione creata nella sezione Definire le stringhe di connessione precedente.

- `dataTableName` definisce la tabella o il foglio contenente i dati da usare nel test.

- `dataAccessMethod` definisce la tecnica per l'accesso ai valori dei dati nell'origine dati.

In questa sezione vengono definite due origini dati da usare in uno unit test.

### <a name="to-define-data-sources"></a>Per definire le origini dati

1. Dopo l'elemento **connectionStrings**, creare un elemento **microsoft.visualstudio.testtools**. Questa sezione è stata creata in Definire una sezione di configurazione personalizzata.

2. All'interno dell'elemento **microsoft.visualstudio.testtools** creare un elemento **dataSources**.

3. All'interno dell'elemento **dataSources** creare due elementi **add**.

4. Nel primo elemento **add** creare i seguenti attributi e valori per un'origine dati di Microsoft Access:

|Attributo|Valori|
|-|------------|
|`name`|`"MyJetDataSource"`|
|`connectionString`|`"MyJetConn"`|
|`dataTableName`|`"MyDataTable"`|
|`dataAccessMethod`|`"Sequential"`|

Nel secondo elemento **add** creare i seguenti attributi e valori per un'origine dati di Microsoft Excel:

|Attributo|Valori|
|-|-|
|`Name`|`"MyExcelDataSource"`|
|`connectionString`|`"MyExcelConn"`|
|`dataTableName`|`"Sheet1$"`|
|`dataAccessMethod`|`"Sequential"`|

L'elemento **microsoft.visualstudio.testtools** dovrebbe essere simile al seguente:

```xml
<microsoft.visualstudio.testtools>
    <dataSources>
        <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
        <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
    </dataSources>
</microsoft.visualstudio.testtools>
```

Il file *app.config* finale dovrebbe essere simile al seguente:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
    <configSections>
        <section name="microsoft.visualstudio.testtools" type="Microsoft.VisualStudio.TestTools.UnitTesting.TestConfigurationSection, Microsoft.VisualStudio.TestPlatform.TestFramework.Extensions" />
    </configSections>
    <connectionStrings>
        <add name="MyJetConn" connectionString="Provider=Microsoft.Jet.OLEDB.4.0; Data Source=C:\testdatasource.accdb; Persist Security Info=False;" providerName="System.Data.OleDb" />
        <add name="MyExcelConn" connectionString="Dsn=Excel Files;dbq=data.xlsx;defaultdir=.\; driverid=790;maxbuffersize=2048;pagetimeout=5" providerName="System.Data.Odbc" />
    </connectionStrings>
    <microsoft.visualstudio.testtools>
        <dataSources>
            <add name="MyJetDataSource" connectionString="MyJetConn" dataTableName="MyDataTable" dataAccessMethod="Sequential"/>
            <add name="MyExcelDataSource" connectionString="MyExcelConn" dataTableName="Sheet1$" dataAccessMethod="Sequential"/>
        </dataSources>
    </microsoft.visualstudio.testtools>
</configuration>
```

## <a name="create-a-unit-test-that-uses-data-sources-defined-in-appconfig"></a>Creare uno unit test che usa le origini dati definite in app.config

Ora che è stato definito un file *app.config*, si creerà uno unit test che usa i dati che si trovano nelle origini dati definite nel file *app. config*. In questa sezione verranno eseguite le operazioni seguenti:

- Creare le origini dati presenti nel file *app.config*.

- Usare le origini dati in due metodi di test che confrontano i valori in ciascuna origine dati.

### <a name="to-create-a-microsoft-access-data-source"></a>Per creare un'origine dati di Microsoft Access

1. Creare un database di Microsoft Access denominato *testdatasource.accdb*.

2. Creare una tabella e denominarla `MyDataTable` in *testdatasource.accdb*.

3. Creare due campi in `MyDataTable` denominati `Arg1` e `Arg2` usando il tipo di dati `Number`.

4. Aggiungere cinque entità a `MyDataTable` con i valori seguenti per `Arg1` e `Arg2`, rispettivamente: (10,50), (3,2), (6,0), (0,8) e (12312,1000).

5. Salvare e chiudere il database.

6. Cambiare la stringa di connessione in modo che punti al percorso del database. Cambiare il valore di `Data Source` in modo da riflettere il percorso del database.

### <a name="to-create-a-microsoft-excel-data-source"></a>Per creare un'origine dati di Microsoft Excel

1. Creare un foglio di calcolo di Microsoft Excel denominato *data.xlsx*.

2. Creare un foglio denominato `Sheet1` se non è già presente in *data.xlsx*.

3. Creare due intestazioni di colonna e assegnare loro i nomi `Val1` e `Val2` in `Sheet1`.

4. Aggiungere cinque entità a `Sheet1` con i valori seguenti per `Val1` e `Val2`, rispettivamente: (1,1), (2,2), (3,3), (4,4) e (5,0).

5. Salvare e chiudere il foglio di calcolo.

6. Cambiare la stringa di connessione in modo che punti al percorso del foglio di calcolo. Cambiare il valore di `dbq` in modo da riflettere il percorso del foglio di calcolo.

### <a name="to-create-a-unit-test-using-the-appconfig-data-sources"></a>Per creare uno unit test usando le origini dati in app.config

1. Aggiungere uno unit test al progetto di test.

2. Sostituire il contenuto generato automaticamente dello unit test con il codice seguente:

    ```csharp
    using System;
    using Microsoft.VisualStudio.TestTools.UnitTesting;

    namespace TestProject1
    {
         [TestClass]
        public class UnitTest1
        {
            private TestContext context;

            public TestContext TestContext
            {
                get { return context; }
                set { context = value; }
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\testdatasource.accdb")]
            [DataSource("MyJetDataSource")]
            public void MyTestMethod()
            {
                int a = Int32.Parse(context.DataRow["Arg1"].ToString());
                int b = Int32.Parse(context.DataRow["Arg2"].ToString());
                Assert.AreNotEqual(a, b, "A value was equal.");
            }

            [TestMethod()]
            [DeploymentItem("MyTestProject\\data.xlsx")]
            [DataSource("MyExcelDataSource")]
            public void MyTestMethod2()
            {
                Assert.AreEqual(context.DataRow["Val1"], context.DataRow["Val2"]);
            }
        }
    }
    ```

3. Esaminare gli attributi DataSource. Si notino i nomi delle impostazioni nel file *app.config*.

4. Compilare la soluzione ed eseguire i test MyTestMethod e MyTestMethod2.

> [!IMPORTANT]
> Distribuire gli elementi come origini dati in modo che siano accessibili al test nella directory di distribuzione.

## <a name="see-also"></a>Vedi anche

- [Eseguire unit test del codice](../test/unit-test-your-code.md)
- [Procedura: Creare uno unit test basato sui dati](../test/how-to-create-a-data-driven-unit-test.md)
