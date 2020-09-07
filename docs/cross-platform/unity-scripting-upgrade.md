---
title: Uso di .NET 4.x in Unity
author: therealjohn
ms.author: johmil
ms.date: 08/29/2018
ms.topic: how-to
ms.assetid: E2C9420F-A5D5-4472-9020-2B63FB27A133
ms.technology: vs-unity-tools
ms.workload:
- unity
ms.openlocfilehash: 9a53db2d7cb73fbbb8ea694386dbada3186957ee
ms.sourcegitcommit: 5caad925ca0b5d136416144a279e984836d8f28c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/07/2020
ms.locfileid: "89508977"
---
# <a name="using-net-4x-in-unity"></a>Uso di .NET 4.x in Unity

C# e .NET, le tecnologie sottostanti alle funzionalità di scripting Unity, continuano a essere aggiornate sin dal rilascio originale di Microsoft nel 2002. Gli sviluppatori Unity potrebbero però non essere a conoscenza del flusso costante di nuove funzionalità aggiunte per il linguaggio C# e .NET Framework. Questo perché prima di Unity 2017.1, Unity ha usato un runtime di scripting equivalente a .NET 3.5, perdendo anni di aggiornamenti.

Con il rilascio di Unity 2017.1, Unity ha introdotto una versione sperimentale del runtime di scripting aggiornata a una versione compatibile con .NET 4.6 e C# 6. In Unity 2018.1, il runtime equivalente di .NET 4.x non è più considerato sperimentale, mentre il runtime equivalente a .NET 3.5 precedente viene ora considerato la versione legacy. Con il rilascio di Unity 2018.3, Unity progetta di rendere il runtime di scripting aggiornato la selezione predefinita con ulteriori aggiornamenti a C# 7. Per altre informazioni e indicazioni sugli aggiornamenti più recenti, leggere questo [post di blog](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/) di Unity oppure visitare il [forum dedicato alle anteprime di scripting sperimentali](https://forum.unity.com/forums/experimental-scripting-previews.107/). Nel frattempo, consultare le sezioni seguenti per altre informazioni sulle nuove funzionalità ora disponibili con il runtime di scripting .NET 4.x.

## <a name="prerequisites"></a>Prerequisiti

* [Unity 2017.1 o versione successiva](https://unity3d.com/) (consigliata la versione 2018.2)
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download)

## <a name="enabling-the-net-4x-scripting-runtime-in-unity"></a>Abilitazione del runtime di scripting .NET 4.x in Unity

Per abilitare il runtime di scripting .NET 4.x, seguire questa procedura:

1. Aprire PlayerSettings in Unity Inspector selezionando **Edit > Project Settings > Player** (Modifica > Impostazioni progetto > Player).

1. Sotto l'intestazione **Configuration** (Configurazione) fare clic sull'elenco a discesa **Scripting Runtime Version** (Versione runtime di scripting) e selezionare **.NET 4.x Equivalent** (Equivalente a .NET 4.x). Verrà richiesto di riavviare Unity.

![Selezionare l'equivalente di .NET 4.x](media/vstu_scripting-runtime-version.png)

## <a name="choosing-between-net-4x-and-net-standard-20-profiles"></a>Scelta tra i profili .NET 4.x e .NET Standard 2.0

Dopo essere passati al runtime di scripting equivalente a .NET 4.x, è possibile specificare il **livello di compatibilità API** usando il menu a discesa in PlayerSettings: **Edit > Project Settings > Player** (Modifica > Impostazioni progetto > Player). Sono disponibili due opzioni:

* **.NET Standard 2,0**. Questo profilo corrisponde al [profilo .NET Standard 2.0](https://github.com/dotnet/standard/blob/master/docs/versions/netstandard2.0.md) pubblicato da .NET Foundation. Unity consiglia .NET Standard 2.0 per i nuovi progetti. Ha dimensioni minori rispetto a .NET 4.x e ciò rappresenta un vantaggio per le piattaforme con vincoli di dimensioni. Inoltre, Unity si è impegnata a supportare questo profilo in tutte le piattaforme supportate da Unity.

* **.NET 4. x**. Questo profilo consente di accedere all'API .NET 4 più recente. Include tutto il codice disponibile nelle librerie di classi .NET Framework e supporta anche i profili .NET Standard 2.0. Usare il profilo .NET 4.x se il progetto richiede una parte dell'API non inclusa nel profilo .NET Standard 2.0. Tuttavia, alcune parti di questa API potrebbero non essere supportate in tutte le piattaforme di Unity.

Ulteriori informazioni su queste opzioni sono disponibili nel [post di blog](https://blogs.unity3d.com/2018/03/28/updated-scripting-runtime-in-unity-2018-1-what-does-the-future-hold/) di Unity.

### <a name="adding-assembly-references-when-using-the-net-4x-api-compatibility-level"></a>Aggiunta di riferimenti ad assembly quando si usa il livello di compatibilità delle API .NET 4.x

Quando si usa l'impostazione .NET Standard 2.0 nell'elenco a discesa **Api Compatibility Level** (Livello di compatibilità API), tutti gli assembly nel profilo dell'API hanno riferimenti e sono utilizzabili. Tuttavia, quando si usa il profilo più esteso .NET 4.x, alcuni degli assembly forniti da Unity non sono inclusi nei riferimenti per impostazione predefinita. Per usare queste API, è necessario aggiungere manualmente un riferimento all'assembly. È possibile visualizzare gli assembly forniti da Unity nella directory **MonoBleedingEdge/lib/mono** dell'installazione dell'editor di Unity:

![Directory MonoBleedingEdge](media/vstu_monobleedingedge.png)

Ad esempio, se si usa il profilo .NET 4.x e si vuole usare `HttpClient`, è necessario aggiungere un riferimento all'assembly per System.Net.Http.dll. In caso contrario, il compilatore segnalerà che manca un riferimento all'assembly:

![Riferimento all'assembly mancante](media/vstu_missing-reference.png)

Visual Studio rigenera i file con estensione csproj e sln per i progetti Unity ogni volta che vengono aperti. Di conseguenza, non è possibile aggiungere riferimenti ad assembly direttamente in Visual Studio, perché andranno perduti alla riapertura del progetto. È invece necessario usare un file di testo speciale denominato **mcs.rsp**:

1. Creare un nuovo file di testo denominato **mcs.rsp** nella directory **Assets** radice del progetto Unity.

1. Nella prima riga nel file di testo vuoto immettere `-r:System.Net.Http.dll` e quindi salvare il file. È possibile sostituire "System.Net.Http.dll" con qualsiasi assembly incluso per cui potrebbe mancare un riferimento.

1. Riavviare l'editor di Unity.

## <a name="taking-advantage-of-net-compatibility"></a>Vantaggi della compatibilità con .NET

Oltre a una nuova sintassi C# e a nuove funzionalità per il linguaggio, il runtime di scripting .NET 4.x consente agli utenti di Unity di accedere a un'enorme raccolta di pacchetti di .NET che non sono compatibili con il runtime di scripting .NET 3.5 legacy.

### <a name="add-packages-from-nuget-to-a-unity-project"></a>Aggiungere pacchetti da NuGet a un progetto Unity

[NuGet](https://www.nuget.org/) è la gestione pacchetti per .NET. NuGet è integrato in Visual Studio. Tuttavia, i progetti Unity richiedono un processo speciale per l'aggiunta di pacchetti NuGet, necessario perché quando si apre un progetto in Unity, i file di progetto di Visual Studio vengono rigenerati, annullando configurazioni necessarie. Per aggiungere un pacchetto da NuGet al progetto Unity, eseguire le operazioni seguenti:

1. Individuare un pacchetto compatibile da aggiungere in NuGet (.NET Standard 2.0 o .NET 4.x). In questo esempio verrà illustrata l'aggiunta di [Json.NET](https://www.nuget.org/packages/Newtonsoft.Json/), un pacchetto diffuso per l'utilizzo di JSON, a un progetto .NET Standard 2.0.

1. Fare clic sul pulsante **download** :

    ![pulsante download](media/vstu_nuget-download.png)

1. Individuare il file scaricato e modificarne l'estensione da **.nupkg** a **.zip**.

1. All'interno del file ZIP passare alla directory **lib/netstandard2.0** e copiare il file **Newtonsoft.Json.dll**.

1. Nella cartella **Assets** radice del progetto Unity creare una nuova cartella denominata **Plugins**. Plugins è un nome di cartella speciale in Unity. Per altre informazioni, vedere la [documentazione di Unity](https://docs.unity3d.com/Manual/Plugins.html).

1. Incollare il file **Newtonsoft.Json.dll** nella directory **Plugins** del progetto Unity.

1. Creare un file denominato **link.xml** nella directory **Assets** del progetto Unity e aggiungere il codice XML seguente.  Questa operazione assicurerà che il processo di rimozione del bytecode di Unity non rimuova i dati necessari durante l'esportazione in una piattaforma IL2CPP.  Anche se questo passaggio è specifico per questa libreria, è possibile riscontrare problemi con altre librerie che usano la reflection in modo analogo.  Per altre informazioni, vedere la [documentazione di Unity](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html) su questo argomento.

    ```xml
    <linker>
      <assembly fullname="System.Core">
        <type fullname="System.Linq.Expressions.Interpreter.LightLambda" preserve="all" />
      </assembly>
    </linker>
    ```

È ora tutto pronto per usare il pacchetto Json.NET.

```csharp
using Newtonsoft.Json;
using UnityEngine;

public class JSONTest : MonoBehaviour
{
    class Enemy
    {
        public string Name { get; set; }
        public int AttackDamage { get; set; }
        public int MaxHealth { get; set; }
    }
    private void Start()
    {
        string json = @"{
            'Name': 'Ninja',
            'AttackDamage': '40'
            }";

        var enemy = JsonConvert.DeserializeObject<Enemy>(json);

        Debug.Log($"{enemy.Name} deals {enemy.AttackDamage} damage.");
        // Output:
        // Ninja deals 40 damage.
    }
}
```

Si tratta di un semplice esempio dell'uso di una libreria senza dipendenze. Quando i pacchetti NuGet si basano su altri pacchetti NuGet, è necessario scaricare manualmente tali dipendenze e aggiungerle al progetto nello stesso modo.

## <a name="new-syntax-and-language-features"></a>Nuova sintassi e nuove funzionalità del linguaggio

Il runtime di scripting aggiornato consente agli sviluppatori Unity di accedere a C# 6, oltre a numerose nuove funzionalità per il linguaggio e alla nuova sintassi.

### <a name="auto-property-initializers"></a>Inizializzatori di proprietà automatiche

Nel runtime di scripting .NET 3.5 di Unity, la sintassi per le proprietà automatiche consente di definire rapidamente le proprietà non inizializzate, ma l'inizializzazione deve avvenire altrove nello script. Con il runtime .NET 4.x è ora possibile inizializzare le proprietà automatiche nella stessa riga:

```csharp
// .NET 3.5
public int Health { get; set; } // Health has to be initialized somewhere else, like Start()

// .NET 4.x
public int Health { get; set; } = 100;
```

### <a name="string-interpolation"></a>Interpolazione di stringhe

Con il runtime .NET 3.5 precedente, per la concatenazione di stringhe era prevista una sintassi complicata. Ora, con il Runtime .NET 4. x, la funzionalità di [ `$` interpolazione di stringhe](/dotnet/csharp/language-reference/tokens/interpolated) consente di inserire le espressioni in stringhe in una sintassi più diretta e leggibile:

```csharp
// .NET 3.5
Debug.Log(String.Format("Player health: {0}", Health)); // or
Debug.Log("Player health: " + Health);

// .NET 4.x
Debug.Log($"Player health: {Health}");
```

### <a name="expression-bodied-members"></a>Membri con corpo di espressione

Con la più recente sintassi C# disponibile nel runtime .NET 4.x, si possono usare [espressioni lambda](/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) per sostituire il corpo delle funzioni per renderle più concise:

```csharp
// .NET 3.5
private int TakeDamage(int amount)
{
    return Health -= amount;
}

// .NET 4.x
private int TakeDamage(int amount) => Health -= amount;
```

È anche possibile usare membri con corpo di espressione nelle proprietà di sola lettura:

```csharp
// .NET 4.x
public string PlayerHealthUiText => $"Player health: {Health}";
```

### <a name="task-based-asynchronous-pattern-tap"></a>Modello asincrono basato su attività (TAP)

La [programmazione asincrona](/dotnet/csharp/async) consente di eseguire operazioni che richiedono tempo senza che l'applicazione smetta di rispondere. Questa funzionalità consente anche al codice di attendere il completamento di operazioni di lunga durata prima di continuare con il codice che dipende dai risultati di queste operazioni. Si può ad esempio aspettare che un file venga caricato o il completamento di un'operazione di rete.

In Unity, la programmazione asincrona si ottiene in genere con [coroutine](https://docs.unity3d.com/Manual/Coroutines.html). Tuttavia, da C# 5, il metodo preferito per la programmazione asincrona per lo sviluppo .NET è diventato il [modello asincrono basato su attività TAP (Task-based Asynchronous Pattern)](/dotnet/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap) usando le parole chiave `async` e `await` con [ System.Threading.Task](/dotnet/api/system.threading.tasks.task). In breve, in una funzione `async` è possibile usare `await` per attendere il completamento di un'attività senza bloccare l'aggiornamento del resto dell'applicazione:

```csharp
// Unity coroutine
using UnityEngine;
public class UnityCoroutineExample : MonoBehaviour
{
    private void Start()
    {
        StartCoroutine(WaitOneSecond());
        DoMoreStuff(); // This executes without waiting for WaitOneSecond
    }
    private IEnumerator WaitOneSecond()
    {
        yield return new WaitForSeconds(1.0f);
        Debug.Log("Finished waiting.");
    }
}
```

```csharp
// .NET 4.x async-await
using UnityEngine;
using System.Threading.Tasks;
public class AsyncAwaitExample : MonoBehaviour
{
    private async void Start()
    {
        Debug.Log("Wait.");
        await WaitOneSecondAsync();
        DoMoreStuff(); // Will not execute until WaitOneSecond has completed
    }
    private async Task WaitOneSecondAsync()
    {
        await Task.Delay(TimeSpan.FromSeconds(1));
        Debug.Log("Finished waiting.");
    }
}
```

TAP è un argomento complesso, con varie sfumature specifiche per Unity di cui devono tenere conto gli sviluppatori. Di conseguenza, TAP non è un sostituto universale per le coroutine in Unity, bensì un altro strumento a disposizione. L'ambito di questa funzionalità esula dagli scopi di questo articolo, ma di seguito vengono forniti alcuni suggerimenti e procedure consigliate generali.

#### <a name="getting-started-reference-for-tap-with-unity"></a>Informazioni di riferimento introduttive per TAP con Unity

Questi suggerimenti possono essere utili per iniziare a usare il modello TAP in Unity:

* Le funzioni asincrone destinate a essere attese devono avere il tipo restituito [`Task`](/dotnet/api/system.threading.tasks.task) o [`Task<TResult>`](/dotnet/api/system.threading.tasks.task-1) .
* Le funzioni asincrone che restituiscono un'attività devono avere il suffisso **"Async"** aggiunto ai relativi nomi. Il suffisso "Async" consente di indicare che una funzione deve sempre essere attesa.
* Usare solo il tipo restituito `async void` per le funzioni che attivano funzioni asincrone dal codice sincrono tradizionale. Tali funzioni non possono essere attese e non devono avere il suffisso "Async" nei relativi nomi.
* Unity usa UnitySynchronizationContext per assicurarsi che le funzioni asincrone vengano eseguite sul thread principale per impostazione predefinita. L'API di Unity non è accessibile all'esterno del thread principale.
* È possibile eseguire attività su thread in background con metodi quali [`Task.Run`](/dotnet/api/system.threading.tasks.task.run) e [`Task.ConfigureAwait(false)`](/dotnet/api/system.threading.tasks.task.configureawait) . Questa tecnica è utile per l'offload delle operazioni onerose dal thread principale per migliorare le prestazioni. Tuttavia, l'uso di thread in background può causare problemi di cui è difficile eseguire il debug, ad esempio [situazioni di race condition](https://wikipedia.org/wiki/Race_condition).
* L'API di Unity non è accessibile all'esterno del thread principale.
* Le attività che usano i thread non sono supportate in build WebGL Unity.

#### <a name="differences-between-coroutines-and-tap"></a>Differenze tra coroutine e TAP

Esistono alcune importanti differenze tra le coroutine e TAP/async-await:

* Le coroutine non possono restituire valori, diversamente da `Task<TResult>`.
* Non è possibile inserire `yield` in un'istruzione try-catch e ciò rende difficile la gestione degli errori con le coroutine. Try-catch, tuttavia, funziona con TAP.
* La funzionalità delle coroutine di Unity non è disponibile nelle classi non derivate da MonoBehaviour. TAP è un'ottima soluzione per la programmazione asincrona in tali classi.
* Attualmente, Unity non consiglia TAP come sostituzione generale per le coroutine. La profilatura è l'unico modo per conoscere i risultati specifici di un approccio rispetto all'altro per ogni progetto.

> [!NOTE]
> A partire da Unity 2018.2, i metodi asincroni di debug con punti di interruzione non sono del tutto supportati. Tuttavia, [questa funzionalità è prevista in Unity 2018.3](https://twitter.com/jbevain/status/900043560665235456).

### <a name="nameof-operator"></a>Operatore nameof

L'operatore `nameof` ottiene il nome di stringa di una variabile, un tipo o un membro. Alcuni casi in cui `nameof` risulta utile sono la registrazione degli errori e il recupero del nome della stringa di un enum:

```csharp
// Get the string name of an enum:
enum Difficulty {Easy, Medium, Hard};
private void Start()
{
    Debug.Log(nameof(Difficulty.Easy));
    RecordHighScore("John");
    // Output:
    // Easy
    // playerName
}
// Validate parameter:
private void RecordHighScore(string playerName)
{
    Debug.Log(nameof(playerName));
    if (playerName == null) throw new ArgumentNullException(nameof(playerName));
}
```

### <a name="caller-info-attributes"></a>Attributi informativi sul chiamante

Gli [attributi informativi sul chiamante](/dotnet/csharp/programming-guide/concepts/caller-information) forniscono informazioni relative al chiamante di un metodo. È necessario specificare un valore predefinito per ogni parametro da usare con un attributo informativo sul chiamante:

```csharp
private void Start ()
{
    ShowCallerInfo("Something happened.");
}
public void ShowCallerInfo(string message,
        [System.Runtime.CompilerServices.CallerMemberName] string memberName = "",
        [System.Runtime.CompilerServices.CallerFilePath] string sourceFilePath = "",
        [System.Runtime.CompilerServices.CallerLineNumber] int sourceLineNumber = 0)
{
    Debug.Log($"message: {message}");
    Debug.Log($"member name: {memberName}");
    Debug.Log($"source file path: {sourceFilePath}");
    Debug.Log($"source line number: {sourceLineNumber}");
}
// Output:
// Something happened
// member name: Start
// source file path: D:\Documents\unity-scripting-upgrade\Unity Project\Assets\CallerInfoTest.cs
// source line number: 10
```

### <a name="using-static"></a>Direttiva using static

La direttiva [using static](/dotnet/csharp/language-reference/keywords/using-static) consente di usare funzioni statiche senza digitare il nome della classe. Con using static è possibile risparmiare spazio e tempo se è necessario usare diverse funzioni statiche dalla stessa classe:

```csharp
// .NET 3.5
using UnityEngine;
public class Example : MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(Mathf.RoundToInt(Mathf.PI));
        // Output:
        // 3
    }
}
```

```csharp
// .NET 4.x
using UnityEngine;
using static UnityEngine.Mathf;
public class UsingStaticExample: MonoBehaviour
{
    private void Start ()
    {
        Debug.Log(RoundToInt(PI));
        // Output:
        // 3
    }
}
```

## <a name="il2cpp-considerations"></a>Considerazioni su IL2CPP

Quando si esporta un gioco in piattaforme come iOS, Unity userà il motore IL2CPP per "eseguire il transpile" di IL in codice C++ che viene quindi compilato usando il compilatore nativo della piattaforma di destinazione. In questo scenario, esistono numerose funzionalità di .NET che non sono supportate, ad esempio parti della reflection e l'utilizzo della parola chiave `dynamic`. Mentre è possibile controllare l'utilizzo di queste funzionalità nel codice, è possibile riscontrare problemi durante l'uso di DLL e SDK di terze parti non scritti tenendo conto di Unity e IL2CPP. Per altre informazioni su questo argomento, vedere la documentazione relativa alle [restrizioni di scripting](https://docs.unity3d.com/Manual/ScriptingRestrictions.html) nel sito di Unity.

Inoltre, come accennato nell'esempio Json.NET precedente, Unity proverà a rimuovere il codice inutilizzato durante il processo di esportazione IL2CPP.  Sebbene questo non sia in genere un problema, con le librerie che usano la reflection, può rimuovere accidentalmente le proprietà o i metodi che verranno chiamati in fase di esecuzione che non possono essere determinati in fase di esportazione.  Per risolvere questi problemi, aggiungere un file **link.xml** al progetto, che contiene un elenco di assembly e spazi dei nomi su cui non eseguire il processo di rimozione.  Per informazioni dettagliate, vedere la [documentazione di Unity sulla rimozione del bytecode](https://docs.unity3d.com/Manual/IL2CPP-BytecodeStripping.html).

## <a name="net-4x-sample-unity-project"></a>Progetto Unity di esempio di .NET 4.x

L'esempio contiene esempi di diverse funzionalità di .NET 4.x. È possibile scaricare il progetto o visualizzare il codice sorgente in [GitHub](https://github.com/Microsoft/unity-scripting-upgrade).

## <a name="additional-resources"></a>Risorse aggiuntive

* [Blog di Unity - Miglioramenti del runtime di scripting in Unity 2018.2](https://blogs.unity3d.com/2018/07/11/scripting-runtime-improvements-in-unity-2018-2/)
* [Storia di C#](/dotnet/csharp/whats-new/csharp-version-history)
* [Novità di C# 6](/dotnet/csharp/whats-new/csharp-6)
* [Programmazione asincrona in Unity con coroutine e TAP](/archive/blogs/appconsult/unity-coroutine-tap-en-us)
* [Async-Await invece di coroutine in Unity 2017](http://www.stevevermeulen.com/index.php/2017/09/using-async-await-in-unity3d-2017/)
* [Forum su Unity - Anteprime di scripting sperimentali](https://forum.unity.com/forums/experimental-scripting-previews.107/)