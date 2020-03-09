---
title: Tecniche e strumenti di debug CRT
description: Scrivi codice migliore con meno bug usando Visual Studio per correggere le eccezioni, correggere gli errori e migliorare il codice
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
ms.sourcegitcommit: 3154387056160bf4c36ac8717a7fdc0cd9faf3f9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78409228"
---
# <a name="debugging-techniques-and-tools-to-help-you-write-better-code"></a>Tecniche e strumenti di debug che consentono di scrivere codice migliore

La correzione di bug ed errori nel codice può richiedere molto tempo e talvolta frustrante--attività. È necessario tempo per apprendere come eseguire il debug in modo efficace, ma un IDE potente come Visual Studio può semplificare notevolmente il processo. Un IDE può essere utile per correggere gli errori ed eseguire il debug del codice più rapidamente, ma non solo per questo, ma può anche essere utile per scrivere codice migliore con meno bug. Lo scopo di questo articolo è fornire una visualizzazione olistica del processo di correzione dei bug, per cui si saprà quando utilizzare l'analizzatore di codice, quando utilizzare il debugger, come correggere le eccezioni e come scrivere codice per finalità. Se si sa già che è necessario usare il debugger, vedere [la prima occhiata al debugger](../debugger/debugger-feature-tour.md).

Questo articolo illustra come sfruttare l'IDE per rendere più produttivi le sessioni di codifica. Si toccano diverse attività, ad esempio:

* Preparare il codice per il debug sfruttando l'analizzatore del codice dell'IDE

* Come correggere le eccezioni (errori di run-time)

* Come ridurre al minimo i bug mediante la codifica per finalità (mediante Assert)

* Quando utilizzare il debugger

Per illustrare queste attività, vengono illustrati alcuni dei tipi più comuni di errori e bug che si verificheranno quando si tenta di eseguire il debug delle app. Sebbene il codice di esempio C#sia, le informazioni concettuali sono generalmente applicabili C++a, Visual Basic, JavaScript e altri linguaggi supportati da Visual Studio, ad eccezione dei casi indicati. Gli screenshot sono in linguaggio C#.

## <a name="create-a-sample-app-with-some-bugs-and-errors-in-it"></a>Creare un'app di esempio con alcuni bug ed errori

Il codice seguente presenta alcuni bug che è possibile correggere usando l'IDE di Visual Studio. L'app è una semplice app che simula il recupero di dati JSON da un'operazione, la deserializzazione dei dati in un oggetto e l'aggiornamento di un elenco semplice con i nuovi dati.

Per creare l'app:

1. È necessario che Visual Studio sia installato e che sia installato lo **sviluppo multipiattaforma .NET Core** o il carico di lavoro sviluppo di applicazioni **desktop .NET** , a seconda del tipo di app che si vuole creare.

    Se Visual Studio non è ancora installato, accedere alla pagina  [Download di Visual Studio](https://visualstudio.microsoft.com/downloads/)  per installarlo gratuitamente.

    Per installare il carico di lavoro avendo già Visual Studio, fare clic su **Strumenti** > **Ottieni strumenti e funzionalità**. Verrà avviato il Programma di installazione di Visual Studio. Scegliere lo **sviluppo multipiattaforma .NET Core** o il carico di lavoro sviluppo di applicazioni **desktop .NET** , quindi scegliere **modifica**.

1. Aprire Visual Studio.

    ::: moniker range=">=vs-2019"
    Nella finestra iniziale scegliere **Crea un nuovo progetto**. Digitare **console** nella casella di ricerca e quindi scegliere **app console (.NET Core)** o **app console (.NET Framework)** . Scegliere **Avanti**. Digitare un nome di progetto come **Console_Parse_JSON** e fare clic su **Crea**.
    ::: moniker-end
    ::: moniker range="vs-2017"
    Nella barra dei menu scegliere **File** > **Nuovo** > **Progetto**. Nel riquadro sinistro della finestra di dialogo **nuovo progetto** , in oggetto **visivo C#** , scegliere **app console**, quindi nel riquadro centrale scegliere app **Console (.NET Core)** o **app console (.NET Framework)** . Digitare un nome come **Console_Parse_JSON** e fare clic su **OK**.
    ::: moniker-end

    Se non viene visualizzato il modello di progetto **app console (.NET Core)** o **app console (.NET Framework)** , passare a **strumenti** > **ottenere strumenti e funzionalità**, che consente di aprire il programma di installazione di Visual Studio. Scegliere lo **sviluppo multipiattaforma .NET Core** o il carico di lavoro sviluppo di applicazioni **desktop .NET** , quindi scegliere **modifica**.

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

## <a name="find-the-red-and-green-squiggles"></a>Trovare il controllo ortografia durante rosso e verde.

Prima di provare ad avviare l'app di esempio ed eseguire il debugger, controllare il codice nell'editor di codice per il controllo ortografia durante rosso e verde. Rappresentano gli errori e gli avvisi identificati dall'analizzatore del codice dell'IDE. Il controllo ortografia durante rosso è costituito da errori in fase di compilazione, che è necessario correggere prima di poter eseguire il codice. Il controllo ortografia durante verde sono avvisi. Sebbene sia spesso possibile eseguire l'app senza correggere gli avvisi, questi possono costituire un'origine di bug e spesso si risparmiano tempo e problemi esaminando questi ultimi. Gli avvisi e gli errori vengono visualizzati anche nella finestra di **Elenco errori** , se si preferisce una visualizzazione elenco.

Nell'app di esempio vengono visualizzati diversi controllo ortografia durante rossi che è necessario correggere e uno verde che verrà esaminato. Ecco il primo errore.

![Errore visualizzato come zigzag rosso](../debugger/media/write-better-code-red-squiggle.png)

Per correggere l'errore, è possibile esaminare un'altra funzionalità dell'IDE, rappresentata dall'icona lampadina.

## <a name="check-the-light-bulb"></a>Controllare la lampadina.

Il primo zigzag rosso rappresenta un errore in fase di compilazione. Posizionare il puntatore del mouse su di esso per visualizzare il messaggio ```The name `Encoding` does not exist in the current context```.

Si noti che questo errore Mostra un'icona a forma di lampadina in basso a sinistra. Insieme all'icona del cacciavite ![icona del cacciavite](../ide/media/screwdriver-icon.png), l'icona a forma di lampadina ![icona a forma di lampadina](../ide/media/light-bulb-icon.png) rappresenta azioni rapide che consentono di correggere o effettuare il refactoring del codice inline. Il bulbo di luce rappresenta i problemi che è *necessario* correggere. Il cacciavite è per i problemi che è possibile scegliere di correggere. Per risolvere l'errore, usare la prima correzione consigliata facendo clic su **using System. Text (sistema** ) a sinistra.

![Usare la lampadina per correggere il codice](../debugger/media/write-better-code-missing-include.png)

Quando si fa clic su questo elemento, Visual Studio aggiunge l'istruzione `using System.Text` nella parte superiore del file *Program.cs* e la zigzag rossa scompare. Se non si è certi di quale sia la correzione suggerita, scegliere il collegamento **Anteprima modifiche** a destra prima di applicare la correzione.

L'errore precedente è quello comune che in genere si corregge aggiungendo una nuova istruzione `using` al codice. Esistono diversi errori comuni e simili a questo, ad esempio ```The type or namespace `Name` cannot be found.``` questi tipi di errori potrebbero indicare un riferimento a un assembly mancante (fare clic con il pulsante destro del mouse sul progetto, scegliere **aggiungi** > **riferimento**), un nome digitato in modo errato o una libreria C#mancante che è necessario aggiungere (per, fare clic con il pulsante destro del mouse sul progetto e scegliere **Gestisci pacchetti NuGet**).

## <a name="fix-the-remaining-errors-and-warnings"></a>Correggere gli errori e gli avvisi rimanenti

Ci sono altri controllo ortografia durante da esaminare in questo codice. Viene visualizzato un errore di conversione del tipo comune. Quando si passa il mouse su zigzag, si noterà che il codice sta provando a convertire una stringa in un valore int, che non è supportato a meno che non si aggiunga codice esplicito per eseguire la conversione.

![Errore di conversione del tipo](../debugger/media/write-better-code-conversion-error.png)

Poiché l'analizzatore del codice non è in grado di indovinare lo scopo, non sono disponibili lampadine che consentano di risolvere questo problema. Per correggere l'errore, è necessario conoscerne lo scopo. In questo esempio non è troppo difficile vedere che `points` deve essere un valore numerico (Integer), perché si sta tentando di aggiungere `points` a `totalpoints`.

Per correggere l'errore, modificare il membro `points` della classe `User` da questo:

```csharp
[DataMember]
internal string points;
```

con questo:

```csharp
[DataMember]
internal int points;
```

Le linee ondulate rosse nell'editor di codice vengono eliminate.

Passare quindi il puntatore sul zigzag verde nella dichiarazione del membro dati `points`. L'analizzatore di codice indica che alla variabile non viene mai assegnato un valore.

![Messaggio di avviso per la variabile non assegnata](../debugger/media/write-better-code-warning-message.png)

In genere, questo rappresenta un problema che deve essere corretto. Nell'app di esempio è tuttavia possibile archiviare i dati nella variabile `points` durante il processo di deserializzazione, quindi aggiungere tale valore al membro dati `totalpoints`. In questo esempio si conosce lo scopo del codice e si può tranquillamente ignorare l'avviso. Tuttavia, se si desidera eliminare l'avviso, è possibile sostituire il codice seguente:

```csharp
item.totalpoints = users[i].points;
```

con il seguente:

```csharp
item.points = users[i].points;
item.totalpoints += users[i].points;
```

Il zigzag verde va fuori.

## <a name="fix-an-exception"></a>Correggi un'eccezione

Quando sono state corrette tutte le controllo ortografia durante rosse e risolte, o almeno esaminate, tutte le controllo ortografia durante verdi, si è pronti per avviare il debugger ed eseguire l'app.

Premere **F5** (**debug > Avvia debug**) o il pulsante **Avvia debug** ![Avvia](../debugger/media/dbg-tour-start-debugging.png "Avvia debug") debug sulla barra degli strumenti Debug.

A questo punto, l'app di esempio genera un'eccezione `SerializationException` (un errore di Runtime). Ovvero, l'app viene soffocata sui dati che sta provando a serializzare. Poiché l'app è stata avviata in modalità di debug (debugger collegato), l'helper eccezioni del debugger consente di eseguire direttamente il codice che ha generato l'eccezione e fornisce un messaggio di errore utile.

![Si verifica un'operazione di serializzazione](../debugger/media/write-better-code-serialization-exception.png)

Il messaggio di errore indica che non è possibile analizzare il valore `4o` come Integer. Quindi, in questo esempio, si sa che i dati sono errati: `4o` dovrebbe essere `40`. Tuttavia, se non si ha il controllo dei dati in uno scenario reale (ad indicare che si sta ricevendo da un servizio Web), cosa è possibile fare? In che modo è possibile risolvere il problema?

Quando si verifica un'eccezione, è necessario chiedere (e rispondere) a un paio di domande:

* Questa eccezione è solo un bug che è possibile correggere? Oppure

* Si tratta di un'eccezione che può verificarsi per gli utenti?

Se è il primo, correggere il bug. Nell'app di esempio significa correggere i dati non validi. Se è il secondo, potrebbe essere necessario gestire l'eccezione nel codice usando un blocco di `try/catch` (si osserveranno altre strategie possibili nella sezione successiva). Nell'app di esempio sostituire il codice seguente:

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

Un blocco `try/catch` comporta un certo costo in termini di prestazioni, quindi è consigliabile usarli solo quando sono effettivamente necessari, ovvero dove (a) potrebbero essere presenti nella versione di rilascio dell'app e dove (b) la documentazione per il metodo indica che è necessario verificare l'eccezione (presupponendo che la documentazione sia stata completata). In molti casi, è possibile gestire un'eccezione in modo appropriato e non sarà mai necessario che l'utente ne sia a conoscenza.

Ecco alcuni suggerimenti importanti per la gestione delle eccezioni:

* Evitare di utilizzare un blocco catch vuoto, ad esempio `catch (Exception) {}`, che non esegue l'azione appropriata per esporre o gestire un errore. Un blocco catch vuoto o non informativo può nascondere le eccezioni e rendere il codice più difficile da eseguire il debug anziché più semplice.

* Usare il blocco `try/catch` intorno alla funzione specifica che genera l'eccezione (`ReadObject`nell'app di esempio). Se lo si usa per un blocco di codice più ampio, viene nascosta la posizione dell'errore. Ad esempio, non usare il blocco `try/catch` per la chiamata alla funzione padre `ReadToObject`, illustrato di seguito oppure non si conosce esattamente dove si è verificata l'eccezione.

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

* Per le funzioni non note incluse nell'app, in particolare quelle che interagiscono con i dati esterni (ad esempio una richiesta Web), controllare la documentazione per visualizzare le eccezioni che la funzione può generare. Può trattarsi di informazioni critiche per la corretta gestione degli errori e per il debug dell'app.

Per l'app di esempio, correggere il `SerializationException` nel metodo `GetJsonData` cambiando `4o` in `40`.

## <a name="clarify-your-code-intent-by-using-assert"></a>Chiarire l'intenzione del codice tramite Assert

Fare clic sul pulsante **Riavvia** ![app riavvia](../debugger/media/dbg-tour-restart.png "RestartApp") sulla barra degli strumenti Debug (**CTRL** + **MAIUSC** + **F5**). Questa operazione riavvia l'app in un minor numero di passaggi. Nella finestra della console viene visualizzato l'output seguente.

![Valore null nell'output](../debugger/media/write-better-code-using-assert-null-output.png)

In questo output è possibile visualizzare un elemento che non è abbastanza adatto. il **nome** e il **Cognome** per il terzo record sono vuoti.

Questo è il momento giusto per illustrare una procedura di codifica utile, spesso sottoutilizzata, che consiste nell'usare `assert` istruzioni nelle funzioni. Aggiungendo il codice seguente, si include un controllo di runtime per assicurarsi che `firstname` e `lastname` non siano `null`. Sostituire il codice seguente nel metodo `UpdateRecords`:

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

Con l'aggiunta di `assert` istruzioni come questa alle funzioni durante il processo di sviluppo, è possibile specificare lo scopo del codice. Nell'esempio precedente, viene specificato quanto segue:

* Per il primo nome è necessaria una stringa valida
* Per il cognome è necessaria una stringa valida

Specificando Intent in questo modo, si applicano le proprie esigenze. Si tratta di un metodo semplice e pratico che è possibile utilizzare per la superficie dei bug durante lo sviluppo. (le istruzioni`assert` vengono utilizzate anche come elemento principale negli unit test.)

Fare clic sul pulsante **Riavvia** ![app riavvia](../debugger/media/dbg-tour-restart.png "RestartApp") sulla barra degli strumenti Debug (**CTRL** + **MAIUSC** + **F5**).

> [!NOTE]
> Il codice `assert` è attivo solo in una build di debug.

Quando si riavvia, il debugger viene sospeso sull'istruzione `assert`, perché l'espressione `users[i].firstname != null` restituisce `false` anziché `true`.

![Assert viene risolto in false](../debugger/media/write-better-code-using-assert.png)

Il `assert` errore indica che è necessario esaminare il problema. `assert` possono coprire molti scenari in cui non viene necessariamente visualizzata un'eccezione. In questo esempio, l'utente non visualizzerà un'eccezione e un valore `null` verrà aggiunto come `firstname` nell'elenco di record. Questo può causare problemi in un secondo momento, ad esempio nell'output della console, e potrebbe risultare più difficile eseguire il debug.

> [!NOTE]
> Negli scenari in cui si chiama un metodo sul valore `null`, un `NullReferenceException` risultati. In genere è consigliabile evitare di utilizzare un blocco `try/catch` per un'eccezione generale, ovvero un'eccezione non associata alla funzione di libreria specifica. Qualsiasi oggetto può generare un `NullReferenceException`. Se non si è certi, controllare la documentazione relativa alla funzione di libreria.

Durante il processo di debug, è opportuno tenere una specifica `assert` istruzione fino a quando non si sa che è necessario sostituirla con una correzione del codice reale. Si supponga di decidere che l'utente può riscontrare l'eccezione in una build di rilascio dell'app. In tal caso, è necessario effettuare il refactoring del codice per assicurarsi che l'app non generi un'eccezione irreversibile o provochi un altro errore. Quindi, per correggere questo codice, sostituire il codice seguente:

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

Utilizzando questo codice, si soddisfano i requisiti del codice e si verifica che un record con un valore `firstname` o `lastname` di `null` non venga aggiunto ai dati.

In questo esempio sono state aggiunte le due istruzioni `assert` all'interno di un ciclo. In genere, quando si usa `assert`, è consigliabile aggiungere istruzioni `assert` nel punto di ingresso (inizio) di una funzione o di un metodo. Si sta esaminando attualmente il metodo `UpdateRecords` nell'app di esempio. In questo metodo, si sa che si verificano problemi se uno degli argomenti del metodo è `null`, quindi è necessario verificarli entrambi con un'istruzione `assert` nel punto di ingresso della funzione.

```csharp
public static void UpdateRecords(List<User> db, User[] users)
{
    Debug.Assert(db != null);
    Debug.Assert(users != null);
```

Per le istruzioni precedenti, lo scopo è quello di caricare i dati esistenti (`db`) e recuperare i nuovi dati (`users`) prima di aggiornare qualsiasi elemento.

È possibile utilizzare `assert` con qualsiasi tipo di espressione che viene risolta in `true` o `false`. Quindi, ad esempio, è possibile aggiungere un'istruzione `assert` come questa.

```csharp
Debug.Assert(users[0].points > 0);
```

Il codice precedente è utile se si desidera specificare la seguente finalità: per aggiornare il record dell'utente è necessario un nuovo valore punto maggiore di zero (0).

## <a name="inspect-your-code-in-the-debugger"></a>Esaminare il codice nel debugger

A questo punto, dopo aver risolto tutti i problemi critici relativi all'app di esempio, è possibile passare ad altre cose importanti.

È stato illustrato l'helper eccezioni del debugger, ma il debugger è uno strumento molto più potente che consente anche di eseguire altre operazioni, ad esempio eseguire un'istruzione alla volta nel codice e ispezionarne le variabili. Queste funzionalità più potenti sono utili in molti scenari, in particolare quanto segue:

* Si sta tentando di isolare un bug di runtime nel codice, ma non è possibile farlo usando metodi e strumenti descritti in precedenza.

* Si vuole convalidare il codice, ovvero guardarlo mentre è in esecuzione per assicurarsi che si stia comportando nel modo previsto ed eseguendo le operazioni desiderate.

    È istruttivo tenere sotto controllo il codice durante l'esecuzione. È possibile ottenere altre informazioni sul codice in questo modo ed è spesso in grado di identificare i bug prima che manifestino eventuali sintomi evidenti.

Per informazioni su come usare le funzionalità essenziali del debugger, vedere [debug per principianti assoluti](../debugger/debugging-absolute-beginners.md).

## <a name="fix-performance-issues"></a>Correggi problemi di prestazioni

I bug di un altro tipo includono codice inefficiente che causa l'esecuzione lenta dell'app o l'utilizzo di una quantità eccessiva di memoria. In genere, l'ottimizzazione delle prestazioni è un'operazione che si esegue in un secondo momento nello sviluppo di app. Tuttavia, è possibile che si verifichino problemi di prestazioni tempestivamente (ad esempio, si noterà che una parte dell'app è in esecuzione lenta) e potrebbe essere necessario testare l'app con gli strumenti di profilatura in anticipo. Per altre informazioni sugli strumenti di profilatura, ad esempio lo strumento utilizzo CPU e l'analizzatore memoria, vedere [prima di tutto gli strumenti di profilatura](../profiling/profiling-feature-tour.md).

## <a name="next-steps"></a>Passaggi successivi

In questo articolo si è appreso come evitare e correggere molti bug comuni nel codice e quando utilizzare il debugger. Successivamente, altre informazioni sull'uso del debugger di Visual Studio per correggere i bug.

> [!div class="nextstepaction"]
> [Debug per principianti](../debugger/debugging-absolute-beginners.md)
