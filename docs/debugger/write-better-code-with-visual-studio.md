---
title: Tecniche e strumenti di debug CRT
description: Scrivere codice migliore con meno bug tramite Visual Studio per risolvere le eccezioni, correggere gli errori e migliorare il codice
ms.custom:
- debug-experiment
- seodec18
ms.date: 01/24/2019
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: a355930734bfb122a088fb20817b3318a365cc63
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54961715"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Debug tecniche e strumenti che consentono di scrivere codice migliore

Correzione di bug e gli errori nel codice può richiedere molto tempo e talvolta frustrazione: attività. Serve tempo per imparare a eseguire il debug in modo efficace, ma un potente IDE come Visual Studio può rendere molto più semplice il processo. Un IDE consente di correggere gli errori e il debug del codice più rapidamente e non solo che, ma può anche agevolare la scrittura di codice migliorato con meno bug. L'obiettivo di questo articolo è offrire una visione olistica del processo di "correzione degli errori", in modo da conoscere quando usare l'analizzatore di codice, quando usare il debugger, come correzione delle eccezioni e come codice per un intent. Se si conosce già è necessario usare il debugger, vedere [innanzitutto osservare il debugger](../debugger/debugger-feature-tour.md).

In questo articolo si parla sfruttando l'IDE per rendere più produttiva la scrittura di codice sessioni. Discussa marginalmente numerose attività, ad esempio:

* Preparare il codice per il debug, sfruttando analizzatore del codice dell'IDE

* Per la risoluzione delle eccezioni (errori di run-time)

* Come ridurre al minimo i bug mediante la codifica per intent (utilizzando il metodo assert)

* Quando usare il debugger

Per dimostrare queste attività, abbiamo illustrato alcuni dei tipi più comuni degli errori e i bug che incontrano quando si tenta di eseguire il debug delle app. Anche se il codice di esempio è C#, le informazioni concettuali sono applicabili a livello generale a C++, Visual Basic, JavaScript e altri linguaggi supportati da Visual Studio (se diversamente specificato). Gli screenshot sono in linguaggio C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Creare un'app di esempio con alcuni degli errori in essa

Il codice seguente contiene alcuni bug che è possibile correggere mediante l'IDE di Visual Studio. In questo caso l'app è una semplice app che simula recupero dei dati JSON da un'operazione, la deserializzazione di dati a un oggetto e l'aggiornamento di un elenco semplice con i nuovi dati.

Per creare l'app:

1. Aprire Visual Studio e scegli **File > Nuovo progetto**. Sotto **Visual C#** , scegliere **Desktop di Windows** oppure **.NET Core**, quindi nel riquadro centrale scegliere un **App Console**.

    > [!NOTE]
    > Se il modello di progetto **Applicazione console** non viene visualizzato, fare clic sul collegamento **Apri il Programma di installazione di Visual Studio** nel riquadro sinistro della finestra di dialogo **Nuovo progetto**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo per desktop .NET** o **Sviluppo multipiattaforma .NET Core** e quindi **Modifica**.

2. Nel **Name** , digitare **Console_Parse_JSON** e fare clic su **OK**. Visual Studio crea il progetto.

3. Sostituire il codice del progetto predefinito *Program.cs* file con il codice di esempio seguente.

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

## <a name="find-the-red-and-green-squiggles"></a>Trovare le linee a zigzag rosse e verdi.

Prima di tentare di avviare l'app di esempio ed eseguire il debugger, controllare il codice nell'editor del codice per le linee a zigzag rosse e verdi. Questi rappresentano errori e avvisi che sono identificati dall'analizzatore di codice dell'IDE. Le righe rosse a zigzag sono errori di compilazione, che è necessario risolvere prima di poter eseguire il codice. Le sottolineature ondulate verdi sono avvisi. Sebbene sia spesso possibile eseguire l'app senza risolvere gli avvisi, può essere fonte di bug ed è spesso risparmiare tempo e problemi con l'analisi dei loro. Questi avvisi ed errori visualizzati anche nel **elenco errori** finestra, se si preferisce una visualizzazione elenco.

Nell'app di esempio, noterete che diverse righe rosse a zigzag che è necessario correggere e esamineranno uno quella verde. Ecco il primo errore.

![Errore durante la visualizzazione come una sottolineatura ondulata rossa](../debugger/media/write-better-code-red-squiggle.png)

Per correggere questo errore, verrà esaminato un'altra funzionalità dell'IDE, rappresentato dall'icona lampadina.

## <a name="check-the-light-bulb"></a>Controllare la lampadina.

Il primo sottolineatura ondulata rossa rappresenta un errore in fase di compilazione. Passare il mouse su di essa e viene visualizzato il messaggio ```The name `Encoding` does not exist in the current context```.

Si noti che questo errore viene visualizzata un'icona lampadina in basso a sinistra. Con la relativa icona cacciavite ![icona cacciavite](../ide/media/screwdriver-icon.png), l'icona lampadina ![icona lampadina](../ide/media/light-bulb-icon.png) rappresenta azioni rapide eseguibili automaticamente consente di correggere o effettuare il refactoring del codice inline. Problemi che rappresenta la lampadina *dovrebbero* correggere. In tutti i casi sono per i problemi che è possibile scegliere di correggere. Usare la prima correzione suggerita per correggere l'errore facendo **utilizzando System. Text** a sinistra.

![Usare la lampadina per correggere codice](../debugger/media/write-better-code-missing-include.png)

Quando si fa clic su questo elemento, Visual Studio aggiunge il `using System.Text` istruzione all'inizio del *Program.cs* file e la sottolineatura rossa scomparirà. (Quando non si è certi cosa farà una correzione suggerita, scegliere il **Anteprima modifiche** collegamento a destra prima di applicare la correzione.)

L'errore precedente è uno standard comune che in genere, risolvere aggiungendo una nuova `using` istruzione nel codice. Esistono diversi errori comuni, in modo analoghi a questo, ad esempio ```The type or namespace `Name` cannot be found.``` questi tipi di errore potrebbero indicare un riferimento all'assembly mancante (il pulsante destro del progetto, scegliere **Add** > **riferimento**), un nome scritto male o in una raccolta manca che è necessario aggiungere (per C#, fare clic sul progetto e scegliere **Gestisci pacchetti NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Risolvere gli errori e avvisi rimanenti

Esistono alcune altre sottolineature esaminare nel codice seguente. In questo caso, viene visualizzato un errore di conversione tipo comune. Quando passa il mouse sulla sottolineatura, noterete che il codice sta tentando di convertire una stringa in un integer, che non è supportato solo se si aggiunge codice esplicito per effettuare la conversione.

![Errore di conversione del tipo](../debugger/media/write-better-code-conversion-error.png)

Perché l'analizzatore di codice non è possibile indovinare l'intento, non esistono Nessun lampadine per aiutarti in questo momento. Per correggere questo errore, è necessario conoscere la finalità del codice. In questo esempio, non è troppo difficile da osservare che `points` deve essere un valore numerico (integer), poiché si sta provando ad aggiungere `points` a `totalpoints`.

Per correggere questo errore, modificare il `points` membro del `User` da questa classe:

```csharp
[DataMember]
internal string points;
```

a questo scopo:

```csharp
[DataMember]
internal int points;
```

Le linee rosse ondulate nell'editor di codice più visualizzata.

Successivamente, passare il mouse sulla linea verde ondulata nella dichiarazione del `points` (membro dati). L'analizzatore di codice indica che la variabile non viene mai assegnata un valore.

![Messaggio di avviso per la variabile non assegnata](../debugger/media/write-better-code-warning-message.png)

In genere, questo rappresenta un problema che deve essere corretto. Tuttavia, nell'app di esempio è sono in realtà i dati archiviati nel `points` durante il processo di deserializzazione e quindi aggiungere tale valore alla variabile il `totalpoints` (membro dati). In questo esempio, si conosce l'intento del codice e può ignorare l'avviso. Tuttavia, se si desidera eliminare l'avviso, è possibile sostituire il codice seguente:

```csharp
item.totalpoints = users[i].points;
```

con il seguente:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

La sottolineatura a zigzag di colore verde andrà a sparire.

## <a name="fix-an-exception"></a>Correggere un'eccezione

Dopo aver risolto tutte le righe rosse a zigzag e risolti o almeno esaminare - tutte le sottolineature ondulate verdi, si è pronti per avviare il debugger ed eseguire l'app.

Premere **F5** (**Debug > Avvia debug**) o il pulsante **Avvia debug** ![Avvia debug](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") nella barra degli strumenti Debug.

A questo punto, l'app di esempio genera una `SerializationException` eccezione (un errore di runtime). Vale a dire, l'app riduce l'area dei dati tenta di serializzare. Poiché è stato avviato l'app in modalità di debug (debugger collegato), Helper eccezioni del debugger consente a destra il codice che ha generato l'eccezione e ti offre un messaggio di errore utili.

![Si verifica una SerializationException](../debugger/media/write-better-code-serialization-exception.png)

Il messaggio di errore indica che il valore `4o` non può essere analizzato come numero intero. Pertanto, in questo esempio, si conosce i dati non sono valido: `4o` deve essere `40`. Tuttavia, se non si ha controllo dei dati in uno scenario reale (ad esempio si riceve da un servizio web), operazioni su di esso? Come risolvere il problema?

Quando si raggiunge un'eccezione, è necessario (e risposte) un paio di domande:

* È semplicemente un bug che è possibile risolvere questa eccezione? Oppure

* Questa eccezione è qualcosa che gli utenti possono incontrare?

Se è il primo, correggere il bug. (Nell'app di esempio, che si intende correggere i dati errati.) Se si tratta del secondo, si potrebbe essere necessario gestire l'eccezione nel codice utilizzando un `try/catch` blocco (prendiamo in esame gli altri possibili strategie nella sezione successiva). Nell'app di esempio, sostituire il codice seguente:

```csharp
users = ser.ReadObject(ms) as User[];
```

con questo codice:

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

Oggetto `try/catch` blocco ha alcune delle prestazioni dei costi, quindi è opportuno usarle quando servono effettivamente, vale a dire, in cui (a) possono verificarsi nella versione di rilascio dell'app e in cui (b) la documentazione per il metodo indica che è consigliabile ricercare il eccezione (presupponendo che la documentazione è stata completata!). In molti casi, è possibile gestire un'eccezione in modo appropriato e l'utente non sarà mai necessario segnalarlo.

Ecco un paio di suggerimenti importanti per la gestione delle eccezioni:

* Evitare di usare un blocco catch vuoto, ad esempio `catch (Exception) {}`, che non accetta l'azione appropriata per esporre o gestire un errore. Un blocco catch vuoto o non informativa possibile nascondere le eccezioni e possa rendere più difficile eseguire il debug anziché più facilmente il codice.

* Usare la `try/catch` blocco di tutto la funzione specifica che genera l'eccezione (`ReadObject`, nell'app di esempio). Se si utilizza intorno a un frammento di codice più esaustivo, si finisce nascondendo la posizione dell'errore. Ad esempio, non usare la `try/catch` blocco nella chiamata alla funzione di padre `ReadToObject`, riportati di seguito, o non si sa esattamente dove l'eccezione si è verificato.

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

* Per funzioni non note da includere nell'app, expecially quelli che interagiscono con i dati esterni (ad esempio, una richiesta web), consultare la documentazione per visualizzare le eccezioni che la funzione è potrebbe generare. Può trattarsi di informazioni critiche per la gestione degli errori corretta e di debug dell'app.

Per le app di esempio, correggere la `SerializationException` nella `GetJsonData` metodo modificando `4o` a `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Chiarire le proprie intenzioni codice dall'uso di assert

Fare clic sul pulsante **Riavvia** ![Riavvia app](../debugger/media/dbg-tour-restart.png "Riavvia app") nella barra degli strumenti di debug (**CTRL** + **MAIUSC** + **F5**). L'app verrà riavviato in meno passaggi. Verrà visualizzato l'output seguente nella finestra della console.

![Valore null nell'output](../debugger/media/write-better-code-using-assert-null-output.png)

È possibile visualizzare un elemento in questo output non è corretto. **nome** e **lastname** per il terzo record sono vuote.

Questo è il momento giusto per parlare di una procedura di codifica utile, spesso sottoutilizzata, che consiste nell'usare `assert` istruzioni nelle funzioni. Aggiungendo il codice seguente, si include un controllo di runtime per assicurarsi che `firstname` e `lastname` non sono `null`. Sostituire il codice seguente nel `UpdateRecords` metodo:

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

Aggiungendo `assert` istruzioni simile alle funzioni durante il processo di sviluppo, consente di specificare la finalità del codice. Nell'esempio precedente, abbiamo specificare quanto segue:

* Una stringa valida è necessaria per il nome
* Una stringa valida è necessaria per il cognome

Specificando finalità in questo modo, si applicano i requisiti. Si tratta di un metodo semplice e pratico che è possibile usare per i bug di superficie durante lo sviluppo. (`assert` istruzioni possono essere usate anche come l'elemento principale di unit test.)

Fare clic sul pulsante **Riavvia** ![Riavvia app](../debugger/media/dbg-tour-restart.png "Riavvia app") nella barra degli strumenti di debug (**CTRL** + **MAIUSC** + **F5**).

> [!NOTE]
> Il `assert` codice non è attivo solo in una build di Debug.

Quando si riavvia, il debugger si sofferma sul `assert` istruzione, perché l'espressione `users[i].firstname != null` restituisca `false` invece di `true`.

![L'asserzione viene risolta in false](../debugger/media/write-better-code-using-assert.png)

Il `assert` errore indica che si verifica un problema che devi analizzare. `assert` può coprire molti scenari in cui non viene necessariamente visualizzata un'eccezione. In questo esempio, l'utente non verrà restituita un'eccezione e un `null` valore viene aggiunto come `firstname` nell'elenco di record. Ciò può causare problemi in un secondo momento (ad esempio vedere nell'output della console) e potrebbe essere difficile eseguire il debug.

> [!NOTE]
> Negli scenari in cui si chiama un metodo per la `null` valore, un `NullReferenceException` risultati. In genere si vuole evitare di usare un `try/catch` blocca per un'eccezione, vale a dire, un'eccezione che non è associata alla funzione di libreria specifico. Puoi generare qualsiasi oggetto un `NullReferenceException`. Se non si è certi, consultare la documentazione per la funzione della libreria.

Durante il processo di debug, è consigliabile mantenere una determinata `assert` istruzione fino a quando non si conosce è necessario sostituirlo con una correzione rapida per il codice effettivo. Si supponga che si decide che l'utente potrebbe incontrare l'eccezione in una build di rilascio dell'app. In tal caso, è necessario effettuare il refactoring di codice per assicurarsi che l'app non generare un'eccezione irreversibile o comportare un altro errore. Pertanto, per correggere questo codice, sostituire il codice seguente:

```csharp
if (existingUser == false)
{
    User user = new User();
```

con questo codice:

```csharp
if (existingUser == false && users[i].firstname != null && users[i].lastname != null)
{
    User user = new User();
```

Tramite questo codice, si soddisfano i requisiti di codice e assicurarsi che un record con un `firstname` oppure `lastname` pari a `null` non viene aggiunto ai dati.

In questo esempio, abbiamo aggiunto due `assert` istruzioni all'interno di un ciclo. In genere, quando si usa `assert`, è consigliabile aggiungere `assert` istruzioni nel punto di ingresso (inizio) di una funzione o metodo. Si sta attualmente esaminando la `UpdateRecords` metodo nell'app di esempio. In questo metodo, si è sicuri problemi se uno degli argomenti del metodo è `null`, quindi archiviarle entrambi con un `assert` istruzione relativa al punto di ingresso della funzione.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Per le istruzioni precedenti, la finalità è che si caricano dati esistenti (`db`) e recuperare i nuovi dati (`users`) prima di aggiornare alcuna operazione.

È possibile usare `assert` con qualsiasi tipo di espressione che restituisca `true` o `false`. Quindi, ad esempio, è possibile aggiungere un `assert` istruzione simile alla seguente.

```csharp
Debug.Assert(users[0].points > 0);
```

Il codice precedente è utile se si desidera specificare la finalità seguente: un nuovo valore di punto di maggiore di zero (0) è richiesto per aggiornare il record dell'utente.

## <a name="inspect-your-code-in-the-debugger"></a>Esaminare il codice nel debugger

Bene, ora che è stato risolto tutti gli elementi critici che si è verificato un problema con l'app di esempio, è possibile passare ad altri importanti!

È stato illustrato Helper eccezioni del debugger, ma il debugger è uno strumento molto più potente che consente inoltre di eseguire altre operazioni, ad esempio istruzioni del codice ed esaminare le variabili. Queste funzionalità più potenti sono utili in molti scenari, in particolare quanto segue:

* Sta provando a isolare un bug di runtime nel codice, ma non è possibile eseguire questa operazione usando i metodi e gli strumenti illustrati in precedenza.

* Si desidera convalidare il codice, vale a dire, guardare mentre è in esecuzione per assicurarsi che si comporta nel modo che previsto e in questo ciò che si desidera venga.

    È interessante osservare il codice mentre è in esecuzione. È possibile approfondire il codice in questo modo e spesso possibile identificare i bug prima che si manifestino alcun sintomo ovvia.

Per informazioni su come usare le funzionalità essenziali del debugger, vedere [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Correggi problemi di prestazioni

I bug di un altro tipo includono codice inefficiente che fa sì che l'app a esecuzione lenta o usare troppa memoria. Ottimizzazione delle prestazioni è in genere, è eseguire in un secondo momento nell'ambiente di sviluppo di app. Tuttavia, è possibile eseguire in problemi di prestazioni all'inizio (ad esempio, noterete che l'esecuzione di alcune parti dell'applicazione risulta rallentata), e potrebbe essere necessario testare l'app con gli strumenti di profilatura sin dall'inizio. Per altre informazioni su strumenti, ad esempio lo strumento utilizzo CPU e l'analizzatore di memoria per la profilatura, vedere [descrive gli strumenti di profilatura](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Passaggi successivi

In questo articolo si è appreso come evitare e risolvere molti bug comuni nel codice e quando usare il debugger. Altre informazioni sull'uso del debugger di Visual Studio per correggere i bug.

> [!div class="nextstepaction"]
> [Debug per principianti](../debugger/debugging-absolute-beginners.md)
