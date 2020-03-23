---
title: Tecniche e strumenti di debug CRT
description: Scrivere codice migliore con meno bug utilizzando Visual Studio per correggere le eccezioni, correggere gli errori e migliorare il codice
ms.custom:
- debug-experiment
- seodec18
ms.date: 02/14/2020
ms.topic: conceptual
helpviewer_keywords:
- debugger
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2ac595098d793e44d65312a09fc8857225f150ef
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302028"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Tecniche e strumenti di debug per scrivere codice migliore

Correggere bug ed errori nel codice può richiedere molto tempo e talvolta essere frustrante. Ci vuole tempo per imparare a eseguire il debug in modo efficace, ma un IDE potente come Visual Studio può rendere il vostro lavoro molto più facile. Un IDE consente di correggere gli errori ed eseguire il debug del codice più rapidamente, e non solo, ma può anche aiutare a scrivere codice migliore con meno bug. Il nostro obiettivo in questo articolo è quello di fornire una visione olistica del processo di "correzione dei bug", in modo da sapere quando utilizzare l'analizzatore di codice, quando utilizzare il debugger, come correggere le eccezioni e come codificare per finalità. Se si è già noti che è necessario utilizzare il debugger, vedere [Prima di tutto esaminare il debugger](../debugger/debugger-feature-tour.md).

In questo articolo, si parla di sfruttare l'IDE per rendere le sessioni di codifica più produttivo. Tocchiamo diverse attività, come:

* Preparare il codice per il debug sfruttando l'analizzatore di codice dell'IDEPrepare your code for debugging by leveraging the IDE's code analyzer

* Come correggere le eccezioni (errori di runtime)How to fix exceptions (run-time errors)

* Come ridurre al minimo i bug codificando per finalità (utilizzando assert)

* Quando utilizzare il debugger

Per illustrare queste attività, vengono illustrati alcuni dei tipi più comuni di errori e bug che si verificano quando si tenta di eseguire il debug delle app. Anche se il codice di esempio è in c'è, le informazioni concettuali sono in genere applicabili a C , Visual Basic, JavaScript e altri linguaggi supportati da Visual Studio (tranne dove indicato). Gli screenshot sono in linguaggio C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Creare un'app di esempio con alcuni bug ed errori

The following code has some bugs that you can fix using the Visual Studio IDE. L'app è una semplice app che simula il recupero di dati JSON da un'operazione, la deserializzazione dei dati in un oggetto e l'aggiornamento di un elenco semplice con i nuovi dati.

Per creare l'app:

1. È necessario che sia installato Visual Studio e che sia **lo sviluppo multipiattaforma .NET Core** o il carico di lavoro di sviluppo desktop **.NET,** a seconda del tipo di app che si desidera creare.

    Se Visual Studio non è già stato installato, passare alla pagina dei [download](https://visualstudio.microsoft.com/downloads/) di Visual Studio per installarlo gratuitamente.

    Se è necessario installare il carico di lavoro ma si dispone già di Visual Studio, fare clic su **Strumenti** > **Get Tools and Features**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere il carico di lavoro di **sviluppo multipiattaforma .NET Core** o **.NET,** quindi scegliere **Modifica**.

1. Aprire Visual Studio.

    ::: moniker range=">=vs-2019"
    Nella finestra di avvio scegliere **Crea un nuovo progetto.** Digitare **console** nella casella di ricerca e quindi scegliere **App console (.NET Core)** o **App console (.NET Framework)**. Scegliere **Avanti**. Digitare un nome di progetto come **Console_Parse_JSON** e fare clic su **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Dalla barra dei menu superiore, scegliere **File** > **Nuovo** > **progetto**. Nel riquadro sinistro della finestra di dialogo **Nuovo progetto,** in **Visual C,** scegliere **App console**e quindi nel riquadro centrale scegliere App **console (.NET Core)** o **App console (.NET Framework)**. Digitare un nome come **Console_Parse_JSON** e fare clic su **OK**.
    ::: moniker-end

    Se il modello di progetto **App console (.NET Core)** o **App console (.NET Framework),** passare a **Strumenti** > **Get Tools and Features**, che consente di aprire il programma di installazione di Visual Studio. Scegliere **lo sviluppo multipiattaforma .NET Core** o il carico di lavoro di sviluppo desktop **.NET,** quindi scegliere **Modifica**.

    Visual Studio crea il progetto della console che viene visualizzato nel riquadro destro di Esplora soluzioni.

1. Sostituire il codice predefinito nel file *di Program.cs* del progetto con il codice di esempio riportato di seguito.

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

## <a name="find-the-red-and-green-squiggles"></a>Trova gli scarabocchi rossi e verdi!

Prima di provare ad avviare l'app di esempio ed eseguire il debugger, controllare il codice nell'editor di codice per le scarabocchie rosse e verdi. Questi rappresentano errori e avvisi identificati dall'analizzatore di codice dell'IDE. Le tabelle ondulazioni rosse sono errori in fase di compilazione, che è necessario correggere prima di eseguire il codice. Le ondulazioni verdi sono avvisi. Anche se spesso è possibile eseguire l'app senza correggere gli avvisi, possono essere una fonte di bug e spesso si risparmia tempo e problemi analizzandoli. Questi avvisi ed errori vengono visualizzati anche nella finestra **Elenco errori,** se si preferisce una visualizzazione elenco.

Nell'app di esempio vengono visualizzati diversi scarabocchi rossi che è necessario correggere e uno verde che verrà esaminato. Ecco il primo errore.

![Errore visualizzato come onda rossa](../debugger/media/write-better-code-red-squiggle.png)

Per correggere questo errore, verrà esaminare un'altra funzionalità dell'IDE, rappresentato dall'icona lampadina.

## <a name="check-the-light-bulb"></a>Controlla la lampadina!

La prima ondulata rossa rappresenta un errore in fase di compilazione. Passare il mouse su ```The name `Encoding` does not exist in the current context```di esso e viene visualizzato il messaggio .

Si noti che questo errore mostra un'icona a forma di lampadina in basso a sinistra. Insieme con l'icona ![](../ide/media/screwdriver-icon.png)screwdriver screwdriver , l'icona ![](../ide/media/light-bulb-icon.png) lampadina icona lampadina rappresenta azioni rapide che consentono di correggere o refactoring codice inline. La lampadina rappresenta i problemi che è *necessario* risolvere. Il cacciavite è per i problemi che si potrebbe scegliere di risolvere. Utilizzare la prima correzione suggerita per risolvere l'errore facendo clic su **System.Text** a sinistra.

![Utilizzare la lampadina per correggere il codice](../debugger/media/write-better-code-missing-include.png)

Quando si fa clic su `using System.Text` questo elemento, Visual Studio aggiunge l'istruzione nella parte superiore del file *di Program.cs* e la linea ondulata rossa scompare. Quando non sei sicuro di cosa funzionerà per una correzione suggerita, scegli il link **Anteprima modifiche** a destra prima di applicare la correzione.

L'errore precedente è comune che in genere `using` si correla aggiungendo una nuova istruzione al codice. Esistono diversi errori comuni e simili ```The type or namespace `Name` cannot be found.``` a questo, ad esempio Questi tipi di errori possono indicare un riferimento all'assembly mancante (fare clic con il pulsante destro del mouse sul progetto, scegliere **Aggiungi** > **riferimento**), un nome con errori di ortografia o una libreria mancante che è necessario aggiungere (per C, fare clic con il pulsante destro del mouse sul progetto e scegliere Gestisci **pacchetti NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Correggere gli errori e gli avvisi rimanenti

Ci sono un paio di linee a zigzag da guardare in questo codice. In questo caso, viene visualizzato un errore di conversione del tipo comune. Quando si passa il puntatore del mouse sulla modalità ondulata, si nota che il codice sta tentando di convertire una stringa in un int, che non è supportato a meno che non si aggiunge codice esplicito per effettuare la conversione.

![Errore di conversione del tipo](../debugger/media/write-better-code-conversion-error.png)

Poiché l'analizzatore di codice non può indovinare il vostro intento, non ci sono lampadine per aiutarvi questa volta. Per correggere questo errore, è necessario conoscere lo scopo del codice. In questo esempio, non è troppo difficile `points` vedere che dovrebbe essere un valore numerico `points` `totalpoints`(intero), poiché si sta tentando di aggiungere a .

Per correggere questo errore, modificare il `points` membro della `User` classe da questo:

```csharp
[DataMember]
internal string points;
```

con questo:

```csharp
[DataMember]
internal int points;
```

Le righe rosse ondulate nell'editor di codice vanno via.

Successivamente, passare il mouse sulla linea ondulata verde nella dichiarazione del `points` membro dati. L'analizzatore di codice indica che alla variabile non viene mai assegnato un valore.

![Messaggio di avviso per variabile non assegnata](../debugger/media/write-better-code-warning-message.png)

In genere, questo rappresenta un problema che deve essere risolto. Tuttavia, nell'app di esempio si `points` archiviano effettivamente i dati nella variabile `totalpoints` durante il processo di deserializzazione e quindi si aggiunge tale valore al membro dati. In questo esempio, si conosce lo scopo del codice e si può ignorare l'avviso. Tuttavia, se si desidera eliminare l'avviso, è possibile sostituire il codice seguente:However, if you want to eliminate the warning, you can replace the following code:

```csharp
item.totalpoints = users[i].points;
```

con il seguente:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

La carta da fornello verde se ne va.

## <a name="fix-an-exception"></a>Correggere un'eccezioneFix an exception

Dopo aver corretto tutte le scarabocchie rosse e risolto - o almeno studiato - tutte le scarabocchie verdi, sei pronto per avviare il debugger ed eseguire l'app.

Premere **F5** (**Debug > Avvia debug**) o il pulsante Avvia **debug** nella barra degli strumenti Debug. ![Start Debugging](../debugger/media/dbg-tour-start-debugging.png "Avvia debug")

A questo punto, l'app `SerializationException` di esempio genera un'eccezione (un errore di runtime). Ovvero, l'app soffoca i dati che sta tentando di serializzare. Poiché l'app è stata avviata in modalità di debug (debugger collegato), l'helper eccezioni del debugger consente di accedere direttamente al codice che ha generato l'eccezione e fornisce un messaggio di errore utile.

![Si verifica un'eccezione SerializationException](../debugger/media/write-better-code-serialization-exception.png)

Il messaggio di errore indica `4o` che il valore non può essere analizzato come un numero intero. Quindi, in questo esempio, sai che `4o` i `40`dati sono cattivi: dovrebbe essere . Tuttavia, se non si ha il controllo dei dati in uno scenario reale (diciamo che li stai ricevendo da un servizio web), cosa si fa al riguardo? Come si fa a risolvere questo problema?

Quando si colpisce un'eccezione, è necessario porre (e rispondere) un paio di domande:

* Si tratta solo di un bug che è possibile correggere? Oppure

* Si tratta di un'eccezione che gli utenti potrebbero incontrare?

Se è il primo, correggere il bug. (Nell'app di esempio, ciò significa correggere i dati non riusciti.) In questo caso, potrebbe essere necessario gestire l'eccezione `try/catch` nel codice usando un blocco (esaminiamo altre possibili strategie nella sezione successiva). Nell'app di esempio sostituire il codice seguente:In the sample app, replace the following code:

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

Un `try/catch` blocco ha un certo costo di prestazioni, quindi ti consigliamo di usarli solo quando ne hai realmente bisogno, cioè dove (a) potrebbero verificarsi nella versione di rilascio dell'app e dove (b) la documentazione per il metodo indica che è necessario verificare l'eccezione (supponendo che la documentazione sia completa!). In molti casi, è possibile gestire un'eccezione in modo appropriato e l'utente non avrà mai bisogno di conoscerla.

Ecco un paio di suggerimenti importanti per la gestione delle eccezioni:Here are a couple of important tips for exception handling:

* Evitare di utilizzare un `catch (Exception) {}`blocco catch vuoto, ad esempio , che non esegue l'azione appropriata per esporre o gestire un errore. Un blocco catch vuoto o non informativo può nascondere le eccezioni e può rendere il codice più difficile da eseguire il debug anziché più semplice.

* Usa `try/catch` il blocco intorno alla funzione specifica`ReadObject`che genera l'eccezione ( , nell'app di esempio). Se lo si utilizza intorno a un blocco di codice più grande, si finisce per nascondere la posizione dell'errore. Ad esempio, non utilizzare `try/catch` il blocco intorno alla `ReadToObject`chiamata alla funzione padre , illustrato di seguito, altrimenti non si conosce esattamente dove si è verificata l'eccezione.

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

* Per le funzioni sconosciute incluse nell'app, in particolare quelle che interagiscono con dati esterni (ad esempio una richiesta Web), consulta la documentazione per vedere quali eccezioni è probabile che la funzione generi. Queste possono essere informazioni critiche per una corretta gestione degli errori e per il debug dell'app.

Per l'app di `SerializationException` esempio, correggere `4o` `40`il metodo in modificando il `GetJsonData` metodo in .

## <a name="clarify-your-code-intent-by-using-assert"></a>Chiarire l'intento di codice usando l'asserzione

Fare clic sul pulsante **Riavvia** ![app di riavvio](../debugger/media/dbg-tour-restart.png "App di riavvio") nella barra degli strumenti Debug **(CTRL** + **Maiusc** + **F5**). Questa operazione riavvia l'app in meno passaggi. Viene visualizzato il seguente output nella finestra della console.

![Valore Null nell'outputNull value in output](../debugger/media/write-better-code-using-assert-null-output.png)

Si può vedere qualcosa in questo output che non è del tutto giusto. **nome** e **cognome** per il terzo record sono vuoti!

Questo è un buon momento per parlare di una pratica di `assert` codifica utile, spesso sottoutilizzato, che è quello di utilizzare le istruzioni nelle funzioni. Aggiungendo il codice seguente, si include un `firstname` controllo `lastname` di `null`runtime per assicurarsi che e non siano . Sostituire il codice `UpdateRecords` seguente nel metodo:

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

Aggiungendo `assert` istruzioni come questa alle funzioni durante il processo di sviluppo, è possibile specificare lo scopo del codice. Nell'esempio precedente, specifichiamo quanto segue:

* È necessaria una stringa valida per il nome
* È necessaria una stringa valida per il cognome

Specificando la finalità in questo modo, si applicano i requisiti. Questo è un metodo semplice e pratico che è possibile utilizzare per far emergere i bug durante lo sviluppo. (le`assert` istruzioni vengono utilizzate anche come elemento principale negli unit test.)

Fare clic sul pulsante **Riavvia** ![app di riavvio](../debugger/media/dbg-tour-restart.png "App di riavvio") nella barra degli strumenti Debug **(CTRL** + **Maiusc** + **F5**).

> [!NOTE]
> Il `assert` codice è attivo solo in una build di debug.

Al riavvio, il debugger `assert` si ferma sull'istruzione, poiché l'espressione `users[i].firstname != null` restituisce `false` anziché . `true`

![Assert si risolve in falseAssert resolves to false](../debugger/media/write-better-code-using-assert.png)

L'errore `assert` indica che è necessario analizzare il problema. `assert`può coprire molti scenari in cui non si vede necessariamente un'eccezione. In questo esempio, l'utente non vedrà `null` un'eccezione e viene aggiunto un valore come `firstname` nell'elenco di record. Ciò potrebbe causare problemi in un secondo momento (come si vede nell'output della console) e potrebbe essere più difficile eseguire il debug.

> [!NOTE]
> Negli scenari in cui si `null` chiama `NullReferenceException` un metodo sul valore, un risultato. In genere si desidera `try/catch` evitare di utilizzare un blocco per un'eccezione generale, ovvero un'eccezione che non è legata alla funzione di libreria specifica. Qualsiasi oggetto può `NullReferenceException`generare un oggetto . Se non si è sicuri, consultare la documentazione relativa alla funzione di libreria.

Durante il processo di debug, è `assert` bene mantenere una particolare istruzione fino a quando non si sa che è necessario sostituirla con una correzione effettiva del codice. Supponiamo che tu decida di decidere che l'utente potrebbe riscontrare l'eccezione in una build di rilascio dell'app. In tal caso, è necessario effettuare il refactoring del codice per assicurarsi che l'app non generi un'eccezione irreversibile o generi un altro errore. Quindi, per correggere questo codice, sostituire il codice seguente:

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

Utilizzando questo codice, si soddisfano i requisiti del `firstname` codice `lastname` e `null` assicurarsi che un record con un o valore di non viene aggiunto ai dati.

In questo esempio sono `assert` state aggiunte le due istruzioni all'interno di un ciclo. In genere, `assert`quando si utilizza `assert` , è consigliabile aggiungere istruzioni nel punto di ingresso (inizio) di una funzione o di un metodo. Si sta esaminando `UpdateRecords` il metodo nell'app di esempio. In questo metodo, si sa che si è `null`in difficoltà se `assert` uno degli argomenti del metodo è , quindi controllarli entrambi con un'istruzione nel punto di ingresso della funzione.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Per le istruzioni precedenti, lo scopo è caricare`db`i dati esistenti`users`( ) e recuperare nuovi dati ( ) prima di aggiornare qualsiasi elemento.

È possibile `assert` utilizzare con qualsiasi tipo `true` di `false`espressione che si risolve in o . Così, per esempio, è `assert` possibile aggiungere un'istruzione come questa.

```csharp
Debug.Assert(users[0].points > 0);
```

Il codice precedente è utile se si desidera specificare la finalità seguente: è necessario un nuovo valore di punto maggiore di zero (0) per aggiornare il record dell'utente.

## <a name="inspect-your-code-in-the-debugger"></a>Esaminare il codice nel debuggerInspect your code in the debugger

OK, ora che hai risolto tutto ciò che è critico che è sbagliato con l'applicazione di esempio, è possibile passare ad altre cose importanti!

È stato illustrato l'helper eccezioni del debugger, ma il debugger è uno strumento molto più potente che consente anche di eseguire altre operazioni, ad esempio un'istruzione alla volta nel codice e di esaminarne le variabili. Queste funzionalità più potenti sono utili in molti scenari, in particolare le seguenti:

* Si sta tentando di isolare un bug di runtime nel codice, ma non è possibile farlo utilizzando metodi e strumenti descritti in precedenza.

* Si desidera convalidare il codice, ovvero guardarlo mentre viene eseguito per assicurarsi che si comporti nel modo desiderato e che si esegua quello desiderato.

    È istruttivo osservare il codice durante l'esecuzione. È possibile ottenere ulteriori informazioni sul codice in questo modo e spesso identificare i bug prima che manifestino sintomi evidenti.

Per informazioni su come utilizzare le funzionalità essenziali del debugger, vedere [Debug per principianti assoluti](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Correggi problemi di prestazioni

Bug di altro tipo includono codice inefficiente che causa una lentezza dell'esecuzione dell'app o un utilizzo eccessivo della memoria. In genere, l'ottimizzazione delle prestazioni è un'operazione che viene effettuata più avanti nello sviluppo dell'app. Tuttavia, puoi riscontrare problemi di prestazioni in anticipo (ad esempio, si nota che una parte dell'app è lenta) e potrebbe essere necessario testare l'app con gli strumenti di profilatura nelle prime fasi. Per ulteriori informazioni sugli strumenti di profilatura, ad esempio lo strumento Utilizzo CPU e Analizzatore memoria, vedere Prima di tutto esaminare gli strumenti di [profilatura](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Passaggi successivi

In questo articolo viene illustrato come evitare e correggere molti bug comuni nel codice e quando usare il debugger. Successivamente, ulteriori informazioni sull'utilizzo del debugger di Visual Studio per correggere i bug.

> [!div class="nextstepaction"]
> [Debug per principianti](../debugger/debugging-absolute-beginners.md)
