---
title: Creare uno unit test basato sui dati
description: Informazioni su come usare microsoft unit test framework per il codice gestito per configurare un metodo unit test per recuperare valori da un'origine dati.
ms.custom: SEO-VS-2020
ms.date: 05/08/2019
ms.topic: how-to
f1_keywords:
- vs.test.testresults.unittest.datadriven
- vs.test.testresults.unittest.datadriven.failure
helpviewer_keywords:
- unit tests, running
- unit tests, data-driven
- data-driven unit tests
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-test
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: d7bcea924cd571e24003bcb66373862fdd0c7ef1
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122139985"
---
# <a name="how-to-create-a-data-driven-unit-test"></a>Procedura: Creare un'istanza guidata unit test

È possibile usare il framework unit test Microsoft per il codice gestito per impostare un metodo di unit test per recuperare i valori da un'origine dati. Il metodo viene eseguito in successione per ogni riga nell'origine dati, rendendo più semplice testare una un'ampia varietà di input con un singolo metodo.

La creazione di uno unit test basato sui dati prevede i passaggi seguenti:

1. Creare un'origine dati che contiene i valori usati nel metodo di test. L'origine dati può essere di qualsiasi tipo registrato nel computer che esegue il test.

2. Aggiungere un campo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext> privato e una proprietà `TestContext` pubblica alla classe di test.

3. Creare un metodo di unit test e aggiungere un attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute> al metodo.

4. Usare la proprietà <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A> dell'indicizzatore per recuperare i valori da usare in un test.

## <a name="the-method-under-test"></a>Metodo sottoposto a test

Come esempio, si supponga di avere:

1. Una soluzione denominata `MyBank` che accetta ed elabora transazioni per diversi tipi di account.

2. Un progetto in `MyBank` denominato `BankDb`, che gestisce le transazioni per gli account.

3. Una classe denominata `Maths` nel progetto `BankDb`, che esegue le funzioni matematiche per garantire che tutte le transazioni siano vantaggiose per la banca.

4. Un progetto di unit test denominato `BankDbTests`, per testare il comportamento del componente `BankDb`.

5. Una classe di unit test denominata `MathsTests`, per verificare il comportamento della classe `Maths`.

Verrà testato un metodo in `Maths` che somma due numeri interi con un ciclo:

```csharp
public int AddIntegers(int first, int second)
{
    int sum = first;
    for( int i = 0; i < second; i++)
    {
        sum += 1;
    }
    return sum;
}
```

## <a name="create-a-data-source"></a>Creare un'origine dati

Per testare il metodo `AddIntegers`, creiamo un'origine dati che specifica un intervallo di valori per i parametri e la somma restituita prevista. Nell'esempio verrà creato un database Sql Compact denominato `MathsData` e una tabella denominata `AddIntegersData` che contiene i nomi di colonna e i valori seguenti

|FirstNumber|SecondNumber|Sum|
|-|------------------|-|
|0|1|1|
|1|1|2|
|2|-3|-1|

## <a name="add-a-testcontext-to-the-test-class"></a>Aggiungere un oggetto TestContext alla classe di test

Il framework unit test crea un oggetto `TestContext` per archiviare le informazioni sull'origine dati per un test basato sui dati. Il framework imposta quindi l'oggetto come valore della proprietà `TestContext` creata.

```csharp
private TestContext testContextInstance;
public TestContext TestContext
{
    get { return testContextInstance; }
    set { testContextInstance = value; }
}
```

Nel metodo di test si accede ai dati tramite la proprietà dell'indicizzatore `DataRow` di `TestContext`.

> [!NOTE]
> .NET core non supporta l'attributo [DataSource](xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute). Se si tenta di accedere ai dati di test in questo modo in un progetto di unit test .NET Core o per la piattaforma UWP, verrà visualizzato un errore simile a **"'TestContext' non contiene una definizione per 'DataRow' e non è stato trovato alcun metodo di estensione accessibile 'DataRow' che accetta un primo argomento di tipo 'TestContext'. Probabilmente manca una direttiva using o un riferimento all'assembly"**.

## <a name="write-the-test-method"></a>Scrivere il metodo di test

Il metodo di test per `AddIntegers` è piuttosto semplice. Per ogni riga nell'origine dati, chiamare `AddIntegers` con i valori della colonna **FirstNumber** e **SecondNumber** come parametri e verificare il valore restituito rispetto al valore della colonna **Sum**:

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0; Data Source=C:\Data\MathsData.sdf;", "Numbers")]
[TestMethod()]
public void AddIntegers_FromDataSourceTest()
{
    var target = new Maths();

    // Access the data
    int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
    int y = Convert.ToInt32(TestContext.DataRow["SecondNumber"]);
    int expected = Convert.ToInt32(TestContext.DataRow["Sum"]);
    int actual = target.IntegerMethod(x, y);
    Assert.AreEqual(expected, actual,
        "x:<{0}> y:<{1}>",
        new object[] {x, y});
}
```

Il metodo `Assert` include un messaggio che visualizza i valori `x` e `y` di un'iterazione non riuscita. Per impostazione predefinita, i valori dichiarati `expected` e `actual` sono già inclusi nei dettagli di un test non riuscito.

### <a name="specify-the-datasourceattribute"></a>Specificare DataSourceAttribute

L'attributo `DataSource` specifica la stringa di connessione per l'origine dati e il nome della tabella usata nel metodo di test. Le informazioni esatte nella stringa di connessione variano a seconda del tipo di origine dati in uso. In questo esempio è stato usato un database SqlServerCe.

```csharp
[DataSource(@"Provider=Microsoft.SqlServerCe.Client.4.0;Data Source=C:\Data\MathsData.sdf", "AddIntegersData")]
```

L'attributo DataSource dispone di tre costruttori.

```csharp
[DataSource(dataSourceSettingName)]
```

Un costruttore con un solo parametro usa le informazioni di connessione archiviate nel file *app.config* per la soluzione. Il nome dell'elemento XML nel file di configurazione che specifica le informazioni di connessione è *dataSourceSettingsName*.

L'uso di un *file app.config* consente di modificare il percorso dell'origine dati senza apportare modifiche allo unit test. Per informazioni su come creare e usare un file *app.config*, vedere [Procedura dettagliata: Uso di un file di configurazione per definire un'origine dati](../test/walkthrough-using-a-configuration-file-to-define-a-data-source.md)

```csharp
[DataSource(connectionString, tableName)]
```

Il costruttore `DataSource` con due parametri specifica la stringa di connessione per l'origine dati e il nome della tabella che contiene i dati per il metodo di test.

Le stringhe di connessione variano a seconda del tipo di origine dati, ma devono contenere un elemento Provider che specifica il nome invariante del provider di dati.

```csharp
[DataSource(
    dataProvider,
    connectionString,
    tableName,
    dataAccessMethod
    )]
```

### <a name="use-testcontextdatarow-to-access-the-data"></a>Usare TestContext.DataRow per l'accesso ai dati

Per accedere ai dati nella tabella `AddIntegersData`, usare l'indicizzatore `TestContext.DataRow`. `DataRow` è un oggetto <xref:System.Data.DataRow>, pertanto i valori delle colonne vengono recuperati in base all'indice o ai nomi delle colonne. Poiché i valori vengono restituiti come oggetti, convertirli nel tipo appropriato:

```csharp
int x = Convert.ToInt32(TestContext.DataRow["FirstNumber"]);
```

## <a name="run-the-test-and-view-results"></a>Eseguire il test e visualizzare i risultati

Al termine della scrittura di un metodo di test, compilare il progetto di test. Il metodo di test viene visualizzato in **Esplora test** nel gruppo **Test non eseguiti**. Quando si eseguono, si scrivono e si rieseguono i test, **Esplora test** visualizza i risultati nei gruppi **Test non superati**, **Test superati** e **Test non eseguiti**. È possibile scegliere **Esegui tutto** per eseguire tutti i test oppure **scegliere Esegui** per scegliere un subset di test da eseguire.

La barra dei risultati dei test nella parte superiore di **Esplora test** viene animata durante l'esecuzione dei test. Al termine del test, la barra diventa verde se tutti i test sono stati superati oppure rossa se almeno uno dei test ha avuto esito negativo. Nel riquadro dei dettagli nella parte inferiore della finestra **Esplora test** appare un riepilogo dell'esecuzione dei test. Selezionare un test per visualizzarne i dettagli nel riquadro inferiore.

> [!NOTE]
> Viene visualizzato un risultato per ogni riga di dati e anche un risultato di riepilogo. Se il test è stato superato in ogni riga di dati, l'esecuzione di riepilogo visualizza **Superato**. Se il test non è stato superato in una riga di dati, l'esecuzione di riepilogo visualizza **Non superato**.

Se è stato eseguito il metodo `AddIntegers_FromDataSourceTest` dell'esempio, la barra dei risultati diventa rossa e il metodo di test viene spostato nei **test non superati**. Un test basato sui dati non riesce se uno dei metodi di cui si esegue l'iterazione dall'origine dati ha esito negativo. Quando si sceglie un test basato sui dati non riuscito nella finestra **Esplora test**, il riquadro dei dettagli visualizza i risultati di ogni iterazione identificata dall'indice delle righe di dati. Nel nostro esempio, risulta che l'algoritmo `AddIntegers` non gestisce correttamente i valori negativi.

Dopo avere corretto il metodo sottoposto a test ed eseguito nuovamente il test, la barra dei risultati diventa verde e il metodo di test viene spostato nel gruppo **Test superati**.

## <a name="see-also"></a>Vedi anche

- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.DataSourceAttribute?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.TestContext.DataRow%2A?displayProperty=fullName>
- <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert?displayProperty=fullName>
- [Eseguire unit test del codice](../test/unit-test-your-code.md)
- [Eseguire unit test con Esplora test](../test/run-unit-tests-with-test-explorer.md)
- [Scrittura di unit test per .NET con il framework di unit test Microsoft per il codice gestito](../test/unit-test-your-code.md)
