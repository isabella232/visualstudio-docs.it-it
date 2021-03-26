---
title: Analizzatori Roslyn e librerie in grado di riconoscere il codice per ImmutableArrays
description: Informazioni su come creare un analizzatore Roslyn reale per rilevare errori comuni quando si usa il pacchetto NuGet System. Collections. Immutable.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e3bdcc9c35f5acaf9937bd18b0160f9e5a58161c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105060586"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analizzatori Roslyn e libreria compatibile con il codice per ImmutableArrays

Il [.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") consente di creare librerie compatibili con il codice. Una libreria con supporto del codice offre funzionalità che è possibile usare e strumenti (analizzatori Roslyn) per aiutare a usare la libreria nel modo migliore o per evitare errori. Questo argomento illustra come creare un analizzatore Roslyn reale per rilevare errori comuni quando si usa il pacchetto NuGet [System. Collections. Immutable](https://www.nuget.org/packages/System.Collections.Immutable) . Nell'esempio viene inoltre illustrato come fornire una correzione del codice per un problema di codice rilevato dall'analizzatore. Gli utenti visualizzano le correzioni del codice nell'interfaccia utente di Visual Studio Light Bulb e possono applicare automaticamente una correzione per il codice.

## <a name="get-started"></a>Introduzione

Per compilare questo esempio, è necessario quanto segue:

* Visual Studio 2015 (non è un'edizione Express) o versione successiva. Puoi usare la versione gratuita di [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Quando si installa Visual Studio, è inoltre possibile controllare **Visual Studio Extensibility Tools** in **strumenti comuni** per installare contemporaneamente l'SDK. Se Visual Studio è già stato installato, è anche possibile installare questo SDK passando al menu principale **file**  >  **nuovo**  >  **progetto**, scegliendo **C#** nel riquadro di spostamento a sinistra e quindi scegliendo **estendibilità**. Quando si sceglie il modello di progetto di navigazione "**installa il Visual Studio Extensibility Tools**", viene richiesto di scaricare e installare l'SDK.
* [.NET Compiler Platform ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). È anche possibile installare questo SDK passando al menu principale **file**  >  **nuovo**  >  **progetto**, scegliendo **C#** nel riquadro di spostamento a sinistra e scegliendo **estendibilità**. Quando si sceglie il modello di progetto di navigazione "**Scarica il .NET Compiler Platform SDK**", viene richiesto di scaricare e installare l'SDK. Questo SDK include il [Syntax Visualizer Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Syntax-Visualizer.md). Questo utile strumento consente di individuare i tipi di modelli di codice da cercare nell'analizzatore. L'infrastruttura dell'analizzatore chiama il codice per tipi di modelli di codice specifici, quindi il codice viene eseguito solo quando necessario e può concentrarsi solo sull'analisi del codice pertinente.

## <a name="whats-the-problem"></a>Qual è il problema?

Si supponga di fornire una libreria con supporto per ImmutableArray (ad esempio <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName> ). Gli sviluppatori C# hanno molta esperienza con gli array .NET. Tuttavia, a causa della natura delle tecniche di ImmutableArrays e di ottimizzazione usate nell'implementazione, le intuizioni per sviluppatori C# comportano la scrittura di codice rotto da parte degli utenti della libreria, come illustrato di seguito. Inoltre, gli utenti non visualizzano gli errori fino alla fase di esecuzione, che non è l'esperienza di qualità usata in Visual Studio con .NET.

Gli utenti hanno familiarità con la scrittura di codice simile al seguente:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

La creazione di matrici vuote per compilare le righe di codice successive e l'utilizzo della sintassi dell'inizializzatore di raccolta è familiare agli sviluppatori C#. Tuttavia, scrivendo lo stesso codice per un arresto anomalo del ImmutableArray in fase di esecuzione:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

Il primo errore è dovuto all'implementazione di ImmutableArray che usa uno struct per eseguire il wrapping dell'archivio dati sottostante. Gli struct devono avere costruttori senza parametri, in modo che `default(T)` le espressioni possano restituire struct con tutti i membri zero o null. Quando il codice accede `b1.Length` a, si verifica un errore di dereferenziazione null in fase di esecuzione perché non è presente alcun array di archiviazione sottostante nello struct ImmutableArray. Il modo corretto per creare un ImmutableArray vuoto è `ImmutableArray<int>.Empty` .

L'errore con gli inizializzatori di raccolta si verifica perché il `ImmutableArray.Add` metodo restituisce nuove istanze ogni volta che viene chiamato. Poiché ImmutableArrays non cambia mai, quando si aggiunge un nuovo elemento, viene restituito un nuovo oggetto ImmutableArray, che può condividere l'archiviazione per motivi di prestazioni con un ImmutableArray esistente. Poiché `b2` punta al primo ImmutableArray prima di chiamare `Add()` cinque volte, `b2` è un ImmutableArray predefinito. Anche la chiamata a length si arresta in modo anomalo con un errore di dereferenziazione null. Il modo corretto per inizializzare un ImmutableArray senza chiamare manualmente Add consiste nell'usare `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})` .

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Trovare i tipi di nodo della sintassi pertinente per attivare l'analizzatore

 Per iniziare a compilare l'analizzatore, è necessario innanzitutto individuare il tipo di SyntaxNode che si vuole cercare. Avviare il **Syntax Visualizer** dal menu **Visualizza**  >  **altri**  >  **Syntax Visualizer Windows Roslyn**.

Posizionare il punto di inserimento dell'editor sulla riga che dichiara `b1` . Si noterà che il Syntax Visualizer Mostra che ci si trova in un `LocalDeclarationStatement` nodo dell'albero della sintassi. Questo nodo dispone di un `VariableDeclaration` , che a sua volta dispone di un, `VariableDeclarator` che a sua volta dispone di un `EqualsValueClause` e infine di un oggetto `ObjectCreationExpression` . Quando si fa clic nell'albero Syntax Visualizer dei nodi, nella finestra dell'editor viene evidenziata la sintassi per visualizzare il codice rappresentato da tale nodo. I nomi dei sottotipi SyntaxNode corrispondono ai nomi usati nella grammatica C#.

## <a name="create-the-analyzer-project"></a>Creare il progetto dell'analizzatore

Dal menu principale scegliere **file**  >  **nuovo**  >  **progetto**. Nella finestra di dialogo **nuovo progetto** , in progetti **C#** nella barra di spostamento a sinistra, scegliere **estendibilità** e nel riquadro destro scegliere il modello **di progetto analizzatore con correzione codice** . Immettere un nome e confermare la finestra di dialogo.

Il modello apre un file *DiagnosticAnalyzer. cs* . Scegliere la scheda buffer dell'editor. Questo file contiene una classe analizzatore (formato dal nome assegnato al progetto) che deriva da `DiagnosticAnalyzer` (un tipo di API Roslyn). La nuova classe dispone di un oggetto `DiagnosticAnalyzerAttribute` che dichiara che l'analizzatore è pertinente per il linguaggio C#, in modo che il compilatore individua e carica l'analizzatore.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

È possibile implementare un analizzatore usando Visual Basic destinato al codice C# e viceversa. È più importante in DiagnosticAnalyzerAttribute scegliere se l'analizzatore è destinato a una lingua o a entrambi. Gli analizzatori più sofisticati che richiedono una modellazione dettagliata del linguaggio possono avere come destinazione solo una singola lingua. Se l'analizzatore, ad esempio, controlla solo i nomi dei tipi o i nomi dei membri pubblici, può essere possibile usare il modello di linguaggio comune Roslyn tra Visual Basic e C#. Ad esempio, FxCop avverte che una classe implementa <xref:System.Runtime.Serialization.ISerializable> , ma la classe non ha l' <xref:System.SerializableAttribute> attributo indipendente dalla lingua e funziona sia per il codice Visual Basic che per il codice C#.

## <a name="initialize-the-analyzer"></a>Inizializzare l'analizzatore

 Scorrere leggermente verso il basso nella `DiagnosticAnalyzer` classe per visualizzare il `Initialize` metodo. Il compilatore chiama questo metodo quando si attiva un analizzatore. Il metodo accetta un `AnalysisContext` oggetto che consente all'analizzatore di ottenere le informazioni di contesto e di registrare i callback per gli eventi per i tipi di codice che si vuole analizzare.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Aprire una nuova riga in questo metodo e digitare "context". per visualizzare un elenco di completamento IntelliSense. Nell'elenco di completamento sono disponibili molti `Register...` metodi che consentono di gestire vari tipi di eventi. Il primo,, ad esempio, `RegisterCodeBlockAction` richiama il codice per un blocco, che in genere è codice tra parentesi graffe. La registrazione per un blocco richiama anche il codice per l'inizializzatore di un campo, il valore assegnato a un attributo o il valore di un parametro facoltativo.

Come altro esempio, `RegisterCompilationStartAction` , richiama il codice all'inizio di una compilazione, operazione utile quando è necessario raccogliere lo stato in molte posizioni. È possibile creare una struttura di dati, ad Say, per raccogliere tutti i simboli usati e ogni volta che l'analizzatore viene richiamato per una sintassi o un simbolo, è possibile salvare le informazioni su ogni posizione nella struttura dei dati. Quando viene richiamato a causa della fine della compilazione, è possibile analizzare tutte le posizioni salvate, ad esempio per segnalare i simboli usati dal codice da ogni `using` istruzione.

Utilizzando il **Syntax Visualizer** si è appreso che si desidera chiamare quando il compilatore elabora un ObjectCreationExpression. Usare questo codice per impostare il callback:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

È possibile registrarsi per un nodo della sintassi e filtrare solo per i nodi della sintassi per la creazione di oggetti. Per convenzione, gli autori dell'analizzatore usano un'espressione lambda per la registrazione delle azioni, che consente di evitare che gli analizzatori siano senza stato. È possibile usare la funzionalità di Visual Studio **genera da utilizzo** per creare il `AnalyzeObjectCreation` metodo. Viene generato anche il tipo corretto di parametro di contesto.

## <a name="set-properties-for-users-of-your-analyzer"></a>Impostare le proprietà per gli utenti dell'analizzatore

In modo che l'analizzatore venga visualizzato nell'interfaccia utente di Visual Studio in modo appropriato, cercare e modificare la seguente riga di codice per identificare l'analizzatore:

```csharp
internal const string Category = "Naming";
```

Cambiare `"Naming"` in `"API Guidance"`.

Successivamente, trovare e aprire il file *Resources. resx* nel progetto usando il **Esplora soluzioni**. È possibile inserire una descrizione per l'analizzatore, il titolo e così via. È possibile modificare il valore di tutti questi valori in `"Don't use ImmutableArray<T> constructor"` per il momento. È possibile inserire gli argomenti di formattazione della stringa nella stringa ( {0} , e {1} così via) e successivamente quando si chiama `Diagnostic.Create()` , è possibile fornire una `params` matrice di argomenti da passare.

## <a name="analyze-an-object-creation-expression"></a>Analizzare un'espressione di creazione di un oggetto

Il `AnalyzeObjectCreation` metodo accetta un tipo diverso di contesto fornito dal framework dell'analizzatore di codice. Il `Initialize` metodo `AnalysisContext` consente di registrare i callback di azione per configurare l'analizzatore. `SyntaxNodeAnalysisContext`, Ad esempio, dispone di un oggetto `CancellationToken` che è possibile passare. Se un utente inizia a digitare nell'editor, Roslyn Annulla l'esecuzione degli analizzatori per salvare il lavoro e migliorare le prestazioni. Come altro esempio, questo contesto ha una proprietà del nodo che restituisce il nodo della sintassi per la creazione di oggetti.

Ottenere il nodo che si può presumere è il tipo per il quale è stata filtrata l'azione del nodo della sintassi:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Avvia Visual Studio con l'analizzatore per la prima volta

Avviare Visual Studio compilando ed eseguendo l'analizzatore (premere **F5**). Poiché il progetto di avvio nella **Esplora soluzioni** è il progetto VSIX, l'esecuzione del codice compila il codice e un progetto VSIX, quindi avvia Visual Studio con il progetto VSIX installato. Quando si avvia Visual Studio in questo modo, viene avviato con un hive del registro di sistema distinto, in modo che l'uso principale di Visual Studio non sarà influenzato dalle istanze di test durante la compilazione degli analizzatori. Al primo avvio di questo modo, Visual Studio esegue diverse inizializzazioni simili a quando si avvia Visual Studio per la prima volta dopo l'installazione.

Creare un progetto console e quindi immettere il codice dell'array nel metodo Main delle applicazioni console:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Le righe di codice con `ImmutableArray` hanno controllo ortografia durante perché è necessario ottenere il pacchetto NuGet non modificabile e aggiungere un' `using` istruzione al codice. Premere il pulsante destro del mouse sul nodo del progetto nella **Esplora soluzioni** e scegliere **Gestisci pacchetti NuGet**. In gestione NuGet digitare "immutable" nella casella di ricerca e scegliere l'elemento **System. Collections. Immutable** (non scegliere **Microsoft. BCL. Immutable**) nel riquadro sinistro e premere il pulsante **Installa** nel riquadro destro. Con l'installazione del pacchetto viene aggiunto un riferimento ai riferimenti del progetto.

Viene ancora visualizzato il controllo ortografia durante rosso `ImmutableArray` , quindi posizionare il punto di inserimento nell'identificatore e premere **CTRL** + **.** (periodo) per visualizzare il menu correzione suggerito e scegliere di aggiungere l'istruzione appropriata `using` .

**Salvare e chiudere** la seconda istanza di Visual Studio per ora per poter continuare.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Terminare l'analizzatore con modifica e continuazione

Nella prima istanza di Visual Studio impostare un punto di interruzione all'inizio del `AnalyzeObjectCreation` Metodo premendo **F9** con il cursore nella prima riga.

Avviare di nuovo l'analizzatore con **F5** e nella seconda istanza di Visual Studio riaprire l'applicazione console creata per l'ultima volta.

Si ritorna alla prima istanza di Visual Studio in corrispondenza del punto di interruzione perché il compilatore Roslyn ha visto un'espressione di creazione di un oggetto e ha chiamato nell'analizzatore.

**Ottenere il nodo di creazione dell'oggetto.** Eseguire un'istruzione/routine della riga che imposta la `objectCreation` variabile premendo **F10** e nella **finestra di controllo immediato** valutare l'espressione `"objectCreation.ToString()"` . Si noterà che il nodo della sintassi a cui punta la variabile è il codice `"new ImmutableArray<int>()"` , solo quello che si sta cercando.

**Ottiene l'oggetto di tipo ImmutableArray<T \> .** È necessario verificare se il tipo da creare è ImmutableArray. In primo luogo, si ottiene l'oggetto che rappresenta questo tipo. È possibile controllare i tipi usando il modello semantico per assicurarsi di avere esattamente il tipo corretto e non confrontare la stringa da `ToString()` . Immettere la riga di codice seguente alla fine della funzione:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

È possibile designare i tipi generici nei metadati con apice inverso (') e il numero di parametri generici. Questo è il motivo per cui non viene visualizzato "... ImmutableArray \<T> "nel nome dei metadati.

Il modello semantico contiene molti elementi utili che consentono di porre domande su simboli, flusso di dati, durata variabile e così via. Roslyn separa i nodi della sintassi dal modello semantico per diversi motivi di progettazione (prestazioni, modellazione di codice errato e così via). Si desidera che il modello di compilazione cerchi le informazioni contenute nei riferimenti per un confronto accurato.

È possibile trascinare il puntatore di esecuzione giallo sul lato sinistro della finestra dell'editor. Trascinarlo fino alla riga che imposta la `objectCreation` variabile ed eseguire un'istruzione alla nuova riga di codice con **F10**. Se si passa il puntatore del mouse sulla variabile `immutableArrayOfType` , si noterà che è stato trovato il tipo esatto nel modello semantico.

**Ottiene il tipo dell'espressione di creazione dell'oggetto.** "Type" viene usato in alcuni modi in questo articolo, ma ciò significa che se si ha un'espressione "New foo", è necessario ottenere un modello di foo. È necessario ottenere il tipo dell'espressione di creazione dell'oggetto per verificare se si tratta del \<T> tipo ImmutableArray. Utilizzare di nuovo il modello semantico per ottenere informazioni sui simboli per il simbolo di tipo (ImmutableArray) nell'espressione di creazione dell'oggetto. Immettere la riga di codice seguente alla fine della funzione:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Poiché l'analizzatore deve gestire codice incompleto o non corretto nei buffer dell'editor (ad esempio, è presente un' `using` istruzione mancante), è necessario verificare la `symbolInfo` presenza di `null` . Per completare l'analisi, è necessario ottenere un tipo denominato (INamedTypeSymbol) dall'oggetto informazioni sui simboli.

**Confrontare i tipi.** Poiché è presente un tipo generico aperto di T che si sta cercando e il tipo nel codice è un tipo generico concreto, è possibile eseguire una query sulle informazioni sui simboli per la costruzione del tipo (un tipo generico aperto) e confrontare il risultato con `immutableArrayOfTType` . Immettere quanto segue alla fine del metodo:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Segnala la diagnostica.** Il reporting della diagnostica è piuttosto semplice. Usare la regola creata nel modello di progetto, che viene definita prima del metodo Initialize. Poiché questa situazione nel codice è un errore, è possibile modificare la riga che ha inizializzato la regola in sostituzione `DiagnosticSeverity.Warning` (zigzag verde) con `DiagnosticSeverity.Error` (zigzag rosso). Il resto della regola viene inizializzato dalle risorse modificate in prossimità dell'inizio della procedura dettagliata. È anche necessario segnalare il percorso per zigzag, ovvero il percorso della specifica del tipo dell'espressione di creazione dell'oggetto. Immettere il codice seguente nel `if` blocco:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

La funzione dovrebbe essere simile alla seguente (probabilmente formattata in modo diverso):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}
```

Rimuovere il punto di interruzione in modo che sia possibile visualizzare l'analizzatore funzionante (e arrestare il ritorno alla prima istanza di Visual Studio). Trascinare il puntatore di esecuzione all'inizio del metodo e premere **F5** per continuare l'esecuzione. Quando si torna alla seconda istanza di Visual Studio, il compilatore inizierà a esaminare nuovamente il codice e chiamerà nell'analizzatore. È possibile visualizzare un zigzag in `ImmutableType<int>` .

## <a name="adding-a-code-fix-for-the-code-issue"></a>Aggiunta di una "correzione del codice" per il problema del codice

Prima di iniziare, chiudere la seconda istanza di Visual Studio e arrestare il debug nella prima istanza di Visual Studio (in cui si sta sviluppando l'analizzatore).

**Aggiungere una nuova classe.** Utilizzare il menu di scelta rapida (pulsante destro del puntatore) sul nodo del progetto nella **Esplora soluzioni** e scegliere di aggiungere un nuovo elemento. Aggiungere una classe denominata `BuildCodeFixProvider` . Questa classe deve derivare da `CodeFixProvider` e sarà necessario usare **CTRL** + **.** (periodo) per richiamare la correzione del codice che aggiunge l' `using` istruzione corretta. Questa classe deve anche essere annotata con `ExportCodeFixProvider` l'attributo e sarà necessario aggiungere un' `using` istruzione per risolvere l' `LanguageNames` enumerazione. È necessario disporre di un file di classe con il codice seguente:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Stub di membri derivati.** A questo punto, posizionare il punto di inserimento dell'editor nell'identificatore `CodeFixProvider` e premere **CTRL** + **.** (periodo) per eseguire lo stub dell'implementazione per questa classe di base astratta. Questo genera una proprietà e un metodo per l'utente.

**Implementare la proprietà.** Compilare il `FixableDiagnosticIds` corpo della proprietà `get` con il codice seguente:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn riunisce diagnostica e correzioni abbinando questi identificatori, che sono solo stringhe. Il modello di progetto ha generato automaticamente un ID di diagnostica ed è possibile modificarlo. Il codice nella proprietà restituisce solo l'ID della classe analizzatore.

**Il metodo RegisterCodeFixAsync accetta un contesto.** Il contesto è importante perché una correzione del codice può essere applicata a più diagnostica oppure può esserci più di un problema in una riga di codice. Se si digita "context". nel corpo del metodo, l'elenco di completamento IntelliSense visualizzerà alcuni membri utili. È presente un membro CancellationToken che è possibile controllare per verificare se un elemento vuole annullare la correzione. È presente un membro del documento con molti membri utili e consente di ottenere gli oggetti del progetto e del modello di soluzione. È presente un membro span che rappresenta l'inizio e la fine della posizione del codice specificata quando è stata segnalata la diagnostica.

**Rendere il metodo asincrono.** La prima cosa da fare è correggere la dichiarazione di metodo generata in modo che sia un `async` metodo. La correzione del codice per lo stub dell'implementazione di una classe astratta non include la `async` parola chiave anche se il metodo restituisce `Task` .

**Ottiene la radice della struttura ad albero della sintassi.** Per modificare il codice è necessario produrre un nuovo albero della sintassi con le modifiche apportate dalla correzione del codice. È necessario che `Document` dal contesto da chiamare `GetSyntaxRootAsync` . Si tratta di un metodo asincrono perché è presente un lavoro sconosciuto per ottenere l'albero della sintassi, eventualmente anche per ottenere il file dal disco, analizzarlo e compilare il modello di codice Roslyn. L'interfaccia utente di Visual Studio deve rispondere durante questo periodo di tempo, che usa `async` Abilita. Sostituire la riga di codice nel metodo con il codice seguente:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Individuare il nodo con il problema.** Si passa l'intervallo del contesto, ma il nodo trovato potrebbe non essere il codice che è necessario modificare. La diagnostica restituita ha fornito solo l'intervallo per l'identificatore del tipo (in cui appartiene zigzag), ma è necessario sostituire l'intera espressione di creazione dell'oggetto, inclusa la `new` parola chiave all'inizio e le parentesi alla fine. Aggiungere il codice seguente al metodo e usare **CTRL** + **.** per aggiungere un' `using` istruzione per `ObjectCreationExpressionSyntax` ):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Registrare la correzione del codice per l'interfaccia utente lampadina.** Quando si registra la correzione del codice, Roslyn inserisce automaticamente l'interfaccia utente di Visual Studio Light Bulb. Gli utenti finali vedranno che possono usare **CTRL** + **.** (periodo) quando l'analizzatore controllo ortografia durante l'uso di un costruttore non valido `ImmutableArray<T>` . Poiché il provider di correzione del codice viene eseguito solo quando si verifica un problema, è possibile presupporre di avere l'espressione di creazione dell'oggetto che si sta cercando. Dal parametro context è possibile registrare la nuova correzione del codice aggiungendo il codice seguente alla fine del `RegisterCodeFixAsync` Metodo:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

È necessario inserire il punto di inserimento dell'editor nell'identificatore, `CodeAction` quindi premere **CTRL** + **.** (periodo) per aggiungere l' `using` istruzione appropriata per questo tipo.

Posizionare quindi il punto di inserimento dell'editor nell' `ChangeToImmutableArrayEmpty` identificatore e usare **CTRL** + **.** ancora una volta per generare questo stub di metodo.

L'ultimo frammento di codice aggiunto registra la correzione del codice passando un oggetto `CodeAction` e l'ID di diagnostica per il tipo di problema rilevato. In questo esempio è presente un solo ID di diagnostica per cui questo codice fornisce correzioni, quindi è possibile passare semplicemente il primo elemento della matrice di ID di diagnostica. Quando si crea `CodeAction` , si passa il testo che l'interfaccia utente lampadina deve usare come descrizione della correzione del codice. Si passa anche una funzione che accetta un oggetto CancellationToken e restituisce un nuovo documento. Il nuovo documento dispone di un nuovo albero della sintassi che include il codice con patch che chiama `ImmutableArray.Empty` . Questo frammento di codice usa un'espressione lambda in modo che possa essere chiusa sul nodo objectCreation e sul documento del contesto.

**Costruire la nuova struttura ad albero della sintassi.** Nel `ChangeToImmutableArrayEmpty` metodo il cui Stub è stato generato in precedenza, immettere la riga di codice: `ImmutableArray<int>.Empty;` . Se si visualizza nuovamente la finestra degli strumenti di **Syntax Visualizer** , è possibile osservare che questa sintassi è un nodo SimpleMemberAccessExpression. Questo è ciò che questo metodo deve costruire e restituire in un nuovo documento.

La prima modifica a `ChangeToImmutableArrayEmpty` consiste nell'aggiungere `async` prima `Task<Document>` perché i generatori di codice non possono presupporre che il metodo sia asincrono.

Inserire il codice seguente nel corpo, in modo che il metodo sia simile al seguente:

```csharp
private async Task<Document> ChangeToImmutableArrayEmpty(
    ObjectCreationExpressionSyntax objectCreation, Document document,
    CancellationToken c)
{
    var generator = SyntaxGenerator.GetGenerator(document);
    var memberAccess =
        generator.MemberAccessExpression(objectCreation.Type, "Empty");
    var oldRoot = await document.GetSyntaxRootAsync(c);
    var newRoot = oldRoot.ReplaceNode(objectCreation, memberAccess);
    return document.WithSyntaxRoot(newRoot);
}
```

È necessario inserire il punto di inserimento dell'editor nell' `SyntaxGenerator` identificatore e usare **CTRL** + **.** (periodo) per aggiungere l' `using` istruzione appropriata per questo tipo.

Questo codice usa `SyntaxGenerator` , che è un tipo utile per la costruzione di un nuovo codice. Dopo aver ricevuto un generatore per il documento in cui si è verificato il problema di codice, `ChangeToImmutableArrayEmpty` chiama `MemberAccessExpression` , passando il tipo con il membro a cui si vuole accedere e passando il nome del membro sotto forma di stringa.

Il metodo recupera quindi la radice del documento e, poiché può implicare un lavoro arbitrario nel caso generale, il codice attende questa chiamata e passa il token di annullamento. I modelli di codice Roslyn non sono modificabili, ad esempio l'uso di una stringa .NET; Quando si aggiorna la stringa, si ottiene un nuovo oggetto stringa in return. Quando si chiama `ReplaceNode` , si ottiene un nuovo nodo radice. La maggior parte della struttura ad albero della sintassi è condivisa (poiché non è modificabile), ma il `objectCreation` nodo viene sostituito con il `memberAccess` nodo, così come tutti i nodi padre fino alla radice dell'albero della sintassi.

## <a name="try-your-code-fix"></a>Prova la correzione del codice

È ora possibile premere **F5** per eseguire l'analizzatore in una seconda istanza di Visual Studio. Aprire il progetto console usato in precedenza. A questo punto si noterà che la lampadina viene visualizzata in cui si trova la nuova espressione di creazione di un oggetto `ImmutableArray<int>` . Se si preme **CTRL** + **.** (periodo), verrà visualizzata la correzione del codice e verrà visualizzata un'anteprima della differenza del codice generata automaticamente nell'interfaccia utente lampadina. Roslyn lo crea automaticamente.

**Suggerimento Pro:** Se si avvia la seconda istanza di Visual Studio e non viene visualizzata la lampadina con la correzione del codice, potrebbe essere necessario cancellare la cache dei componenti di Visual Studio. La cancellazione della cache impone a Visual Studio di riesaminare i componenti, quindi Visual Studio dovrebbe quindi selezionare il componente più recente. Arrestare prima di tutto la seconda istanza di Visual Studio. Quindi, in **Esplora risorse** passare a *%LocalAppData%\Microsoft\VisualStudio\16.0Roslyn \\*. ("16,0" passa dalla versione alla versione con Visual Studio). Eliminare la sottodirectory *ComponentModelCache*.

## <a name="talk-video-and-finish-code-project"></a>Talk video e termina progetto di codice

Questo esempio è stato sviluppato e illustrato più avanti in [questo argomento](https://channel9.msdn.com/events/Build/2015/3-725). In questo articolo viene illustrato l'analizzatore funzionante e viene illustrato come crearlo.

[Qui](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)è possibile visualizzare tutto il codice terminato. Le sottocartelle *DoNotUseImmutableArrayCollectionInitializer* e *DoNotUseImmutableArrayCtor* includono ognuna un file c# per individuare i problemi e un file c# che implementa le correzioni del codice visualizzate nell'interfaccia utente di Visual Studio Light Bulb. Si noti che il codice finito ha un'astrazione leggermente maggiore per evitare di recuperare l' \<T> oggetto di tipo ImmutableArray più volte. USA azioni registrate annidate per salvare l'oggetto tipo in un contesto disponibile ogni volta che vengono eseguite le azioni secondarie (analizza la creazione di oggetti e analizza le inizializzazioni della raccolta).

## <a name="see-also"></a>Vedi anche

* [\\\Build 2015 Talk](https://channel9.msdn.com/events/Build/2015/3-725)
* [Codice completato su GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Alcuni esempi su GitHub, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Altri documenti nel sito di GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Regole FxCop implementate con gli analizzatori Roslyn in GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
