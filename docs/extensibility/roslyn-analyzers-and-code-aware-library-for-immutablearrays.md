---
title: Analizzatori Roslyn e librerie in grado di riconoscere il codice per ImmutableArrays
description: Informazioni su come compilare un analizzatore Roslyn reale per rilevare gli errori comuni quando si usa il pacchetto NuGet System.Collections.Immutable.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ad08b0635e4c81fef4b1747f1b5da1e859977f65
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158359"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analizzatori Roslyn e libreria in grado di riconoscere il codice per ImmutableArrays

Il [.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") consente di compilare librerie in grado di riconoscere il codice. Una libreria con supporto del codice offre funzionalità che è possibile usare e gli strumenti (analizzatori Roslyn) per usare la libreria nel modo migliore o per evitare errori. Questo argomento illustra come compilare un analizzatore Roslyn reale per rilevare gli errori comuni quando si usa il pacchetto NuGet [System.Collections.Immutable.](https://www.nuget.org/packages/System.Collections.Immutable) L'esempio illustra anche come fornire una correzione del codice per un problema di codice rilevato dall'analizzatore. Gli utenti visualizzano le correzioni del codice nell Visual Studio'interfaccia utente della lampadina e possono applicare automaticamente una correzione per il codice.

## <a name="get-started"></a>Introduzione

Per compilare questo esempio, sono necessari gli elementi seguenti:

* Visual Studio 2015 (non Express Edition) o versione successiva. È possibile usare [l'edizione Visual Studio Community gratuita](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md). È anche possibile, quando si installa Visual Studio, controllare Visual Studio **strumenti** di estendibilità in **Strumenti comuni** per installare l'SDK contemporaneamente. Se è già stato installato Visual Studio, è anche possibile installare questo SDK scegliendo File nuovo Project dal **menu** principale, scegliendo C# nel riquadro di spostamento a sinistra e quindi  >    >   **Extensibility**.  Quando si sceglie il modello di progetto breadcrumb " Install **the Visual Studio Extensibility Tools**", viene richiesto di scaricare e installare l'SDK.
* [.NET Compiler Platform SDK ("Roslyn").](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK) È anche possibile installare questo SDK scegliendo File nuovo dal **menu** principale Project , scegliendo C# nel riquadro di spostamento a sinistra e quindi  >    >   **Extensibility**.  Quando si sceglie "**Scarica il modello di progetto .NET Compiler Platform SDK**" breadcrumb, viene richiesto di scaricare e installare l'SDK. Questo SDK include [roslyn Syntax Visualizer](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Syntax-Visualizer.md). Questo utile strumento consente di descrizione dei tipi di modello di codice da cercare nell'analizzatore. L'infrastruttura dell'analizzatore chiama nel codice per tipi di modello di codice specifici, quindi il codice viene eseguito solo quando necessario e può concentrarsi solo sull'analisi del codice pertinente.

## <a name="whats-the-problem"></a>Qual è il problema?

Imagine una libreria con supporto ImmutableArray (ad esempio, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName> ). Gli sviluppatori C# hanno molta esperienza con le matrici .NET. Tuttavia, a causa della natura di ImmutableArrays e delle tecniche di ottimizzazione usate nell'implementazione, le intuizioni degli sviluppatori C# causano agli utenti della libreria di scrivere codice interrotto, come illustrato di seguito. Inoltre, gli utenti non visualizzano gli errori fino alla fase di esecuzione, che non è l'esperienza di qualità a cui vengono usati in Visual Studio con .NET.

Gli utenti hanno familiarità con la scrittura di codice simile al seguente:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

La creazione di matrici vuote da compilare con le righe di codice successive e l'uso della sintassi dell'inizializzatore di raccolta sono familiari agli sviluppatori C#. Tuttavia, la scrittura dello stesso codice per un oggetto ImmutableArray si arresta in modo anomalo in fase di esecuzione:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

Il primo errore è dovuto all'implementazione di ImmutableArray che usa uno struct per eseguire il wrapping dell'archiviazione dati sottostante. Gli struct devono avere costruttori senza parametri in modo che le espressioni possano restituire `default(T)` struct con tutti i membri zero o Null. Quando il codice accede a , si verifica un errore di dereferenziazione Null in fase di esecuzione perché non è presente alcuna matrice di archiviazione sottostante nello `b1.Length` struct ImmutableArray. Il modo corretto per creare un oggetto ImmutableArray vuoto è `ImmutableArray<int>.Empty` .

L'errore con gli inizializzatori di raccolta si verifica perché il `ImmutableArray.Add` metodo restituisce nuove istanze ogni volta che viene chiamato. Poiché ImmutableArrays non cambia mai, quando si aggiunge un nuovo elemento, si ottiene un nuovo oggetto ImmutableArray (che può condividere l'archiviazione per motivi di prestazioni con un oggetto ImmutableArray esistente in precedenza). Poiché `b2` punta al primo Oggetto ImmutableArray prima di chiamare cinque `Add()` volte, è un oggetto `b2` ImmutableArray predefinito. Anche la chiamata a Length si arresta in modo anomalo con un errore di dereferenziazione Null. Il modo corretto per inizializzare un oggetto ImmutableArray senza chiamare manualmente Add è usare `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})` .

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Trovare i tipi di nodo della sintassi pertinenti per attivare l'analizzatore

 Per iniziare a compilare l'analizzatore, è innanzitutto necessario compilare il tipo di SyntaxNode da cercare. Avviare il **Syntax Visualizer** dal menu **Visualizza** altro  >  **Windows**  >  **Roslyn Syntax Visualizer**.

Posizionare il punto di interruzione dell'editor sulla riga che dichiara `b1` . Verrà visualizzato il messaggio Syntax Visualizer si è in un `LocalDeclarationStatement` nodo dell'albero della sintassi. Questo nodo ha un oggetto , che a sua volta ha un , che a sua volta ha un oggetto `VariableDeclaration` e infine è presente un oggetto `VariableDeclarator` `EqualsValueClause` `ObjectCreationExpression` . Quando si fa clic nell'Syntax Visualizer di nodi, la sintassi nella finestra dell'editor viene evidenziata per mostrare il codice rappresentato da tale nodo. I nomi dei sottotipi SyntaxNode corrispondono ai nomi usati nella grammatica C#.

## <a name="create-the-analyzer-project"></a>Creare il progetto dell'analizzatore

Scegliere Nuovo file dal menu  >    >  **principale Project**. Nella finestra **di dialogo Nuovo Project** progetti **C#** nella barra di spostamento a sinistra scegliere **Estendibilità** e nel riquadro destro scegliere il modello di progetto **Analizzatore** con correzione codice. Immettere un nome e confermare la finestra di dialogo.

Il modello apre un file *DiagnosticAnalyzer.cs.* Scegliere la scheda buffer dell'editor. Questo file ha una classe analizzatore (formata dal nome fornito dal progetto) che deriva da `DiagnosticAnalyzer` (un tipo di API Roslyn). La nuova classe ha un analizzatore dichiarante pertinente per il linguaggio C# in modo che il compilatore individua `DiagnosticAnalyzerAttribute` e carica l'analizzatore.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

È possibile implementare un analizzatore usando Visual Basic che ha come destinazione il codice C# e viceversa. È più importante in DiagnosticAnalyzerAttribute scegliere se l'analizzatore ha come destinazione un linguaggio o entrambi. Gli analizzatori più sofisticati che richiedono una modellazione dettagliata del linguaggio possono avere come destinazione una sola lingua. Se l'analizzatore, ad esempio, controlla solo i nomi dei tipi o dei membri pubblici, potrebbe essere possibile usare il modello di linguaggio comune offerte da Roslyn in Visual Basic e C#. Ad esempio, FxCop avvisa che una classe implementa , ma la classe non ha l'attributo indipendente dal linguaggio e funziona sia per il codice <xref:System.Runtime.Serialization.ISerializable> Visual Basic che per il codice <xref:System.SerializableAttribute> C#.

## <a name="initialize-the-analyzer"></a>Inizializzare l'analizzatore

 Scorrere leggermente verso il basso nella `DiagnosticAnalyzer` classe per visualizzare il metodo `Initialize` . Il compilatore chiama questo metodo quando si attiva un analizzatore. Il metodo accetta un oggetto che consente all'analizzatore di ottenere informazioni sul contesto e di registrare callback per gli eventi per i tipi di codice `AnalysisContext` da analizzare.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Aprire una nuova riga in questo metodo e digitare "context". per visualizzare un elenco di completamento IntelliSense. Nell'elenco di completamento sono disponibili molti metodi `Register...` per gestire vari tipi di eventi. Ad esempio, il primo, , chiama di nuovo il codice per un blocco, che in genere è codice tra parentesi `RegisterCodeBlockAction` graffe. La registrazione per un blocco richiama anche il codice per l'inizializzatore di un campo, il valore assegnato a un attributo o il valore di un parametro facoltativo.

Come altro esempio, , chiama di nuovo il codice all'inizio di una compilazione, utile quando è necessario raccogliere lo stato `RegisterCompilationStartAction` in più posizioni. È possibile creare una struttura di dati, ad esempio, per raccogliere tutti i simboli usati e ogni volta che l'analizzatore viene richiamato per una sintassi o un simbolo, è possibile salvare le informazioni su ogni posizione nella struttura dei dati. Quando si viene richiamati a causa della fine della compilazione, è possibile analizzare tutti i percorsi salvati, ad esempio, per segnalare i simboli utilizzati dal codice da ogni `using` istruzione.

Usando il **Syntax Visualizer**, si è appreso che si vuole essere chiamati quando il compilatore elabora un oggetto ObjectCreationExpression. Usare questo codice per configurare il callback:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Si registra per un nodo sintassi e si filtrano solo i nodi della sintassi per la creazione di oggetti. Per convenzione, gli autori di analizzatori usano un'espressione lambda durante la registrazione delle azioni, che consente di mantenere gli analizzatori senza stato. È possibile usare la Visual Studio **genera dall'utilizzo** per creare il `AnalyzeObjectCreation` metodo . Verrà generato anche il tipo corretto di parametro di contesto.

## <a name="set-properties-for-users-of-your-analyzer"></a>Impostare le proprietà per gli utenti dell'analizzatore

In modo che l'analizzatore sia visualizzato Visual Studio'interfaccia utente in modo appropriato, cercare e modificare la riga di codice seguente per identificare l'analizzatore:

```csharp
internal const string Category = "Naming";
```

Cambiare `"Naming"` in `"API Guidance"`.

Trovare e aprire quindi il file *Resources.resx* nel progetto usando Esplora soluzioni **.** È possibile inserire una descrizione per l'analizzatore, il titolo e così via. È possibile modificare il valore di tutti questi valori in `"Don't use ImmutableArray<T> constructor"` per il momento. È possibile inserire argomenti di formattazione di stringa nella stringa ( , , e così via) e in un secondo momento quando si chiama , è possibile fornire una matrice di {0} {1} argomenti da `Diagnostic.Create()` `params` passare.

## <a name="analyze-an-object-creation-expression"></a>Analizzare un'espressione di creazione di oggetti

Il `AnalyzeObjectCreation` metodo accetta un tipo diverso di contesto fornito dal framework dell'analizzatore del codice. Il `Initialize` metodo consente di `AnalysisContext` registrare i callback di azione per configurare l'analizzatore. , `SyntaxNodeAnalysisContext` ad esempio, ha un `CancellationToken` oggetto che è possibile passare. Se un utente inizia a digitare nell'editor, Roslyn annulla l'esecuzione degli analizzatori per salvare il lavoro e migliorare le prestazioni. Come altro esempio, questo contesto ha una proprietà Node che restituisce il nodo della sintassi per la creazione di oggetti.

Ottenere il nodo, che è possibile presupporre sia il tipo per cui è stata filtrata l'azione del nodo della sintassi:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Avviare Visual Studio con l'analizzatore la prima volta

Avviare Visual Studio compilando ed eseguendo l'analizzatore (premere **F5).** Poiché il progetto di avvio nel **Esplora soluzioni** è il progetto VSIX, l'esecuzione del codice compila il codice e un vsix e quindi avvia Visual Studio con tale VSIX installato. Quando si avvia Visual Studio in questo modo, viene avviato con un hive del Registro di sistema distinto in modo che l'uso principale di Visual Studio non sia influenzato dalle istanze di test durante la compilazione degli analizzatori. La prima volta che si avvia in questo modo, Visual Studio diverse inizializzazioni simili a quelle Visual Studio dopo l'installazione.

Creare un progetto console e quindi immettere il codice della matrice nel metodo Main delle applicazioni console:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Le righe di codice con hanno righe a righe a righe di testo a righe non modificabili perché è necessario ottenere il pacchetto NuGet non modificabile e aggiungere `ImmutableArray` `using` un'istruzione al codice. Premere il pulsante destro del puntatore sul nodo del **progetto** nel Esplora soluzioni e scegliere **Gestisci NuGet pacchetti**. Nella finestra di NuGet manager digitare "Immutable" nella casella di ricerca e scegliere l'elemento **System.Collections.Immutable** (non scegliere **Microsoft.Bcl.Immutable)** nel riquadro sinistro e premere il **pulsante Installa** nel riquadro destro. L'installazione del pacchetto aggiunge un riferimento ai riferimenti al progetto.

Sono ancora presenti linee a linee a linee rosse in , quindi posizionare il punto di controllo in tale identificatore `ImmutableArray` e premere **CTRL** + **.** (punto) per visualizzare il menu delle correzioni suggerite e scegliere di aggiungere l'istruzione `using` appropriata.

**Salva tutto e chiudi** la seconda istanza di Visual Studio per il momento per impostare uno stato pulito per continuare.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Completare l'analizzatore usando Modifica e continuazione

Nella prima istanza di Visual Studio impostare un punto di interruzione all'inizio del metodo premendo F9 con il punto di `AnalyzeObjectCreation` interruzione nella prima riga. 

Avviare di nuovo l'analizzatore **con F5** e nella seconda istanza di Visual Studio riaprire l'applicazione console creata l'ultima volta.

Si torna alla prima istanza di Visual Studio punto di interruzione perché il compilatore Roslyn ha visto un'espressione di creazione di oggetti e ha chiamato nell'analizzatore.

**Ottiene il nodo di creazione dell'oggetto.** Eseguire un'istruzione alla riga che imposta `objectCreation` la variabile premendo **F10** e nella finestra di controllo **immediato** valutare l'espressione `"objectCreation.ToString()"` . Si noti che il nodo della sintassi a cui punta la variabile è il codice , proprio `"new ImmutableArray<int>()"` quello che si sta cercando.

**Ottenere ImmutableArray<tipo \> T.** È necessario controllare se il tipo creato è ImmutableArray. In primo luogo, si ottiene l'oggetto che rappresenta questo tipo. È possibile controllare i tipi usando il modello semantico per assicurarsi di avere esattamente il tipo corretto e non confrontare la stringa da `ToString()` . Immettere la riga di codice seguente alla fine della funzione:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

I tipi generici vengono designati nei metadati con gli inserviti (') e il numero di parametri generici. Per questo motivo non viene visualizzato "... ImmutableArray \<T> " nel nome dei metadati.

Il modello semantico include molti elementi utili che consentono di porre domande su simboli, flusso di dati, durata variabile e così via. Roslyn separa i nodi della sintassi dal modello semantico per vari motivi di progettazione (prestazioni, modellazione di codice ergogoo e così via). Si vuole che il modello di compilazione ricerca le informazioni contenute nei riferimenti per un confronto accurato.

È possibile trascinare il puntatore di esecuzione giallo sul lato sinistro della finestra dell'editor. Trascinarlo verso l'alto nella riga che imposta la variabile ed eseguire `objectCreation` un'istruzione alla riga di codice usando **F10.** Se si passa il puntatore del mouse sulla variabile , si può vedere che è stato trovato il tipo `immutableArrayOfType` esatto nel modello semantico.

**Ottiene il tipo dell'espressione di creazione dell'oggetto.** "Type" viene usato in diversi modi in questo articolo, ma questo significa che se si ha un'espressione "new Foo", è necessario ottenere un modello di Foo. È necessario ottenere il tipo dell'espressione di creazione dell'oggetto per verificare se si tratta del tipo \<T> ImmutableArray. Usare di nuovo il modello semantico per ottenere informazioni sui simboli per il simbolo di tipo (ImmutableArray) nell'espressione di creazione dell'oggetto. Immettere la riga di codice seguente alla fine della funzione:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Poiché l'analizzatore deve gestire codice incompleto o non corretto nei buffer dell'editor (ad esempio, è presente un'istruzione mancante), è necessario verificare `using` `symbolInfo` che sia `null` . È necessario ottenere un tipo denominato (INamedTypeSymbol) dall'oggetto informazioni sui simboli per completare l'analisi.

**Confrontare i tipi.** Poiché è presente un tipo generico aperto di T che si sta cercando e il tipo nel codice è un tipo generico concreto, è possibile eseguire una query sulle informazioni sui simboli per trovare l'elemento da cui viene costruito il tipo (un tipo generico aperto) e confrontare il risultato con `immutableArrayOfTType` . Immettere quanto segue alla fine del metodo :

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Segnalare la diagnostica.** La segnalazione della diagnostica è piuttosto semplice. Usare la regola creata automaticamente nel modello di progetto, definito prima del metodo Initialize. Poiché questa situazione nel codice è un errore, è possibile modificare la riga che ha inizializzato Rule in modo che sostituisca (linea on line `DiagnosticSeverity.Warning` verde) con `DiagnosticSeverity.Error` (linea a righe onnipresente rossa). Il resto della regola viene inizializzato dalle risorse modificate all'inizio della procedura dettagliata. È anche necessario segnalare la posizione per la stringa onnipresente, ovvero la posizione della specifica del tipo dell'espressione di creazione dell'oggetto. Immettere questo codice nel `if` blocco :

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

Rimuovere il punto di interruzione in modo che sia possibile vedere l'analizzatore funzionante (e interrompere il ritorno alla prima istanza di Visual Studio). Trascinare il puntatore di esecuzione all'inizio del metodo e premere **F5** per continuare l'esecuzione. Quando si torna alla seconda istanza di Visual Studio, il compilatore inizierà a esaminare nuovamente il codice e chiamerà l'analizzatore. È possibile visualizzare una stringa onnipresente in `ImmutableType<int>` .

## <a name="adding-a-code-fix-for-the-code-issue"></a>Aggiunta di una "correzione del codice" per il problema di codice

Prima di iniziare, chiudere la seconda istanza di Visual Studio e arrestare il debug nella prima istanza di Visual Studio (in cui si sta sviluppando l'analizzatore).

**Aggiungere una nuova classe.** Usare il menu di scelta rapida (pulsante del puntatore a destra) nel nodo del progetto **nel** Esplora soluzioni e scegliere di aggiungere un nuovo elemento. Aggiungere una classe denominata `BuildCodeFixProvider` . Questa classe deve derivare da `CodeFixProvider` e sarà necessario usare  + **CTRL.** (punto) per richiamare la correzione del codice che aggiunge l'istruzione `using` corretta. Questa classe deve anche essere annotata con l'attributo e sarà necessario aggiungere `ExportCodeFixProvider` `using` un'istruzione per risolvere `LanguageNames` l'enumerazione. Dovrebbe essere presente un file di classe con il codice seguente:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Stub dei membri derivati.** Inserire ora il punto di accesso dell'editor nell'identificatore `CodeFixProvider` e premere **CTRL** + **.** (punto) per eseguire lo stub dell'implementazione per questa classe di base astratta. In questo modo vengono generati automaticamente una proprietà e un metodo .

**Implementare la proprietà .** Compilare `FixableDiagnosticIds` il corpo della `get` proprietà con il codice seguente:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn riunisce la diagnostica e le correzioni abbinando questi identificatori, che sono semplicemente stringhe. Il modello di progetto ha generato automaticamente un ID di diagnostica ed è possibile modificarlo. Il codice nella proprietà restituisce semplicemente l'ID dalla classe dell'analizzatore.

**Il metodo RegisterCodeFixAsync accetta un contesto.** Il contesto è importante perché una correzione del codice può essere applicata a più diagnostica o potrebbe esserci più di un problema in una riga di codice. Se si digita "context". Nel corpo del metodo l'elenco di completamento IntelliSense mostrerà alcuni membri utili. È presente un membro CancellationToken che è possibile controllare per verificare se si vuole annullare la correzione. È presente un membro Document che ha molti membri utili e consente di accedere agli oggetti del modello di progetto e di soluzione. È presente un membro Span che rappresenta l'inizio e la fine della posizione del codice specificata quando è stata segnalata la diagnostica.

**Rendere il metodo asincrono.** La prima cosa da fare è correggere la dichiarazione del metodo generata in modo che sia un `async` metodo. La correzione del codice per lo stub dell'implementazione di una classe astratta non include la parola chiave anche se `async` il metodo restituisce `Task` .

**Ottiene la radice dell'albero della sintassi.** Per modificare il codice è necessario produrre un nuovo albero della sintassi con le modifiche apportate dalla correzione del codice. È necessario che `Document` dal contesto chiami `GetSyntaxRootAsync` . Si tratta di un metodo asincrono perché è presente un lavoro sconosciuto per ottenere l'albero della sintassi, possibilmente includendo il recupero del file dal disco, l'analisi e la compilazione del modello di codice Roslyn. L Visual Studio interno dell'interfaccia utente deve essere reattiva durante questo periodo di tempo, che l'uso di `async` abilita. Sostituire la riga di codice nel metodo con il codice seguente:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Trovare il nodo con il problema.** Si passa l'intervallo del contesto, ma il nodo trovato potrebbe non essere il codice che è necessario modificare. La diagnostica segnalata ha fornito solo l'intervallo per l'identificatore del tipo (a cui appartiene la stringa di onnipresente), ma è necessario sostituire l'intera espressione di creazione dell'oggetto, inclusa la parola chiave all'inizio e le parentesi alla `new` fine. Aggiungere il codice seguente al metodo e usare + **CTRL.** per aggiungere `using` un'istruzione per `ObjectCreationExpressionSyntax` ):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Registrare la correzione del codice per l'interfaccia utente della lampadina.** Quando si registra la correzione del codice, Roslyn si collega automaticamente all'interfaccia utente Visual Studio lampadina. Gli utenti finali potranno usare + **CTRL.** (punto) quando l'analizzatore esegue la disagazione di un uso `ImmutableArray<T>` del costruttore non erato. Poiché il provider di correzione del codice viene eseguito solo quando si verifica un problema, è possibile presupporre di avere l'espressione di creazione dell'oggetto che si stava cercando. Dal parametro context è possibile registrare la nuova correzione del codice aggiungendo il codice seguente alla fine del `RegisterCodeFixAsync` metodo :

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

È necessario inserire il punto di accesso dell'editor nell'identificatore, `CodeAction` , quindi usare  + **CTRL.** (punto) per aggiungere `using` l'istruzione appropriata per questo tipo.

Posizionare quindi il punto di accesso dell'editor `ChangeToImmutableArrayEmpty` nell'identificatore e usare  + **CTRL.** per generare automaticamente questo stub del metodo.

L'ultimo frammento di codice aggiunto registra la correzione del codice passando un e `CodeAction` l'ID di diagnostica per il tipo di problema rilevato. In questo esempio è presente un solo ID di diagnostica per cui questo codice fornisce correzioni, quindi è possibile passare solo il primo elemento della matrice di ID di diagnostica. Quando si crea , si passa il testo che l'interfaccia utente della lampadina `CodeAction` deve usare come descrizione della correzione del codice. Si passa anche una funzione che accetta un CancellationToken e restituisce un nuovo documento. Il nuovo documento include un nuovo albero della sintassi che include il codice con patch che chiama `ImmutableArray.Empty` . Questo frammento di codice usa un'espressione lambda in modo che possa chiudersi sul nodo objectCreation e sul documento del contesto.

**Costruire il nuovo albero della sintassi.** Nel metodo `ChangeToImmutableArrayEmpty` di cui è stato generato lo stub in precedenza immettere la riga di codice: `ImmutableArray<int>.Empty;` . Se si visualizza nuovamente **la Syntax Visualizer** degli strumenti, è possibile vedere che questa sintassi è un nodo SimpleMemberAccessExpression. Questo è ciò che questo metodo deve costruire e restituire in un nuovo documento.

La prima modifica a `ChangeToImmutableArrayEmpty` è l'aggiunta di prima perché i generatori di codice non possono `async` `Task<Document>` presupporre che il metodo debba essere asincrono.

Compilare il corpo con il codice seguente in modo che il metodo sia simile al seguente:

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

È necessario inserire il caret dell'editor nell'identificatore `SyntaxGenerator` e usare  + **CTRL.** (punto) per aggiungere `using` l'istruzione appropriata per questo tipo.

Questo codice usa `SyntaxGenerator` , che è un tipo utile per la costruzione di nuovo codice. Dopo aver generato un generatore per il documento che presenta il problema di codice, chiama , passando il tipo con il membro a cui si vuole accedere e passando il nome del membro `ChangeToImmutableArrayEmpty` `MemberAccessExpression` come stringa.

Successivamente, il metodo recupera la radice del documento e, poiché ciò può comportare operazioni arbitrarie nel caso generale, il codice attende questa chiamata e passa il token di annullamento. I modelli di codice Roslyn non sono modificabili, come l'uso di una stringa .NET. Quando si aggiorna la stringa, viene restituito un nuovo oggetto stringa. Quando si chiama `ReplaceNode` , si ottiene un nuovo nodo radice. La maggior parte dell'albero della sintassi è condivisa (perché non è modificabile), ma il nodo viene sostituito con il nodo , nonché con tutti i nodi padre fino alla radice dell'albero `objectCreation` `memberAccess` della sintassi.

## <a name="try-your-code-fix"></a>Provare la correzione del codice

È ora possibile premere **F5 per** eseguire l'analizzatore in una seconda istanza di Visual Studio. Aprire il progetto console usato in precedenza. A questo punto dovrebbe essere visualizzata la lampadina in cui la nuova espressione di creazione dell'oggetto è per `ImmutableArray<int>` . Se si preme + **CTRL.** (punto), verrà visualizzata la correzione del codice e nell'interfaccia utente della lampadina verrà visualizzata un'anteprima della differenza di codice generata automaticamente. Roslyn crea automaticamente questa opzione.

**Pro suggerimento:** Se si avvia la seconda istanza di Visual Studio e non viene visualizzata la lampadina con la correzione del codice, potrebbe essere necessario cancellare la cache Visual Studio componente. La cancellazione della cache forza Visual Studio a esaminare nuovamente i componenti, quindi Visual Studio necessario prelevare il componente più recente. Arrestare prima di tutto la seconda istanza di Visual Studio. In Esplora Windows **passare** quindi a *%LOCALAPPDATA%\Microsoft\VisualStudio\16.0Roslyn. \\* La versione "16.0" cambia da una versione all'altra con Visual Studio. Eliminare la sottodirectory *ComponentModelCache*.

## <a name="talk-video-and-finish-code-project"></a>Video di presentazione e completamento del progetto di codice

È possibile vedere questo esempio sviluppato e illustrato in modo più completo in [questo discorso.](https://channel9.msdn.com/events/Build/2015/3-725) Il discorso illustra l'analizzatore funzionante e illustra come compilarlo.

È possibile visualizzare tutto il codice completato [qui.](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) Le sottocartelle *DoNotUseImmutableArrayCollectionInitializer* e *DoNotUseImmutableArrayCtor* hanno ognuna un file C# per la ricerca dei problemi e un file C# che implementa le correzioni del codice che vengono visualizzati nell'interfaccia utente della lampadina di Visual Studio. Si noti che il codice completato ha un'astrazione leggermente maggiore per evitare di recuperare l'oggetto di tipo ImmutableArray \<T> più volte. Usa azioni registrate annidate per salvare l'oggetto tipo in un contesto disponibile ogni volta che vengono eseguite le sotto-azioni (analizzare la creazione di oggetti e analizzare le inizializzazioni della raccolta).

## <a name="see-also"></a>Vedi anche

* [\\\Build 2015 talk](https://channel9.msdn.com/events/Build/2015/3-725)
* [Codice completato in GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Diversi esempi di GitHub, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Altri documenti nel sito oss GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Regole FxCop implementate con gli analizzatori Roslyn GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
