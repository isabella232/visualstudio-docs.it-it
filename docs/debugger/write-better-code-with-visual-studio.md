---
title: Tecniche e strumenti di debug CRT
description: Scrivere codice migliore con meno bug usando Visual Studio per correggere le eccezioni, correggere gli errori e migliorare il codice
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f0052faee4e1701b843c71cc6e53dbf89adac7ae
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122035878"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Tecniche di debug e strumenti che consentono di scrivere codice migliore

La correzione di bug ed errori nel codice può essere un'attività dispendiosa in termini di tempo e talvolta frustrante. È necessario tempo per imparare a eseguire il debug in modo efficace, ma un IDE potente come Visual Studio può rendere il processo molto più semplice. Un IDE consente di correggere gli errori ed eseguire il debug del codice più rapidamente e non solo, ma può anche aiutare a scrivere codice migliore con meno bug. L'obiettivo di questo articolo è offrire una visualizzazione olistica del processo di "correzione di bug", in modo da sapere quando usare l'analizzatore del codice, quando usare il debugger, come correggere le eccezioni e come creare codice per finalità. Se si sa già che è necessario usare il debugger, vedere [Prima di tutto il debugger.](../debugger/debugger-feature-tour.md)

Questo articolo illustra come sfruttare l'IDE per rendere le sessioni di scrittura del codice più produttive. Vengono eseguite diverse attività, ad esempio:

* Preparare il codice per il debug sfruttando l'analizzatore del codice dell'IDE

* Come correggere le eccezioni (errori di runtime)

* Come ridurre al minimo i bug codificando la finalità (usando assert)

* Quando usare il debugger

Per illustrare queste attività, vengono illustrati alcuni dei tipi più comuni di errori e bug che si verificano quando si tenta di eseguire il debug delle app. Anche se il codice di esempio è C#, le informazioni concettuali sono in genere applicabili a C++, Visual Basic, JavaScript e altri linguaggi supportati da Visual Studio (tranne dove specificato). Gli screenshot sono in linguaggio C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Creare un'app di esempio con alcuni bug ed errori

Il codice seguente contiene alcuni bug che è possibile correggere usando l'IDE Visual Studio. L'app è una semplice app che simula il recupero di dati JSON da un'operazione, la deserializzazione dei dati in un oggetto e l'aggiornamento di un semplice elenco con i nuovi dati.

Per creare l'app:

1. È necessario aver installato Visual Studio e il carico di lavoro **Sviluppo multipiattaforma .NET Core.**

    Se non è ancora stato installato Visual Studio, passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.

    Se è necessario installare il carico di lavoro ma si dispone già di Visual Studio, fare clic **su** Strumenti  >  **Ottieni strumenti e funzionalità**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il **carico di lavoro Sviluppo multipiattaforma .NET Core,** quindi scegliere **Modifica.**

1. Aprire Visual Studio.

    ::: moniker range=">=vs-2019"
    Nella finestra iniziale scegliere **Crea un nuovo progetto.** Digitare **console** nella casella di ricerca e quindi scegliere **App console** per .NET Core. Scegliere **Avanti**. Digitare un nome di progetto **come Console_Parse_JSON** e fare clic su **Avanti** o **Crea,** a seconda dell'opzione disponibile.

    Per .NET Core, scegliere il framework di destinazione consigliato (.NET Core 3.1) o .NET 5 e quindi scegliere **Crea.**

    Se il modello di progetto **App console** per .NET Core non è visualizzato, passare a Strumenti Ottieni strumenti e funzionalità per aprire il  >  Programma di installazione di Visual Studio. Scegliere il **carico di lavoro Sviluppo multipiattaforma .NET Core,** quindi scegliere **Modifica.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu superiore scegliere **File**  >  **Nuovo**  >  **Project**. Nel riquadro sinistro  della finestra di dialogo Nuovo progetto in **Visual C#** scegliere **App console** e quindi nel riquadro centrale scegliere App **console (.NET Core)**. Digitare un nome **come** Console_Parse_JSON e fare clic su **OK.**

    Se il modello di progetto **App console (.NET Core)** non è visualizzato, passare a Strumenti Ottieni strumenti e funzionalità per aprire il   >  Programma di installazione di Visual Studio. Scegliere il **carico di lavoro Sviluppo multipiattaforma .NET Core,** quindi scegliere **Modifica.**
    ::: moniker-end

    Visual Studio crea il progetto della console che viene visualizzato nel riquadro destro di Esplora soluzioni.

1. Sostituire il codice predefinito nel file *Program.cs* del progetto con il codice di esempio seguente.

```csharp
using System;
using System.Collections.Generic;
using System.Runtime.Serialization.Json;
using System.Runtime.Serialization;
using System.IO;

namespace Console_Parse_JSON
{
    class Program
    {
        static void Main(string[] args)
        {
            var localDB = LoadRecords();
            string data = GetJsonData();

            User[] users = ReadToObject(data);

            UpdateRecords(localDB, users);

            for (int i = 0; i < users.Length; i++)
            {
                List<User> result = localDB.FindAll(delegate (User u) {
                    return u.lastname == users[i].lastname;
                    });
                foreach (var item in result)
                {
                    Console.WriteLine($"Matching Record, got name={item.firstname}, lastname={item.lastname}, age={item.totalpoints}");
                }
            }

            Console.ReadKey();
        }

        // Deserialize a JSON stream to a User object.
        public static User[] ReadToObject(string json)
        {
            User deserializedUser = new User();
            User[] users = { };
            MemoryStream ms = new MemoryStream(Encoding.UTF8.GetBytes(json));
            DataContractJsonSerializer ser = new DataContractJsonSerializer(users.GetType());

            users = ser.ReadObject(ms) as User[];

            ms.Close();
            return users;
        }

        // Simulated operation that returns JSON data.
        public static string GetJsonData()
        {
            string str = "[{ \"points\":4o,\"firstname\":\"Fred\",\"lastname\":\"Smith\"},{\"lastName\":\"Jackson\"}]";
            return str;
        }

        public static List<User> LoadRecords()
        {
            var db = new List<User> { };
            User user1 = new User();
            user1.firstname = "Joe";
            user1.lastname = "Smith";
            user1.totalpoints = 41;

            db.Add(user1);

            User user2 = new User();
            user2.firstname = "Pete";
            user2.lastname = "Peterson";
            user2.totalpoints = 30;

            db.Add(user2);

            return db;
        }
        public static void UpdateRecords(List<User> db, User[] users)
        {
            bool existingUser = false;

            for (int i = 0; i < users.Length; i++)
            {
                foreach (var item in db)
                {
                    if (item.lastname == users[i].lastname && item.firstname == users[i].firstname)
                    {
                        existingUser = true;
                        item.totalpoints += users[i].points;

                    }
                }
                if (existingUser == false)
                {
                    User user = new User();
                    user.firstname = users[i].firstname;
                    user.lastname = users[i].lastname;
                    user.totalpoints = users[i].points;

                    db.Add(user);
                }
            }
        }
    }

    [DataContract]
    internal class User
    {
        [DataMember]
        internal string firstname;

        [DataMember]
        internal string lastname;

        [DataMember]
        // internal double points;
        internal string points;

        [DataMember]
        internal int totalpoints;
    }
}
```

## <a name="find-the-red-and-green-squiggles"></a>Trovare le linee a linee a linee rosse e verdi.

Prima di provare ad avviare l'app di esempio ed eseguire il debugger, controllare che nel codice nell'editor di codice ci sia una linea a linee a linee rossa e verde. Che rappresentano gli errori e gli avvisi identificati dall'analizzatore del codice dell'IDE. Le linee a linee a linee rosse sono errori in fase di compilazione, che è necessario correggere prima di poter eseguire il codice. Le ondre di colore verde sono avvisi. Anche se spesso è possibile eseguire l'app senza correggere gli avvisi, possono essere una fonte di bug e spesso è possibile risparmiare tempo e problemi analizzandoli. Questi avvisi ed errori vengono visualizzati anche nella **finestra Elenco** errori, se si preferisce una visualizzazione elenco.

Nell'app di esempio sono presenti diverse linee a linee a linee rosse che è necessario correggere e una verde da esaminare. Ecco il primo errore.

![Errore visualizzato come una linea a linee oncchi rosse](../debugger/media/write-better-code-red-squiggle.png)

Per correggere l'errore, verrà visualizzata un'altra funzionalità dell'IDE, rappresentata dall'icona a forma di lampadina.

## <a name="check-the-light-bulb"></a>Controllare la lampadina.

La prima linea onerata rossa rappresenta un errore in fase di compilazione. Passare il puntatore del mouse su di esso per visualizzare il messaggio ```The name `Encoding` does not exist in the current context``` .

Si noti che questo errore mostra un'icona a forma di lampadina in basso a sinistra. Insieme all'icona a forma di cacciavite icona a forma di cacciavite , l'icona a forma di lampadina icona a forma di lampadina rappresenta azioni rapide che consentono di correggere o eseguire il ![ ](../ide/media/screwdriver-icon.png) ![ ](../ide/media/light-bulb-icon.png) refactoring del codice inline. La lampadina rappresenta i problemi che *è necessario* risolvere. Il cacciavite è per i problemi che è possibile scegliere di risolvere. Usare la prima correzione suggerita per risolvere l'errore facendo clic **su usando System.Text** a sinistra.

![Usare la lampadina per correggere il codice](../debugger/media/write-better-code-missing-include.png)

Quando si fa clic su questo elemento, Visual Studio l'istruzione all'inizio del `using System.Text` file *Program.cs* e la linea a linee rossa non viene più selezionata. Quando non si è certi dell'operazione che verrà  applicata da una correzione suggerita, scegliere il collegamento Anteprima modifiche a destra prima di applicare la correzione.

L'errore precedente è un errore comune che in genere viene corretto aggiungendo una `using` nuova istruzione al codice. Esistono diversi errori comuni simili a questo, ad esempio Questi tipi di errori possono indicare un riferimento all'assembly mancante (fare clic con il pulsante destro del mouse sul progetto, scegliere Aggiungi riferimento ), un nome errato o una libreria mancante da aggiungere ```The type or namespace `Name` cannot be found.```   >  (per C#, fare clic con il pulsante destro del mouse sul progetto e scegliere **Gestisci pacchetti NuGet).**

## <a name="fix-the-remaining-errors-and-warnings"></a>Correggere gli errori e gli avvisi rimanenti

In questo codice è possibile osservare alcune altre ondreg. In questo caso viene visualizzato un errore di conversione del tipo comune. Quando si passa il puntatore del mouse sulla stringa onnipresente, si nota che il codice sta tentando di convertire una stringa in int, operazione non supportata a meno che non si abiliti codice esplicito per eseguire la conversione.

![Errore di conversione del tipo](../debugger/media/write-better-code-conversion-error.png)

Poiché l'analizzatore del codice non può indovinare la finalità, questa volta non ci sono lampadine utili. Per correggere l'errore, è necessario conoscere la finalità del codice. In questo esempio non è troppo difficile vedere che deve essere un valore numerico (intero), perché si sta tentando `points` di aggiungere `points` a `totalpoints` .

Per correggere l'errore, modificare `points` il membro della classe nel modo `User` seguente:

```csharp
[DataMember]
internal string points;
```

con questo:

```csharp
[DataMember]
internal int points;
```

Le righe ondulate rosse nell'editor di codice non sono più presenti.

Passare quindi il puntatore del mouse sulla linea onnipresente verde nella dichiarazione del `points` membro dati. L'analizzatore del codice indica che alla variabile non viene mai assegnato un valore.

![Messaggio di avviso per la variabile non assegnata](../debugger/media/write-better-code-warning-message.png)

In genere, si tratta di un problema che deve essere risolto. Tuttavia, nell'app di esempio si archiviano i dati nella variabile durante il processo di deserializzazione e quindi si aggiunge tale valore `points` al `totalpoints` membro dati. In questo esempio si conosce la finalità del codice e si può tranquillamente ignorare l'avviso. Tuttavia, se si vuole eliminare l'avviso, è possibile sostituire il codice seguente:

```csharp
item.totalpoints = users[i].points;
```

con il seguente:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

La linea a ondza verde si allontana.

## <a name="fix-an-exception"></a>Correggere un'eccezione

Dopo aver corretto tutte le linee a onnivaia rossa e risolto, o almeno a seguito di un'indagine, tutte le linee a linee a linee verdi, si è pronti per avviare il debugger ed eseguire l'app.

Premere **F5** (**Debug > Avvia** debug ) o il pulsante Avvia debug ![Avvia](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") debug sulla barra degli strumenti Debug. 

A questo punto, l'app di esempio genera `SerializationException` un'eccezione (un errore di runtime). Ciò significa che l'app si affolla sui dati che sta tentando di serializzare. Poiché l'app è stata avviata in modalità di debug (collegata al debugger), l'helper eccezioni del debugger consente di accedere direttamente al codice che ha generato l'eccezione e fornisce un messaggio di errore utile.

![Si verifica un'eccezione SerializationException](../debugger/media/write-better-code-serialization-exception.png)

Il messaggio di errore indica che il valore `4o` non può essere analizzato come integer. Quindi, in questo esempio si sa che i dati non sono validi: `4o` deve essere `40` . Tuttavia, se non si ha il controllo dei dati in uno scenario reale (ad esempio si riceve da un servizio Web), cosa si fa? Come si risolve il problema?

Quando si verifica un'eccezione, è necessario porre (e rispondere) un paio di domande:

* Questa eccezione è solo un bug che è possibile correggere? Oppure

* Si tratta di un'eccezione che gli utenti potrebbero riscontrare?

Se si tratta del primo, correggere il bug. Nell'app di esempio ciò significa correggere i dati non validi. Se si tratta di quest'ultimo, potrebbe essere necessario gestire l'eccezione nel codice usando un blocco . Nella sezione successiva vengono trattate altre `try/catch` strategie possibili. Nell'app di esempio sostituire il codice seguente:

```csharp
users = ser.ReadObject(ms) as User[];
```

Con questo:

```csharp
try
{
    users = ser.ReadObject(ms) as User[];
}
catch (SerializationException)
{
    Console.WriteLine("Give user some info or instructions, if necessary");
    // Take appropriate action for your app
}
```

Un blocco ha un costo delle prestazioni, quindi è consigliabile usarli solo quando sono effettivamente necessari, ovvero dove (a) potrebbero verificarsi nella versione di rilascio dell'app e dove (b) la documentazione per il metodo indica che è necessario verificare l'eccezione (presupponendo che la documentazione sia `try/catch` completa).) In molti casi, è possibile gestire un'eccezione in modo appropriato e l'utente non dovrà mai conoscerla.

Ecco alcuni suggerimenti importanti per la gestione delle eccezioni:

* Evitare di usare un blocco catch vuoto, ad esempio , che non esegue le `catch (Exception) {}` azioni appropriate per esporre o gestire un errore. Un blocco catch vuoto o non informativo può nascondere le eccezioni e rendere più difficile il debug del codice anziché semplificarne il debug.

* Usare il `try/catch` blocco intorno alla funzione specifica che genera l'eccezione ( , `ReadObject` nell'app di esempio). Se si usa intorno a un blocco di codice più grande, si nasconde la posizione dell'errore. Ad esempio, non usare il blocco intorno alla chiamata alla funzione padre , illustrato qui, oppure non si saprà esattamente dove si è verificata `try/catch` `ReadToObject` l'eccezione.

    ```csharp
    // Don't do this
    try
    {
        User[] users = ReadToObject(data);
    }
    catch (SerializationException)
    {
    }
    ```

* Per le funzioni non familiari incluse nell'app, in particolare quelle che interagiscono con dati esterni (ad esempio una richiesta Web), consultare la documentazione per verificare quali eccezioni la funzione potrebbe generare. Possono trattarsi di informazioni critiche per una corretta gestione degli errori e per il debug dell'app.

Per l'app di esempio, `SerializationException` correggere nel metodo modificando in `GetJsonData` `4o` `40` .

## <a name="clarify-your-code-intent-by-using-assert"></a>Chiarire la finalità del codice usando l'asserzione

Fare clic sul **pulsante Riavvia** ![riavvia app](../debugger/media/dbg-tour-restart.png "RestartApp") sulla barra degli strumenti debug ( CTRL  +  **MAIUSC**  +  **F5**). In questo modo l'app viene riavviata in un minor numero di passaggi. Nella finestra della console viene visualizzato l'output seguente.

![Valore Null nell'output](../debugger/media/write-better-code-using-assert-null-output.png)

È possibile vedere qualcosa in questo output che non è del tutto giusto. **name** e **lastname** per il terzo record sono vuoti.

Questo è un buon momento per parlare di una pratica di codifica utile, spesso sottoutilizzata, che consiste nell'usare istruzioni `assert` nelle funzioni. Aggiungendo il codice seguente, si include un controllo di runtime per assicurarsi che `firstname` e `lastname` non siano `null` . Sostituire il codice seguente nel `UpdateRecords` metodo :

```csharp
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

con il seguente:

```csharp
// Also, add a using statement for System.Diagnostics at the start of the file.
Debug.Assert(users[i].firstname != null);
Debug.Assert(users[i].lastname != null);
if (existingUser == false)
{
    User user = new User();
    user.firstname = users[i].firstname;
    user.lastname = users[i].lastname;
```

Aggiungendo istruzioni come queste alle funzioni durante il processo di sviluppo, è possibile specificare la `assert` finalità del codice. Nell'esempio precedente si specifica quanto segue:

* Per il nome è necessaria una stringa valida
* Per il cognome è necessaria una stringa valida

Specificando la finalità in questo modo, si applicano i requisiti. Si tratta di un metodo semplice e pratico che è possibile usare per visualizzare i bug durante lo sviluppo. Le `assert` istruzioni vengono usate anche come elemento principale negli unit test.

Fare clic sul **pulsante Riavvia** ![riavvia app](../debugger/media/dbg-tour-restart.png "RestartApp") sulla barra degli strumenti debug ( CTRL  +  **MAIUSC**  +  **F5**).

> [!NOTE]
> Il `assert` codice è attivo solo in una build di debug.

Al riavvio, il debugger viene sospeso `assert` sull'istruzione , perché l'espressione `users[i].firstname != null` restituisce invece di `false` `true` .

![Assert viene risolto in false](../debugger/media/write-better-code-using-assert.png)

`assert`L'errore indica che si è verificato un problema che è necessario analizzare. `assert` può coprire molti scenari in cui non viene necessariamente visualizzata un'eccezione. In questo esempio l'utente non visualizza un'eccezione e viene aggiunto un valore `null` `firstname` come nell'elenco di record. Ciò potrebbe causare problemi in un secondo momento ,ad esempio nell'output della console, e potrebbe essere più difficile eseguire il debug.

> [!NOTE]
> Negli scenari in cui si chiama un metodo sul `null` valore , viene `NullReferenceException` restituito un risultato. In genere si vuole evitare di usare un blocco per un'eccezione generale, ad esempio un'eccezione non `try/catch` associata alla funzione di libreria specifica. Qualsiasi oggetto può generare un'eccezione `NullReferenceException` . Se non si è certi, consultare la documentazione relativa alla funzione di libreria.

Durante il processo di debug, è bene mantenere un'istruzione specifica fino a quando non si sa che è necessario sostituirla `assert` con una correzione di codice effettiva. Si potrebbe decidere che l'utente potrebbe riscontrare l'eccezione in una build di rilascio dell'app. In tal caso, è necessario effettuare il refactoring del codice per assicurarsi che l'app non genera un'eccezione irreversibile o non restituirà altri errori. Quindi, per correggere questo codice, sostituire il codice seguente:

```csharp
if (existingUser == false)
{
    User user = new User();
```

Con questo:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Usando questo codice, è possibile soddisfare i requisiti del codice e assicurarsi che un record con valore o non sia `firstname` `lastname` aggiunto ai `null` dati.

In questo esempio sono state aggiunte le due `assert` istruzioni all'interno di un ciclo . In genere, quando si usa , è meglio aggiungere istruzioni nel punto di ingresso `assert` `assert` (inizio) di una funzione o di un metodo. Si sta attualmente esaminando il `UpdateRecords` metodo nell'app di esempio. In questo metodo si è in difficoltà se uno degli argomenti del metodo è , quindi verificarli entrambi con un'istruzione nel punto `null` `assert` di ingresso della funzione.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Per le istruzioni precedenti, la finalità è caricare i dati esistenti ( ) e recuperare nuovi dati ( ) prima `db` `users` di aggiornare qualsiasi elemento.

È possibile usare `assert` con qualsiasi tipo di espressione che si risolve in o `true` `false` . Ad esempio, è possibile aggiungere `assert` un'istruzione come questa.

```csharp
Debug.Assert(users[0].points > 0);
```

Il codice precedente è utile se si vuole specificare la finalità seguente: è necessario un nuovo valore di punto maggiore di zero (0) per aggiornare il record dell'utente.

## <a name="inspect-your-code-in-the-debugger"></a>Esaminare il codice nel debugger

Ora che sono stati risolti tutti gli elementi critici che non sono corretti con l'app di esempio, è possibile passare ad altre informazioni importanti.

È stato illustrato l'helper eccezioni del debugger, ma il debugger è uno strumento molto più potente che consente anche di eseguire altre operazioni, ad esempio eseguire un'istruzione alla volta il codice e controllarne le variabili. Queste funzionalità più potenti sono utili in molti scenari, in particolare le seguenti:

* Si sta tentando di isolare un bug di runtime nel codice, ma non è possibile farlo usando i metodi e gli strumenti descritti in precedenza.

* Si vuole convalidare il codice, ad esempio, guardarlo mentre è in esecuzione per assicurarsi che si comporti nel modo previsto e nel modo desiderato.

    È istruttivo osservare il codice durante l'esecuzione. È possibile ottenere altre informazioni sul codice in questo modo e spesso identificare i bug prima che manifestino sintomi evidenti.

Per informazioni su come usare le funzionalità essenziali del debugger, vedere [Debug per principianti assoluti.](../debugger/debugging-absolute-beginners.md)

## <a name="fix-performance-issues"></a>Correggere i problemi di prestazioni

I bug di altro tipo includono codice inefficiente che causa l'esecuzione lenta dell'app o l'uso di una quantità di memoria insufficiente. In genere, l'ottimizzazione delle prestazioni è un'operazione che si fa più avanti nello sviluppo di app. Tuttavia, è possibile verificarsi in anticipo problemi di prestazioni (ad esempio, si può vedere che una parte dell'app è lenta) e potrebbe essere necessario testare l'app con gli strumenti di profilatura in anticipo. Per altre informazioni sugli strumenti di profilatura, ad esempio lo strumento Utilizzo CPU e l'analizzatore di memoria, vedere Prima di tutto [gli strumenti di profilatura](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Passaggi successivi

In questo articolo si è appreso come evitare e correggere molti bug comuni nel codice e quando usare il debugger. Altre informazioni sull'uso del debugger Visual Studio per correggere i bug.

> [!div class="nextstepaction"]
> [Debug per principianti](../debugger/debugging-absolute-beginners.md)
