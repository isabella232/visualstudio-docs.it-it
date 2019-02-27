---
title: Gli analizzatori di Roslyn e libreria con riconoscimento del codice per ImmutableArrays | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 753201d8f09b93186cac279d20dee2c7f3e1534d
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56843312"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Gli analizzatori di Roslyn e libreria con riconoscimento del codice per ImmutableArrays

Il [.NET Compiler Platform](https://github.com/dotnet/roslyn) ("Roslyn") consente di creare librerie con riconoscimento del codice. Una libreria con riconoscimento del codice fornisce la funzionalità che è possibile usare e agli strumenti (analizzatori di Roslyn) per l'uso della libreria nel modo migliore o per evitare errori. In questo argomento illustra come compilare un analizzatore Roslyn reale per rilevare gli errori comuni quando si usa la [Immutable](https://www.nuget.org/packages/System.Collections.Immutable) pacchetto NuGet. L'esempio illustra inoltre come fornire una correzione del codice per un problema di codice rilevato dall'analizzatore. Gli utenti visualizzano le correzioni del codice in Visual Studio lampadina dell'interfaccia utente e possono applicare una correzione per il codice automaticamente.

## <a name="get-started"></a>Introduzione

È necessario quanto segue per compilare questo esempio:

* Visual Studio 2015 (non una versione Express Edition) o versione successiva. È possibile usare la versione gratuita [Visual Studio Community Edition](https://visualstudio.microsoft.com/vs/community/)
* [Visual Studio SDK](../extensibility/visual-studio-sdk.md). È anche possibile, quando si installa Visual Studio, controllare **Visual Studio Extensibility Tools** sotto **strumenti comuni** per installare il SDK nello stesso momento. Se già stato installato Visual Studio, è anche possibile installare questo SDK, passare al menu principale **File** > **New** > **progetto**, scelta **c#** nel riquadro di spostamento a sinistra e quindi scegliere **estendibilità**. Quando si sceglie di "**installare Visual Studio Extensibility Tools**" modello di progetto di navigazione, viene richiesto di scaricare e installare il SDK.
* [.NET compiler Platform ("Roslyn") SDK](https://aka.ms/roslynsdktemplates). È anche possibile installare questo SDK, passare al menu principale **File** > **New** > **progetto**scegliere **c#** nel riquadro di spostamento a sinistra e scegliendo **estendibilità**. Quando si sceglie "**Download di .NET Compiler Platform SDK**" modello di progetto di navigazione, viene richiesto di scaricare e installare il SDK. Questo SDK include il [Visualizzatore di sintassi Roslyn](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). In questo modo, lo strumento utile capire quali tipi di modello di codice è necessario ricercare nell'analizzatore. Le chiamate di infrastruttura analyzer nel codice per tipi di modello di codice specifico, in modo che il codice viene eseguito quando è necessario solo e concentrarsi solo sull'analisi del codice pertinente.

## <a name="whats-the-problem"></a>Qual è il problema?

Imagine è fornire una libreria con ImmutableArray (ad esempio, <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>) supportano. Gli sviluppatori c# hanno molta esperienza con le matrici .NET. Tuttavia, a causa della natura delle tecniche ImmutableArrays e ottimizzazione utilizzato nell'implementazione, intuitions per gli sviluppatori c# causare agli utenti della libreria di scrivere codice danneggiato, come illustrato di seguito. Inoltre, gli utenti non vengono visualizzati i relativi errori fino al runtime, che non è l'esperienza di qualità che vengono utilizzati per Visual Studio con .NET.

Gli utenti hanno familiarità con la scrittura di codice simile al seguente:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);
```

Creazione di matrici vuote deve compilare con le righe successive del codice e usando la sintassi dell'inizializzatore di raccolta sono familiari agli C# gli sviluppatori. Tuttavia, il codice per un ImmutableArray scrivere lo stesso arresto anomalo in fase di esecuzione:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);
```

Il primo errore è a causa dell'implementazione ImmutableArray usando un tipo struct per eseguire il wrapping dell'archivio dati sottostante. Struct devono avere costruttori senza parametri in modo che `default(T)` espressioni possono restituire gli struct con tutti i membri null o zero. Quando il codice accede `b1.Length`, c'è un valore null alla fase di esecuzione dereferenziare errore perché non contiene alcun array di archiviazione sottostante lo struct ImmutableArray. Il modo corretto per creare un ImmutableArray vuoto è `ImmutableArray<int>.Empty`.

L'errore con gli inizializzatori di raccolta si verifica perché il `ImmutableArray.Add` metodo restituisce nuove istanze ogni volta che viene chiamata. Poiché ImmutableArrays non cambiare mai, quando si aggiunge un nuovo elemento, si ottiene un nuovo oggetto ImmutableArray (che potrà condividere l'archiviazione per motivi di prestazioni con un ImmutableArray già esistente). In quanto `b2` punta al primo ImmutableArray prima di chiamare `Add()` cinque volte, `b2` è un'impostazione predefinita ImmutableArray. Chiamata di lunghezza su di esso anche arresti anomali del sistema con un valore null dereferenziare l'errore. Il modo corretto per inizializzare un ImmutableArray senza manualmente la chiamata a Add, è possibile usare `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="find-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Trovare i tipi di nodo per attivare l'analizzatore sintassi rilevante

 Per iniziare a compilare l'analizzatore, prima di tutto capire quale tipo di SyntaxNode da cercare. Avviare il **Visualizzatore di sintassi** dal menu **View** > **Other Windows** > **Visualizzatore di sintassi Roslyn**.

Posizionare il cursore dell'editor nella riga che dichiara `b1`. Verrà visualizzato il Visualizzatore di sintassi viene illustrato come trovano in un `LocalDeclarationStatement` nodo dell'albero della sintassi. Questo nodo ha un `VariableDeclaration`, che a sua volta ha un `VariableDeclarator`, che a sua volta ha un `EqualsValueClause`e infine è disponibile un `ObjectCreationExpression`. Quando fa clic l'albero di Visualizzatore di sintassi di nodi, la sintassi nella finestra dell'editor vengono evidenziati per visualizzare il codice rappresentato da tale nodo. I nomi dei tipi sub SyntaxNode corrispondono i nomi usati nella grammatica del linguaggio c#.

## <a name="create-the-analyzer-project"></a>Creare il progetto dell'analizzatore

Dal menu principale, scegliere **File** > **New** > **progetto**. Nel **nuovo progetto** finestra di dialogo, sotto **c#** progetti nella barra di spostamento a sinistra, scegliere **estendibilità**e nel riquadro destro scegliere il **Analyzer con Correzione del codice** modello di progetto. Immettere un nome e la finestra di dialogo di conferma.

Il modello verrà aperto un *DiagnosticAnalyzer.cs* file. Scegliere la scheda buffer tale editor. Questo file contiene una classe analyzer (formata dal nome assegnato al progetto) che deriva da `DiagnosticAnalyzer` (un tipo di API Roslyn). La nuova classe ha un `DiagnosticAnalyzerAttribute` dichiarando l'analizzatore è rilevante per il linguaggio c# in modo che il compilatore individua e carica l'analizzatore.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

È possibile implementare un analizzatore utilizzando Visual Basic destinata a codice c#, e viceversa. È più importante in DiagnosticAnalyzerAttribute per scegliere se l'analizzatore è destinata a una lingua o entrambi. Gli analizzatori più sofisticati che richiedono dettagliata modellazione del linguaggio possono avere come destinazione solo una sola lingua. Se l'analizzatore, controlli, ad esempio, solo i nomi dei tipi o i nomi dei membri pubblici, potrebbe essere possibile usare il modello di lingua comune che offre Roslyn in Visual Basic e c#. Ad esempio, FxCop avverte che una classe che implementa <xref:System.Runtime.Serialization.ISerializable>, ma la classe non dispone di <xref:System.SerializableAttribute> attributo è indipendente dal linguaggio e funziona per il codice Visual Basic e c#.

## <a name="initialize-the-analyzer"></a>Inizializzare l'analizzatore

 Scorrere verso il basso un po' `DiagnosticAnalyzer` classe per visualizzare il `Initialize` (metodo). Il compilatore chiama questo metodo quando si attiva un analizzatore. Il metodo accetta un `AnalysisContext` oggetto che consente l'analizzatore per ottenere informazioni sul contesto e registrazione di callback per gli eventi per i tipi di codice da analizzare.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Aprire una nuova riga in questo metodo e il tipo "contesto". Per visualizzare un elenco di completamento IntelliSense. È possibile vedere nell'elenco di completamento sono disponibili molti `Register...` metodi per gestire vari tipi di eventi. Ad esempio, il primo webhook `RegisterCodeBlockAction`, le chiamate al codice per un blocco, ovvero in genere codice tra parentesi graffe. La registrazione per un blocco anche richiama il codice per l'inizializzatore di campo, il valore assegnato a un attributo o il valore di un parametro facoltativo.

Come ulteriore esempio, `RegisterCompilationStartAction`, richiama il codice all'inizio di una compilazione, che risulta utile quando è necessario raccogliere lo stato in molte posizioni. È possibile creare una struttura di dati, ad esempio, per raccogliere tutti i simboli usati, e ogni volta che viene richiamato l'analizzatore per alcune sintassi o un simbolo, è possibile salvare informazioni su ogni posizione nella struttura dei dati. Quando è chiamato nuovamente a causa di terminazione di compilazione, è possibile analizzare tutti i percorsi è stato salvato, ad esempio, per segnalare i simboli nel codice viene utilizzato da ogni `using` istruzione.

Usando il **Visualizzatore di sintassi**, si è appreso che si desidera siano chiamati quando il compilatore elabora un ObjectCreationExpression. Usare questo codice per impostare il callback:

```csharp
context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Registra per un nodo della sintassi e il filtro per solo nodi di sintassi creazione oggetto. Per convenzione, gli autori di Analizzatore utilizzare un'espressione lambda quando si registra azioni, che consente di mantenere gli analizzatori senza stato. È possibile usare la funzionalità di Visual Studio **generazione dall'utilizzo** per creare il `AnalyzeObjectCreation` (metodo). Questo genera il tipo corretto di parametro di contesto eccessivo.

## <a name="set-properties-for-users-of-your-analyzer"></a>Impostare le proprietà per gli utenti dell'analizzatore

In modo che l'analizzatore viene visualizzato nell'interfaccia utente di Visual Studio in modo appropriato, cercare e modificare la riga di codice per identificare l'analizzatore seguente:

```csharp
internal const string Category = "Naming";
```

Change `"Naming"` a `"API Guidance"`.

Quindi trovare e aprire il *Resources. resx* file nel progetto usando la **Esplora soluzioni**. È possibile inserire una descrizione per l'analizzatore, titolo, e così via. È possibile modificare il valore per tutti i componenti su `"Don't use ImmutableArray<T> constructor"` per il momento. È possibile inserire gli argomenti della stringa di formattazione delle stringhe ({0}, {1}e così via) e versioni successive quando si chiama `Diagnostic.Create()`, è possibile fornire un `params` matrice di argomenti da passare.

## <a name="analyze-an-object-creation-expression"></a>Analizzare un'espressione di creazione di oggetti

Il `AnalyzeObjectCreation` metodo accetta un tipo diverso di contesto fornito dal framework dell'analizzatore di codice. Il `Initialize` del metodo `AnalysisContext` consente di registrare i callback di azione per configurare l'analizzatore. Il `SyntaxNodeAnalysisContext`, ad esempio, ha un `CancellationToken` che è possibile passare agli altri. Se un utente avvia la digitazione nell'editor, Roslyn annullerà gli analizzatori in esecuzione per risparmiare lavoro e migliorare le prestazioni. Come ulteriore esempio, questo contesto dispone di una proprietà dei nodi che restituisce il nodo di sintassi di creazione di oggetti.

Ottenere il nodo che si può presupporre che il tipo per cui è applicato l'azione di nodi di sintassi:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launch-visual-studio-with-your-analyzer-the-first-time"></a>Avviare Visual Studio con l'analizzatore la prima volta

Avviare Visual Studio tramite la creazione e l'esecuzione di analizzatore (premere **F5**). Poiché l'avvio del progetto nel **Esplora soluzioni** sia il progetto VSIX, le compilazioni di codice in esecuzione il codice e un file VSIX e quindi avvia Visual Studio con tale estensione VSIX installate. Quando si avvia Visual Studio in questo modo, viene avviato con un hive del Registro di sistema distinte in modo che l'uso principale di Visual Studio verrà influenzato da istanze di test durante la compilazione di analizzatori. La prima volta che si avvia in questo modo, Visual Studio esegue le inizializzazioni più simile a quando avviata prima di tutto Visual Studio dopo l'installazione.

Creare un progetto console e quindi immettere il codice a matrice nel metodo Main le applicazioni console:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);
```

Le righe di codice con `ImmutableArray` sono sottolineature perché è necessario ottenere il pacchetto NuGet non modificabile e aggiungere un `using` istruzione nel codice. Premere il pulsante destro del puntatore sul nodo del progetto nel **Esplora soluzioni** e scegliere **Gestisci pacchetti NuGet**. In Gestione NuGet, digitare "Non modificabile" nella casella di ricerca e scegliere la voce **Immutable** (non si sceglie **Immutable**) nel riquadro a sinistra e premere il  **Installare** pulsante nel riquadro di destra. Installazione del pacchetto aggiunge un riferimento ai riferimenti del progetto.

Noterete ancora che righe rosse a zigzag sotto `ImmutableArray`, quindi posizionare il cursore in tale identificatore e premere **Ctrl**+**.** (punto) per visualizzare il menu di scelta di correzione suggerita e scegliere di aggiungere appropriato `using` istruzione.

**Salvare e chiudere** la seconda istanza di Visual Studio per il momento è inserire in uno stato pulito per continuare.

## <a name="finish-the-analyzer-using-edit-and-continue"></a>Fine dell'analizzatore di utilizzare Modifica e continuazione

Nella prima istanza di Visual Studio, impostare un punto di interruzione all'inizio del `AnalyzeObjectCreation` metodo premendo **F9** con il cursore sulla prima riga.

Avviare nuovamente con l'analizzatore **F5**e nella seconda istanza di Visual Studio, riaprire l'applicazione console è creata l'ultima volta.

Tornare alla prima istanza di Visual Studio nel punto di interruzione perché il compilatore Roslyn visto un'espressione di creazione di oggetti e ha l'analizzatore.

**Ottenere il nodo di creazione di oggetti.** Esegui istruzione/routine la riga che imposta il `objectCreation` variabile premendo **F10**e il **finestra controllo immediato** valutare l'espressione `"objectCreation.ToString()"`. Si noterà che il nodo di sintassi la variabile punta a è il codice `"new ImmutableArray<int>()"`, semplicemente ciò che sta cercando.

**Ottenere ImmutableArray < T\> oggetto tipo.** È necessario controllare se il tipo creato è ImmutableArray. In primo luogo, si ottiene l'oggetto che rappresenta questo tipo. Si verifica tipi tramite il modello semantico per assicurarsi di avere esattamente del tipo corretto e non si confronta la stringa da `ToString()`. Immettere la seguente riga di codice alla fine della funzione:

```csharp
var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");
```

Specificare i tipi generici nei metadati tra apici inversi (') e il numero di parametri generici. Questo è il motivo per cui non viene visualizzato "... ImmutableArray\<T > "nel nome dei metadati.

Il modello semantico dispone di molte operazioni utili che consentono di porre domande sui simboli del flusso di dati, la durata delle variabili, e così via. Roslyn separa i nodi di sintassi dal modello semantico per vari motivi tecnici (prestazioni, modellazione codice errato e così via). Si desidera il modello di compilazione per cercare le informazioni contenute nei riferimenti per il confronto accurato.

È possibile trascinare il puntatore di esecuzione giallo sul lato sinistro della finestra dell'editor. Trascinarlo fino alla riga che imposta la `objectCreation` variabile ed Esegui istruzione/routine di nuova riga di codice usando **F10**. Se si posiziona il puntatore del mouse sulla variabile `immutableArrayOfType`, noterete che è stato rilevato il tipo esatto nel modello semantico.

**Ottenere il tipo dell'espressione di creazione oggetto.** "Type" viene usato in diversi modi in questo articolo, ma ciò significa che se hai "nuovo Foo" espressione, è necessario ottenere un modello di Foo. È necessario ottenere il tipo dell'espressione di creazione oggetto per verificare se è ImmutableArray\<T > tipo. Usare il modello semantico nuovamente per ottenere informazioni sui simboli per il simbolo di tipo (ImmutableArray) nell'espressione di creazione di oggetti. Immettere la seguente riga di codice alla fine della funzione:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type).Symbol as INamedTypeSymbol;
```

Perché l'analizzatore deve gestire codice incompleto o non corretto nel buffer dell'editor (ad esempio, manca un `using` istruzione), è consigliabile ricercare `symbolInfo` da `null`. È necessario ottenere un tipo denominato (INamedTypeSymbol) dall'oggetto simbolo informazioni per completare l'analisi.

**Confrontare i tipi.** Poiché è un tipo generico aperto di T che stiamo cercando e il tipo nel codice è un tipo generico concreto, si eseguono query le informazioni sui simboli per il tipo è costruito da (un tipo generico aperto) e confrontare tale risultato con `immutableArrayOfTType`. Immettere quanto segue alla fine del metodo:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Report di diagnostica.** Creazione di report di diagnostica è piuttosto semplice. Si usa la regola creata nel modello di progetto, che viene definito prima il metodo Initialize. Poiché questa situazione nel codice è un errore, è possibile modificare la riga di inizializzazione regola per sostituire `DiagnosticSeverity.Warning` (linee a zigzag verde) con `DiagnosticSeverity.Error` (sottolineatura ondulata rossa). Il resto della regola Inizializza dalle risorse di cui che è stato modificato nella parte iniziale della procedura dettagliata. È necessario anche segnalare la posizione per la sottolineatura a zigzag, ovvero la posizione della specifica del tipo dell'espressione di creazione oggetto. Immettere il codice di `if` blocco:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

La funzione dovrebbe essere simile al seguente (forse formattato in modo diverso):

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

Rimuovere il punto di interruzione in modo che è possibile vedere l'utilizzo di analizzatore (e arresta la restituzione alla prima istanza di Visual Studio). Trascinare il puntatore di esecuzione all'inizio del metodo e premere **F5** per continuare l'esecuzione. Quando si passa nuovamente alla seconda istanza di Visual Studio, il compilatore inizieranno a esaminare il codice nuovo e chiamerà l'analizzatore. È possibile visualizzare una sottolineatura ondulata sotto `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Aggiunta di una "correzione del codice" per il rilascio di codice

Prima di iniziare, chiudere la seconda istanza di Visual Studio e arrestare il debug della prima istanza di Visual Studio (in cui si sta sviluppando l'analizzatore).

**Aggiungere una nuova classe.** Usare il menu di scelta rapida (pulsante destro del puntatore) sul nodo del progetto nel **Esplora soluzioni** e scegliere di aggiungere un nuovo elemento. Aggiungere una classe denominata `BuildCodeFixProvider`. Questa classe deve derivare da `CodeFixProvider`, e sarà necessario usare **Ctrl**+**.** (punto) per richiamare la correzione del codice che aggiunge il valore corretto `using` istruzione. Questa classe deve inoltre essere annotata con `ExportCodeFixProvider` attributo e si dovranno aggiungere un' `using` istruzione per risolvere il `LanguageNames` enum. È necessario disporre di un file di classe con il codice seguente:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}
```

**Eliminare i membri derivati.** A questo punto, posizionare il cursore dell'editor nell'identificatore `CodeFixProvider` e premere **Ctrl**+**.** (punto) da sottoporre a stub di implementazione per questa classe base astratta. Questo genera una proprietà e un metodo.

**Implementa la proprietà.** Immettere il `FixableDiagnosticIds` della proprietà `get` corpo con il codice seguente:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn offre diagnostica e correzioni creando una corrispondenza tra questi identificatori, che sono semplicemente stringhe. Il modello di progetto generati un ID di diagnostica per l'utente, ed è possibile modificarla. Il codice nella proprietà restituisce solo l'ID della classe analyzer.

**Il metodo RegisterCodeFixAsync accetta un contesto.** Il contesto è importante perché una correzione del codice è possibile applicare a più dati di diagnostica oppure potrebbero esserci più di un problema in una riga di codice. Se si digita "contesto". nel corpo del metodo, l'elenco di completamento IntelliSense illustrerà alcuni membri utile. È disponibile un membro oggetto CancellationToken che è possibile verificare se si desidera annullare la correzione. È disponibile un membro di documento che presenta un numero elevato di membri utili e consente di ottenere gli oggetti modello di progetto e soluzione. È un membro di intervallo che corrisponde all'inizio e fine del percorso del codice specificata quando è stato segnalato il messaggio di diagnostica.

**Impostare il metodo asincroni.** La prima operazione da eseguire è correggere la dichiarazione di metodo generato da un `async` (metodo). La correzione del codice per la generazione di stub per l'implementazione di una classe astratta non include il `async` parola chiave anche se il metodo restituisce un `Task`.

**Ottenere la radice dell'albero della sintassi.** Per modificare il codice che necessari per creare una nuova struttura di sintassi in base alle modifiche rende la correzione del codice. È necessario il `Document` dal contesto per chiamare `GetSyntaxRootAsync`. Questo è un metodo asincrono in quanto lavoro sconosciuto per ottenere l'albero della sintassi, magari con recupero del file dal disco, l'analisi e compilazione del modello di codice Roslyn per tale. L'interfaccia utente di Visual Studio deve essere reattiva durante questo periodo, quali utilizzo `async` Abilita. Sostituire la riga di codice nel metodo con il codice seguente:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Individuare il nodo con il problema.** Si passa nell'intervallo del contesto, ma il nodo che si trova potrebbe non essere il codice che si desidera modificare. La diagnostica restituita fornito solo l'intervallo per l'identificatore del tipo (in cui la sottolineatura a zigzag apparteneva), ma è necessario sostituire l'espressione di creazione di un oggetto intero, inclusi il `new` (parola chiave) all'inizio e alla fine delle parentesi. Aggiungere il codice seguente al metodo (allo stesso modo **Ctrl**+**.** Per aggiungere un `using` istruzione per `ObjectCreationExpressionSyntax`):

```csharp
var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

**Registrare la correzione del codice per la lampadina dell'interfaccia utente.** Quando si registra la correzione del codice, Roslyn viene inserito automaticamente nella lampadina Visual Studio dell'interfaccia utente. Verrà visualizzato agli utenti finali possono usare **Ctrl**+**.** (punto) quando l'analizzatore sottolineature a zigzag di un errato `ImmutableArray<T>` Usa costruttore. Poiché il provider di correzioni di codice viene eseguito solo quando si verifica un problema, è possibile si presuppone l'espressione di creazione oggetto cercato. Dal parametro di contesto, è possibile registrare la nuova correzione del codice aggiungendo il codice seguente alla fine della `RegisterCodeFixAsync` metodo:

```csharp
context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

È necessario posizionare il cursore dell'editor nell'identificatore `CodeAction`, quindi usare **Ctrl**+**.** (punto) per aggiungere l'oggetto appropriato `using` istruzione per questo tipo.

Quindi posizionare il cursore dell'editor nel `ChangeToImmutableArrayEmpty` identificatore e l'utilizzo **Ctrl**+**.** anche in questo caso per generare questo stub di metodo per l'utente.

È stato aggiunto il frammento di codice ultimo registra la correzione del codice, passando un `CodeAction` e l'ID di diagnostica per il tipo di problema rilevato. In questo esempio è presente un solo ID di diagnostica che questo codice fornisce correzioni per, pertanto è possibile passare solo il primo elemento della matrice ID di diagnostica. Quando si crea il `CodeAction`, si passa il testo utilizzato come una descrizione della correzione del codice la lampadina dell'interfaccia utente. È anche possibile passare in una funzione che accetta un oggetto CancellationToken e restituisce un nuovo documento. Il nuovo documento ha un nuovo albero della sintassi che includa il codice con patch che chiama `ImmutableArray.Empty`. Questo frammento di codice viene utilizzata un'espressione lambda in modo che è possibile chiudere il nodo objectCreation e documento del contesto.

**Costruire la nuova struttura di sintassi.** Nel `ChangeToImmutableArrayEmpty` metodo il cui stub generato in precedenza, immettere la riga di codice: `ImmutableArray<int>.Empty;`. Se si visualizza il **Visualizzatore di sintassi** finestra degli strumenti anche in questo caso, è possibile visualizzare questa sintassi è un nodo SimpleMemberAccessExpression. Questo è ciò che questo metodo deve costruire e restituire un nuovo documento.

La prima modifica apportata a `ChangeToImmutableArrayEmpty` consiste nell'aggiungere `async` prima di `Task<Document>` perché i generatori di codice non possono presupporre il metodo deve essere asincrono.

Specificare il corpo con il codice seguente in modo che il metodo è simile al seguente:

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

È necessario inserire il cursore dell'editor nel `SyntaxGenerator` identificatore e l'utilizzo **Ctrl**+**.** (punto) per aggiungere l'oggetto appropriato `using` istruzione per questo tipo.

Questo codice Usa `SyntaxGenerator`, ovvero un tipo utile per la costruzione di nuovo codice. Dopo il recupero di un generatore per il documento che contiene il problema di codice `ChangeToImmutableArrayEmpty` chiamate `MemberAccessExpression`, passando il tipo contenente il membro che vogliamo accedere e passando il nome del membro sotto forma di stringa.

Successivamente, il metodo recupera la radice del documento e, poiché ciò può implicare lavoro arbitrario nel caso generale, il codice attende la chiamata e passa il token di annullamento. Non sono modificabili, all'utilizzo di una stringa .NET; i modelli di codice Roslyn Quando si aggiorna la stringa, si ottiene in cambio un nuovo oggetto stringa. Quando si chiama `ReplaceNode`, si otterrà un nuovo nodo radice. La maggior parte dell'albero della sintassi è condivisa (poiché non è modificabile), ma il `objectCreation` nodo viene sostituito con il `memberAccess` nodo, nonché tutti i nodi padre fino alla radice dell'albero di sintassi.

## <a name="try-your-code-fix"></a>Provare la correzione del codice

È ora possibile premere **F5** per eseguire l'analizzatore in una seconda istanza di Visual Studio. Aprire il progetto di console usato in precedenza. A questo punto dovrebbe essere visualizzato la lampadina in cui la nuova espressione di creazione oggetto si riferisce `ImmutableArray<int>`. Se si preme **Ctrl**+**.** (periodo), quindi verrà visualizzato il codice correggere e si noterà un'anteprima di differenza del codice generato automaticamente nella lampadina dell'interfaccia utente. Roslyn crea automaticamente questo.

**Suggerimento Pro:** Se si avvia la seconda istanza di Visual Studio e non viene visualizzata la lampadina con la correzione del codice, potrebbe essere necessario cancellare la cache dei componenti di Visual Studio. La cancellazione della cache forza Visual Studio per esaminare nuovamente i componenti, in modo che Visual Studio deve selezionare il componente più recente. In primo luogo, arrestare la seconda istanza di Visual Studio. Quindi, nella **Windows Explorer**, passare alla *%LOCALAPPDATA%\Microsoft\VisualStudio\15.0Roslyn\\*. (Il "15.0" cambia da una versione a altra con Visual Studio). Eliminare le sottodirectory *ComponentModelCache*.

## <a name="talk-video-and-finish-code-project"></a>Comunicare con video e di fine progetto di codice

È possibile visualizzare in questo esempio viene sviluppato e illustrate dettagliatamente nella [in questo webcast](https://channel9.msdn.com/events/Build/2015/3-725). Il discorso dimostra l'analizzatore di lavoro e illustra la creazione.

È possibile visualizzare tutto il codice completato [qui](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Le sottocartelle *DoNotUseImmutableArrayCollectionInitializer* e *DoNotUseImmutableArrayCtor* ognuna dispone di un file c# per la ricerca di problemi e un file c# che implementa il codice corregge che mostrano nel Visual Studio lampadina dell'interfaccia utente. Si noti che il codice include una piccola astrazione altre per evitare il recupero ImmutableArray\<T > tipo di oggetto più volte. Usa le azioni registrate annidate per salvare l'oggetto di tipo in un contesto che è disponibile ogni volta che le azioni sub (analizzare la creazione di oggetti e analizzare le inizializzazioni raccolta) eseguire.

## <a name="see-also"></a>Vedere anche

* [\\Talk \Build 2015](https://channel9.msdn.com/events/Build/2015/3-725)
* [Codice completo in GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers)
* [Alcuni esempi su GitHub, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md)
* [Gli altri documenti nel sito GitHub OSS](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)
* [Regole FxCop implementate con analizzatori di Roslyn su GitHub](https://github.com/dotnet/roslyn/tree/master/src/Diagnostics/FxCop)
