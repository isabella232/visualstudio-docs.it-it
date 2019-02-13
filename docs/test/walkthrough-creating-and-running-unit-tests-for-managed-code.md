---
title: Creare ed eseguire unit test per codice gestito
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- unit tests, walkthrough
- unit tests, creating
- unit tests, generating
- unit tests, running
- unit tests, authoring
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
author: gewarren
ms.openlocfilehash: 26988b2fd74ae66bd1ef2724c55248371a81adf1
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55922290"
---
# <a name="walkthrough-create-and-run-unit-tests-for-managed-code"></a>Procedura dettagliata: Creare ed eseguire unit test per codice gestito

Questo articolo illustra come creare, eseguire e personalizzare una serie di unit test usando il framework di unit test di Microsoft per il codice gestito ed **Esplora test** di Visual Studio. Verrà illustrato prima di tutto il progetto C# in fase di sviluppo, quindi saranno creati i test in cui verrà usato il codice e saranno esaminati i risultati. Sarà infine possibile modificare il codice del progetto ed eseguire nuovamente i test.

> [!NOTE]
> Questa procedura dettagliata usa il framework di unit test di Microsoft per il codice gestito. **Esplora test** consente anche di eseguire test da framework di unit test di terze parti che dispongono di adapter per **Esplora test**. Per altre informazioni, vedere [Installare framework di unit test di terze parti](../test/install-third-party-unit-test-frameworks.md)

Per informazioni su come eseguire i test dalla riga di comando, vedere [Opzioni della riga di comando di VSTest.Console.exe](vstest-console-options.md).

## <a name="prerequisites"></a>Prerequisiti

- Il progetto Bank. Vedere [Progetto di esempio per la creazione di unit test](../test/sample-project-for-creating-unit-tests.md).

## <a name="create-a-project-to-test"></a>Creare un progetto da sottoporre a test

1. Aprire Visual Studio.

2. Nel menu **File** selezionare **Nuovo** > **Progetto**.

   Verrà visualizzata la finestra di dialogo **Nuovo progetto** .

3. In **Modelli installati**fare clic su **Visual C#**.

4. Nell'elenco di tipi di applicazione fare clic su **Libreria di classi**.

5. Digitare **Bank** nella casella **Nome**, quindi scegliere **OK**.

   Viene creato nuovo progetto Bank, visualizzato in **Esplora soluzioni** con il file *Class1.cs* aperto nell'editor di codice.

   > [!NOTE]
   > Se il file *Class1.cs* non fosse aperto nell'editor del codice, fare doppio clic sul file *Class1.cs* in **Esplora soluzioni**.

6. Copiare il codice sorgente del [progetto di esempio per la creazione di unit test](../test/sample-project-for-creating-unit-tests.md) e sostituire il contenuto originale di *Class1.cs* con il codice copiato.

7. Salvare il file come *BankAccount.cs*.

8. Scegliere **Compila soluzione** dal menu **Compila**.

A questo punto è disponibile un progetto denominato Bank che contiene il codice sorgente da testare e gli strumenti da usare a questo scopo. Nello spazio dei nomi per Bank, BankAccountNS, è presente la classe pubblica BankAccount, i cui metodi saranno testati nelle routine seguenti.

In questo articolo i test sono incentrati sul metodo Debit. Il metodo Debit viene chiamato quando si preleva denaro da un conto. La definizione del metodo è la seguente:

```csharp
// Method to be tested.
public void Debit(double amount)
{
    if(amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount");
    }
    m_balance += amount;
}
```

## <a name="create-a-unit-test-project"></a>Creare un progetto di unit test

1. Nel menu **File** selezionare **Aggiungi** > **Nuovo progetto**.

   > [!TIP]
   > È possibile aggiungere un altro progetto a una soluzione esistente in altri due modi. È possibile fare clic con il pulsante destro del mouse sulla soluzione in **Esplora soluzioni** e scegliere **Aggiungi** > **Nuovo progetto**. Oppure, è possibile scegliere **File** > **Nuovo** > **Progetto** e quindi nella finestra di dialogo **Nuovo progetto** selezionare l'opzione **Aggiungi a soluzione**:
   >
   > ![Opzione Aggiungi a soluzione nella finestra di dialogo Nuovo progetto](media/add-to-solution.png)

2. Nella finestra di dialogo **Nuovo progetto** espandere **Installato**, **Visual C#** e quindi scegliere **Test**.

3. Nell'elenco dei modelli selezionare **Progetto unit test**.

4. Nella casella **Nome** immettere `BankTests`, quindi scegliere **OK**.

   Il progetto **BankTests** viene aggiunto alla soluzione **Bank**.

5. Nel progetto **BankTests** aggiungere un riferimento al progetto **Bank**.

   In **Esplora soluzioni** selezionare **Riferimenti** nel progetto **BankTests** e quindi scegliere **Aggiungi riferimento** dal menu di scelta rapida.

6. Nella finestra di dialogo **Gestione riferimenti** espandere **Soluzione** e quindi selezionare l'elemento **Bank**.

## <a name="create-the-test-class"></a>Creare la classe di test

Creare una classe di test per verificare la classe `BankAccount`. È possibile usare il file *UnitTest1.cs* generato dal modello del progetto, fornendo nomi più descrittivi per il file e la classe. È possibile eseguire questa operazione in un unico passaggio rinominando il file in **Esplora soluzioni**.

### <a name="rename-a-class-file"></a>Rinominare un file di classe

In **Esplora soluzioni** selezionare il file *UnitTest1.cs* nel progetto BankTests. Dal menu di scelta rapida scegliere **Rinomina** e quindi rinominare il file come *BankAccountTests.cs*. Scegliere **Sì** nella finestra di dialogo in cui viene chiesto se rinominare tutti i riferimenti del progetto all'elemento di codice `UnitTest1`.

Questo passaggio cambia il nome della classe in `BankAccountTests`. Il file *BankAccountTests.cs* contiene ora il codice seguente:

```csharp
using System;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace BankTests
{
    [TestClass]
    public class BankAccountTests
    {
        [TestMethod]
        public void TestMethod1()
        {
        }
    }
}
```

### <a name="add-a-using-statement-to-the-project-under-test"></a>Aggiungere un'istruzione using al progetto sottoposto a test

È anche possibile aggiungere un'istruzione `using` alla classe per consentire di effettuare chiamate nel progetto sottoposto a test senza usare nomi completi. All'inizio del file di classe aggiungere:

```csharp
using BankAccountNS;
```

### <a name="test-class-requirements"></a>Requisiti della classe di test

I requisiti minimi per una classe di test sono i seguenti:

- L'attributo `[TestClass]` è obbligatorio nel framework per unit test di Microsoft per il codice gestito per qualsiasi classe che contiene metodi di unit test che si desidera eseguire in Esplora test.

- Ogni metodo di test che si desidera eseguire in Esplora test deve avere l'attributo `[TestMethod]`.

È possibile avere altre classi in un progetto di unit test che non presentano l'attributo `[TestClass]` ed è possibile avere altri metodi nelle classi di test che non presentano l'attributo `[TestMethod]` . È possibile usare questi altri metodi e classi nei metodi di test.

## <a name="create-the-first-test-method"></a>Creare il primo metodo di test

In questa procedura si scriveranno metodi di unit test per verificare il comportamento del metodo `Debit` della classe `BankAccount`. Il metodo `Debit` è illustrato in precedenza in questo articolo.

È necessario controllare almeno tre comportamenti:

- Il metodo genera un oggetto <xref:System.ArgumentOutOfRangeException> se la quantità di debito è superiore al saldo.

- Il metodo genera <xref:System.ArgumentOutOfRangeException> se la quantità di debito è minore di zero.

- Se l'importo del debito è valido, il metodo sottrae l'importo dal saldo del conto.

> [!TIP]
> È possibile eliminare il metodo `TestMethod1` predefinito, in quanto non verrà usato in questa procedura dettagliata.

### <a name="to-create-a-test-method"></a>Per creare un metodo di test

Il primo test verifica che un importo valido (minore del saldo del conto e maggiore di zero) prelevi l'importo corretto dal conto. Aggiungere il metodo seguente alla classe `BankAccountTests` :

```csharp
[TestMethod]
public void Debit_WithValidAmount_UpdatesBalance()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 4.55;
    double expected = 7.44;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert
    double actual = account.Balance;
    Assert.AreEqual(expected, actual, 0.001, "Account not debited correctly");
}
```

Il metodo è semplice, in quanto configura un nuovo oggetto `BankAccount` con un saldo iniziale e quindi preleva un importo valido. Usa il metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.AreEqual%2A> per verificare che il saldo finale sia quello previsto.

### <a name="test-method-requirements"></a>Requisiti del metodo di test

Un metodo di test deve soddisfare i seguenti requisiti:

- È decorato con l'attributo `[TestMethod]`.

- Restituisce `void`.

- Non può avere parametri.

## <a name="build-and-run-the-test"></a>Compilare ed eseguire il test

1. Scegliere **Compila soluzione** dal menu **Compila**.

   Se non sono presenti errori, **Esplora test** viene visualizzato con **Debit_WithValidAmount_UpdatesBalance** nel gruppo **Test non eseguiti**.

   > [!TIP]
   > Se **Esplora test** non viene visualizzato al termine di una compilazione corretta, scegliere **Test** dal menu, quindi scegliere **Windows** e infine **Esplora test**.

2. Scegliere **Esegui tutto** per eseguire il test. Mentre il test è in esecuzione, la barra di stato nella parte superiore della finestra viene animata. Al termine del test, la barra diventa verde se tutti i metodi di test vengono superati oppure rossa se almeno uno dei test ha esito negativo.

3. In questo caso il test non riesce. Il metodo di test viene spostato nel gruppo **Test non superati**. Selezionare il metodo in **Esplora test** per visualizzare i dettagli nella parte inferiore della finestra.

## <a name="fix-your-code-and-rerun-your-tests"></a>Correggere il codice e rieseguire i test

### <a name="analyze-the-test-results"></a>Analizzare i risultati dei test

Il risultato del test contiene un messaggio che descrive l'errore. Per il metodo `AreEqual` il messaggio visualizza il contenuto previsto (parametro **Previsto\<*valore*>**) e il contenuto ricevuto (parametro **Effettivo\<*valore*>**). Si prevedeva una diminuzione del saldo, ma questo è aumentato di un valore pari alla somma prelevata.

Lo unit test ha rivelato un bug: la quantità da ritirare viene *aggiunta* al saldo del conto anziché essere *sottratta*.

### <a name="correct-the-bug"></a>Correggere il bug

Per correggere l'errore, sostituire la riga:

```csharp
m_balance += amount;
```

con:

```csharp
m_balance -= amount;
```

### <a name="rerun-the-test"></a>Eseguire nuovamente il test

In **Esplora test** scegliere **Esegui tutto** per rieseguire il test. La barra verde/rossa diventa verde per indicare che il test è stato superato, quindi il test viene spostato nel gruppo **Test superati**.

## <a name="use-unit-tests-to-improve-your-code"></a>Usare gli unit test per migliorare il codice

In questa sezione viene descritto come un processo iterativo di analisi, di sviluppo di unit test e di refactoring può aiutare a rendere il codice di produzione più affidabile ed efficace.

### <a name="analyze-the-issues"></a>Analizzare i problemi

È stato creato un metodo di test per confermare che un importo valido viene detratto correttamente nel metodo `Debit`. Ora verificare che il metodo generi un oggetto <xref:System.ArgumentOutOfRangeException> se la quantità di debito è

- superiore al saldo o
- minore di zero.

### <a name="create-the-test-methods"></a>Creare i metodi di test

Creare un metodo di test per verificare il comportamento corretto quando la quantità di debito è minore di zero:

```csharp
[TestMethod]
[ExpectedException(typeof(ArgumentOutOfRangeException))]
public void Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = -100.00;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    account.Debit(debitAmount);

    // Assert is handled by the ExpectedException attribute on the test method.
}
```

Usare l'attributo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.ExpectedExceptionAttribute> per confermare che è stata generata l'eccezione appropriata. L'attributo causa l'esito negativo del test a meno che non venga generata un'eccezione <xref:System.ArgumentOutOfRangeException> . Se si modifica temporaneamente il metodo sottoposto a test in modo che generi un'eccezione <xref:System.ApplicationException> più generica quando la quantità di debito è minore di zero, il test funziona correttamente, ovvero si verifica un errore.

Per sottoporre a test il caso in cui l'importo prelevato è maggiore del saldo, seguire questa procedura:

1. Creare un nuovo metodo di test denominato `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange`.

2. Copiare il corpo del metodo da `Debit_WhenAmountIsLessThanZero_ShouldThrowArgumentOutOfRange` nel nuovo metodo.

3. Impostare `debitAmount` su un numero maggiore del saldo.

### <a name="run-the-tests"></a>Eseguire i test

L'esecuzione dei due metodi di test dimostra che i test funzionano correttamente.

### <a name="continue-the-analysis"></a>Continuare l'analisi

Tuttavia, gli ultimi due metodi di test presentano alcuni problemi. Non è possibile determinare con certezza quale condizione nel metodo sottoposto a test genera l'eccezione quando si esegue uno dei due test. La possibilità di differenziare le due condizioni, ovvero una quantità di debito negativa o un importo superiore al saldo, renderebbe più affidabili i test.

Tornare ad osservare il metodo sottoposto a test. Notare che entrambe le istruzioni condizionali usano un costruttore `ArgumentOutOfRangeException` che accetta come parametro solo il nome dell'argomento:

```csharp
throw new ArgumentOutOfRangeException("amount");
```

È possibile usare un altro costruttore, che include informazioni molto più complete: <xref:System.ArgumentOutOfRangeException.%23ctor(System.String,System.Object,System.String)> include il nome dell'argomento, il valore dell'argomento e un messaggio definito dall'utente. È possibile effettuare il refactoring del metodo sottoposto a test per usare questo costruttore. Ancor meglio, è possibile usare membri di tipo pubblico per specificare gli errori.

### <a name="refactor-the-code-under-test"></a>Effettuare il refactoring del codice sottoposto a test

Prima è necessario definire due costanti per i messaggi di errore nell'ambito di classe. Inserire le costanti nella classe sottoposta a test (BankAccount):

```csharp
public const string DebitAmountExceedsBalanceMessage = "Debit amount exceeds balance";
public const string DebitAmountLessThanZeroMessage = "Debit amount is less than zero";
```

Quindi modificare le due istruzioni condizionali nel metodo `Debit`:

```csharp
    if (amount > m_balance)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountExceedsBalanceMessage);
    }

    if (amount < 0)
    {
        throw new ArgumentOutOfRangeException("amount", amount, DebitAmountLessThanZeroMessage);
    }
```

### <a name="refactor-the-test-methods"></a>Eseguire il refactoring dei metodi di test

Rimuovere l'attributo del metodo di test `ExpectedException` e invece rilevare l'eccezione generata e verificare il messaggio associato. Il metodo <xref:Microsoft.VisualStudio.TestTools.UnitTesting.StringAssert.Contains%2A?displayProperty=fullName> offre la possibilità di confrontare due stringhe.

Ora `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` può assumere l'aspetto seguente:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
    }
}
```

### <a name="retest-rewrite-and-reanalyze"></a>Rieseguire il test, riscrivere e rianalizzare

Si supponga che sia presente un bug nel metodo sottoposto a test e che il metodo `Debit` non attivi un <xref:System.ArgumentOutOfRangeException> né tantomeno generi il messaggio corretto con l'eccezione. Attualmente, il metodo di test non gestisce questa situazione. Se il valore `debitAmount` è valido, ovvero è minore del saldo ma maggiore di zero, non sarà intercettata alcuna eccezione e quindi non verrà mai attivata l'asserzione. Tuttavia il metodo supera il test. Questo non è il risultato desiderato, perché si vuole che il metodo di test abbia esito negativo se non viene generata alcuna eccezione.

È presente un bug nel metodo di test. Per risolvere il problema, aggiungere un'asserzione <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A> alla fine del metodo di test per gestire il caso in cui non viene generata alcuna eccezione.

Una nuova esecuzione dimostra che a questo punto il test *ha esito negativo* se viene rilevata l'eccezione corretta. Il blocco `catch` rileva l'eccezione, ma il metodo continua l'esecuzione e ha esito negativo in corrispondenza della nuova asserzione <xref:Microsoft.VisualStudio.TestTools.UnitTesting.Assert.Fail%2A>. Per risolvere il problema, aggiungere un'istruzione `return` dopo `StringAssert` nel blocco `catch`. Rieseguire il test per verificare che il problema è stato risolto. La versione finale di `Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange` è simile alla seguente:

```csharp
[TestMethod]
public void Debit_WhenAmountIsMoreThanBalance_ShouldThrowArgumentOutOfRange()
{
    // Arrange
    double beginningBalance = 11.99;
    double debitAmount = 20.0;
    BankAccount account = new BankAccount("Mr. Bryan Walton", beginningBalance);

    // Act
    try
    {
        account.Debit(debitAmount);
    }
    catch (ArgumentOutOfRangeException e)
    {
        // Assert
        StringAssert.Contains(e.Message, BankAccount.DebitAmountExceedsBalanceMessage);
        return;
    }

    Assert.Fail("The expected exception was not thrown.");
}
```

I miglioramenti al codice di test hanno creato metodi di test più affidabili e informativi. Il risultato più importante, tuttavia, è il miglioramento del codice sottoposto a test.
