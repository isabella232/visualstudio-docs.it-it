---
title: Analizzatori di Roslyn e libreria in grado di riconoscere il codice per ImmutableArrays Documenti Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
ms.assetid: 0b0afa22-3fca-4d59-908e-352464c1d903
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 65849a3d9ad1cdd073551f96e61997fe5f91118a
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444895"
---
# <a name="roslyn-analyzers-and-code-aware-library-for-immutablearrays"></a>Analizzatori Roslyn e libreria con riconoscimento del codice per ImmutableArrays
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La [piattaforma del compilatore .NET](https://github.com/dotnet/roslyn) ("Roslyn") consente di compilare librerie in grado di riconoscere il codice. Una libreria in grado di riconoscere il codice fornisce funzionalità che è possibile utilizzare e strumenti (analizzatori Roslyn) per utilizzare la libreria nel modo migliore o per evitare errori. In questo argomento viene illustrato come compilare un analizzatore Roslyn del mondo reale per rilevare errori comuni quando si usa il pacchetto [NIB: Immutable Collections](https://msdn.microsoft.com/library/33f4449d-7078-450a-8d60-d9229f66bbca) NuGet. Nell'esempio viene inoltre illustrato come fornire una correzione del codice per un problema di codice rilevato dall'analizzatore. Gli utenti visualizzano le correzioni del codice nell'interfaccia utente della lampadina di Visual Studio e possono applicare automaticamente una correzione per il codice.

## <a name="getting-started"></a>Introduzione
Per compilare questo esempio, è necessario quanto segue:You need the following to build this example:

- Visual Studio 2015 (non Express Edition) o versione successiva. È possibile utilizzare l'edizione gratuita di [Visual Studio Community Edition](https://www.visualstudio.com/products/visual-studio-community-vs)

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md). È anche possibile, durante l'installazione di Visual Studio, controllare gli strumenti di estensibilità di Visual Studio in Common Tools per installare l'SDK contemporaneamente. Se Visual Studio è già stato installato, è anche possibile installare questo SDK accedendo al menu principale **File &#124; Nuovo progetto &#124;...**, scegliendo C ' nel riquadro di spostamento a sinistra e quindi scegliendo Estensibilità. Quando si sceglie il modello di progetto breadcrumb " Installa gli strumenti di**estensibilità**di Visual Studio ", viene richiesto di scaricare e installare l'SDK.

- [.NET Compiler Platform ("Roslyn") SDK](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.NETCompilerPlatformSDK). È anche possibile installare questo SDK accedendo al menu principale **File &#124; Nuovo progetto di &#124; ...**, scegliendo C **'** nel riquadro di spostamento a sinistra e quindi scegliendo **Extensibility**. Quando si sceglie " Scarica il modello di progetto breadcrumb**di .NET Compiler Platform SDK,** viene richiesto di scaricare e installare l'SDK. Questo SDK include il [visualizzatore di sintassi Roslyn](https://github.com/dotnet/roslyn/wiki/Syntax%20Visualizer). Questo strumento estremamente utile consente di capire quali tipi di modello di codice è necessario cercare nell'analizzatore. L'infrastruttura dell'analizzatore chiama il codice per tipi di modello di codice specifici, in modo che il codice venga eseguito solo quando necessario e possa concentrarsi solo sull'analisi del codice pertinente.

## <a name="whats-the-problem"></a>Qual è il problema?
Si supponga di fornire una libreria con supporto <xref:System.Collections.Immutable.ImmutableArray%601?displayProperty=fullName>ImmutableArray (ad esempio, ). Gli sviluppatori di C' hanno molta esperienza con le matrici .NET. Tuttavia, a causa della natura di ImmutableArrays e delle tecniche di ottimizzazione utilizzate nell'implementazione, le intuizioni degli sviluppatori di C' fanno sì che gli utenti della libreria scrivano codice interrotto, come illustrato di seguito. Inoltre, gli utenti non vedono i propri errori fino alla fase di esecuzione, che non è l'esperienza di qualità a cui sono abituati in Visual Studio con .NET.

Gli utenti hanno familiarità con la scrittura di codice simile al seguente:Users are familiar with writing code like the following:

```csharp
var a1 = new int[0];
Console.WriteLine("a1.Length = { 0}", a1.Length);
var a2 = new int[] { 1, 2, 3, 4, 5 };
Console.WriteLine("a2.Length = { 0}", a2.Length);

```

La creazione di matrici vuote da compilare con le righe di codice successive e l'utilizzo della sintassi dell'inizializzatore di raccolta sono molto familiari agli sviluppatori di C. Tuttavia, la scrittura dello stesso codice per un ImmutableArray si blocca in fase di esecuzione:However, writing the same code for an ImmutableArray crashes at runtime:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = { 0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = { 0}", b2.Length);

```

Il primo errore è dovuto all'utilizzo di uno struct da parte dell'implementazione di ImmutableArray per eseguire il wrapping dell'archiviazione dei dati sottostante. Gli struct devono avere costruttori `default(T)` senza parametri in modo che le espressioni possano restituire struct con tutti i membri zero o null. Quando il codice `b1.Length`accede a , si verifica un errore di dereferenziazione null in fase di esecuzione perché non esiste alcuna matrice di archiviazione sottostante nella struttura ImmutableArray . Il modo corretto per creare un oggetto `ImmutableArray<int>.Empty`ImmutableArray vuoto è .

 L'errore con gli inizializzatori di raccolta si verifica perché il metodo ImmutableArray.Add restituisce nuove istanze ogni volta che viene chiamato. Poiché ImmutableArrays non cambia mai, quando si aggiunge un nuovo elemento, si ottiene un nuovo oggetto ImmutableArray (che può condividere l'archiviazione per motivi di prestazioni con un oggetto ImmutableArray precedentemente esistente). Poiché `b2` fa riferimento al primo ImmutableArray prima di chiamare `Add()` cinque volte, `b2` è un oggetto predefinito ImmutableArray. La chiamata di lunghezza su di esso si blocca anche con un errore di dereferenziazione null. Il modo corretto per inizializzare un Oggetto ImmutableArray senza chiamare manualmente Add consiste nell'utilizzare `ImmutableArray.CreateRange(new int[] {1, 2, 3, 4, 5})`.

## <a name="finding-relevant-syntax-node-types-to-trigger-your-analyzer"></a>Ricerca di tipi di nodo di sintassi pertinenti per attivare l'analizzatoreFinding Relevant Syntax Node Types to Trigger Your Analyzer
Per iniziare a compilare l'analizzatore, in primo luogo capire che tipo di SyntaxNode è necessario cercare.   Avviare il visualizzatore di sintassi dal menu **Visualizza &#124; altro visualizzatore sintassi di Roslyn &#124;**.

Posizionare il punto di inserimento dell'editor nella riga che dichiara `b1`. Verrà visualizzato il visualizzatore di sintassi `LocalDeclarationStatement` indica che ci si trova in un nodo dell'albero della sintassi. Questo nodo `VariableDeclaration`ha un oggetto `VariableDeclarator`, che a `EqualsValueClause`sua volta ha `ObjectCreationExpression`un oggetto , che a sua volta ha un oggetto , e infine c'è un oggetto . Quando si fa clic nell'albero del visualizzatore di sintassi dei nodi, la sintassi nella finestra dell'editor viene evidenziata per mostrare il codice rappresentato da tale nodo. I nomi dei sottotipi SyntaxNode corrispondono ai nomi utilizzati nella grammatica di C.

## <a name="creating-the-analyzer-project"></a>Creazione del progetto Analyzer
Dal menu principale scegliere **File &#124; Nuovo &#124; Progetto ...**. Nella finestra di dialogo **Nuovo progetto,** in Progetti **C '** nella barra di spostamento sinistra, scegliere Estensibilità e nel riquadro destro scegliere il modello di progetto **Analizzatore con correzione codice.** Immettere un nome e confermare la finestra di dialogo.

Il modello apre un file DiagnosticAnalyzer.cs. Scegliere la scheda del buffer dell'editor. Questo file ha una classe analizzatore (formata dal `DiagnosticAnalyzer` nome assegnato al progetto) che deriva da (un tipo di API Roslyn). La nuova classe `DiagnosticAnalyzerAttribute` dispone di un analizzatore dichiarante è rilevante per il linguaggio C , in modo che il compilatore individua e carica l'analizzatore.

```csharp
[DiagnosticAnalyzer(LanguageNames.CSharp)]
public class ImmutableArrayAnalyzerAnalyzer : DiagnosticAnalyzer
{}
```

È possibile implementare un analizzatore utilizzando Visual Basic destinato al codice C , e viceversa. È più importante in DiagnosticAnalyzerAttribute per scegliere se l'analizzatore è destinato a un linguaggio o entrambi. Analizzatori più sofisticati che richiedono la modellazione dettagliata del linguaggio possono essere destinati a una sola lingua. Se l'analizzatore, ad esempio, controlla solo i nomi dei tipi o i nomi dei membri pubblici, potrebbe essere possibile utilizzare il modello di linguaggio comune che Roslyn offre in Visual Basic e in C. Ad esempio, FxCop avverte <xref:System.Runtime.Serialization.ISerializable>che una classe implementa <xref:System.SerializableAttribute> , ma la classe non dispone dell'attributo è indipendente dal linguaggio e funziona sia per il codice Visual Basic che per il codice di C.

## <a name="initalizing-the-analyzer"></a>Inizializzazione dell'analizzatore
Scorrere un po' `DiagnosticAnalyzer` verso il `Initialize` basso nella classe per visualizzare il metodo. Il compilatore chiama questo metodo quando si attiva un analizzatore. Il metodo `AnalysisContext` accetta un oggetto che consente all'analizzatore di accedere alle informazioni sul contesto e di registrare i callback per gli eventi per i tipi di codice che si desidera analizzare.

```csharp
public override void Initialize(AnalysisContext context) {}
```

Aprire una nuova riga in questo metodo e digitare "contesto". per visualizzare un elenco di completamento Intellisense. È possibile vedere nell'elenco `Register…` di completamento ci sono molti metodi per gestire vari tipi di eventi. Ad esempio, il `RegisterCodeBlockAction`primo, , richiama il codice per un blocco, che in genere è il codice tra parentesi graffe. La registrazione per un blocco richiama anche il codice per l'inizializzatore di un campo, il valore assegnato a un attributo o il valore di un parametro facoltativo.

Come altro `RegisterCompilationStartAction`esempio, , richiama il codice all'inizio di una compilazione, il che è utile quando è necessario raccogliere lo stato in molte posizioni. È possibile creare una struttura di dati, ad esempio, per raccogliere tutti i simboli utilizzati e ogni volta che l'analizzatore viene richiamato per una sintassi o un simbolo, è possibile salvare informazioni su ogni posizione nella struttura di dati. Quando si viene richiamati a causa della fine della compilazione, è possibile analizzare tutte le `using` posizioni salvate, ad esempio, per segnalare i simboli utilizzati dal codice da ogni istruzione.

Utilizzando il visualizzatore di **sintassi**, si è appreso che si desidera essere chiamati quando il compilatore elabora un ObjectCreationExpression. Utilizzare questo codice per impostare il callback:You use this code to set up the callback:

```csharp

context.RegisterSyntaxNodeAction(c => AnalyzeObjectCreation(c),
                                 SyntaxKind.ObjectCreationExpression);
```

Si esegue la registrazione per un nodo di sintassi e un filtro solo per i nodi della sintassi di creazione di oggetti. Per convenzione, gli autori di analizzatori usano un'espressione lambda durante la registrazione delle azioni, che consente di mantenere gli analizzatori senza stato. È possibile utilizzare la funzionalità di Visual `AnalyzeObjectCreation` Studio **Genera dall'utilizzo** per creare il metodo. Questo genera il tipo corretto di parametro di contesto anche per voi.

## <a name="setting-properties-for-users-of-your-analyzer"></a>Impostazione delle proprietà per gli utenti dell'analizzatore
In modo che l'analizzatore venga visualizzato nell'interfaccia utente di Visual Studio in modo appropriato, cercare e modificare la seguente riga di codice per identificare l'analizzatore:

```csharp
internal const string Category = "Naming";
```

Cambiare `"Naming"` in `"API Guidance"`.

Individuare e aprire quindi il file Resources.resx nel progetto utilizzando **Esplora soluzioni**. È possibile inserire una descrizione per l'analizzatore, titolo, ecc. È possibile modificare il valore `“Don’t use ImmutableArray<T> constructor”` per tutti questi per ora. È possibile inserire argomenti di{0}formattazione delle stringhe nella stringa ( , {1}, e così via) e successivamente, quando si chiama `Diagnostic.Create()`, è possibile fornire una matrice params di argomenti da passare.

## <a name="analyzing-an-object-creation-expression"></a>Analisi di un'espressione di creazione di oggettiAnalyzing an Object Creation Expression
Il `AnalyzeObjectCreation` metodo accetta un tipo diverso di contesto fornito dal framework dell'analizzatore di codice. Il Initialize metodo `AnalysisContext` consente di registrare i callback di azione per impostare l'analizzatore. L'oggetto `SyntaxNodeAnalysisContext`, ad `CancellationToken` esempio, dispone di un che è possibile passare in giro. Se un utente inizia a digitare nell'editor, Roslyn annullerà gli analizzatori in esecuzione per salvare il lavoro e migliorare le prestazioni. Come altro esempio, questo contesto ha un Node proprietà che restituisce il nodo della sintassi di creazione dell'oggetto.

Ottenere il nodo, che è possibile presupporre è il tipo per il quale è stata filtrata l'azione del nodo di sintassi:

```csharp
var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
```

### <a name="launching-visual-studio-with-your-analyzer-the-first-time"></a>Avvio di Visual Studio con l'analizzatore la prima volta
Avviare Visual Studio compilando ed eseguendo l'analizzatore (premere **F5**). Poiché il progetto di avvio in **Esplora soluzioni** è il progetto VSIX, l'esecuzione del codice compila il codice e un progetto VSIX e quindi avvia Visual Studio con tale progetto VSIX installato. Quando si avvia Visual Studio in questo modo, viene avviato con un hive del Registro di sistema distinto in modo che l'utilizzo principale di Visual Studio non sarà influenzato dalle istanze di test durante la compilazione di analizzatori. La prima volta che si avvia in questo modo, Visual Studio esegue diverse inizializzazioni simili a quando è stato avviato Visual Studio dopo l'installazione.

 Creare un progetto console e quindi immettere il codice dell'array nel metodo Main delle applicazioni console:Create a console project and then enter the array code into your console applications Main method:

```csharp
var b1 = new ImmutableArray<int>();
Console.WriteLine("b1.Length = {0}", b1.Length);
var b2 = new ImmutableArray<int> { 1, 2, 3, 4, 5 };
Console.WriteLine("b2.Length = {0}", b2.Length);

```

Le righe di `ImmutableArray` codice con a zigzagna hanno scarabocchi perché è necessario `using` ottenere il pacchetto NuGet non modificabile e aggiungere un'istruzione al codice. Premere il pulsante destro del puntatore sul nodo del progetto in **Esplora soluzioni** e scegliere **Gestisci pacchetti NuGet in corso...**. Nel gestore NuGet, digitare "Immutable" nella casella di ricerca e scegliere l'elemento "System.Collections.Immutable" (non scegliere "Microsoft.Bcl.Immutable") nel riquadro sinistro e premere il pulsante Installa nel riquadro di destra. L'installazione del pacchetto aggiunge un riferimento ai riferimenti del progetto.

Nella sezione , è ancora `ImmutableArray`presente una sottolineaquanto rossa, quindi posizionare il punto di inserimento in tale identificatore e premere **CTRL.** (punto) per visualizzare il menu di correzione suggerito `using` e scegliere di aggiungere l'istruzione appropriata.

**Salva tutto e chiudi** la seconda istanza di Visual Studio per ora per mettere in uno stato pulito per continuare.

## <a name="finishing-the-analyzer-using-edit-and-continue"></a>Completamento dell'analizzatore tramite Modifica e continuazione
Nella prima istanza di Visual Studio, impostare `AnalyzeObjectCreation` un punto di interruzione all'inizio del metodo premendo **F9** con il punto di inserimento nella prima riga.

Avviare nuovamente l'analizzatore con **F5**e nella seconda istanza di Visual Studio riaprire l'applicazione console creata l'ultima volta.

Si torna alla prima istanza di Visual Studio in corrispondenza del punto di interruzione perché il compilatore Roslyn ha visto un'espressione di creazione oggetto e chiamato nell'analizzatore.

**Ottenere il nodo di creazione dell'oggetto.** Passare sulla riga che `objectCreation` imposta la variabile premendo **F10**e `“objectCreation.ToString()”`nella finestra di controllo **immediato** valutare l'espressione . Si nota che il nodo di `"new ImmutableArray<int>()"`sintassi a cui punta la variabile è il codice , proprio quello che si sta cercando.

**Ottenere ImmutableArray\<T>oggetto Type.** È necessario verificare se il tipo creato è ImmutableArray.You need to check if the type being created is ImmutableArray. In primo luogo, si ottiene l'oggetto che rappresenta questo tipo. Controllare i tipi utilizzando il modello semantico per assicurarsi di avere esattamente il tipo corretto e non confrontare la stringa da ToString(). Immettere la seguente riga di codice alla fine della funzione:

```csharp

var immutableArrayOfTType =
    context.SemanticModel
           .Compilation
           .GetTypeByMetadataName("System.Collections.Immutable.ImmutableArray`1");

```

I tipi generici vengono designati nei metadati con backquotes (') e il numero di parametri generici. Ecco perché non si vede "... ImmutableArray\<T>" nel nome dei metadati.

Il modello semantico ha molte cose utili su di esso che consentono di porre domande su simboli, flusso di dati, durata variabile, ecc. Roslyn separa i nodi di sintassi dal modello semantico per vari motivi di progettazione (prestazioni, modellazione di codice errato e così via). Si desidera che il modello di compilazione cerchi le informazioni contenute nei riferimenti per un confronto accurato.

È possibile trascinare il puntatore di esecuzione giallo sul lato sinistro della finestra dell'editor. Trascinarlo fino alla riga `objectCreation` che imposta la variabile e passare alla nuova riga di codice utilizzando **F10**. Se si posiziona il puntatore del mouse sulla variabile `immutableArrayOfType`, si nota che è stato trovato il tipo esatto nel modello semantico.

**Ottenere il tipo dell'espressione di creazione oggetto.** "Tipo" viene utilizzato in alcuni modi in questo articolo, ma questo significa che se si dispone di "nuova espressione Foo", è necessario ottenere un modello di Foo. È necessario ottenere il tipo dell'espressione di creazione dell'oggetto\<per verificare se si tratta del tipo di> ImmutableArray T. Utilizzare nuovamente il modello semantico per ottenere informazioni sui simboli per il simbolo di tipo (ImmutableArray) nell'espressione di creazione dell'oggetto. Immettere la seguente riga di codice alla fine della funzione:

```csharp
var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as INamedTypeSymbol;

```

Poiché l'analizzatore deve gestire codice incompleto o non corretto `using` nei buffer dell'editor (ad esempio, è presente un'istruzione mancante), è necessario verificare `symbolInfo` che sia `null`. È necessario ottenere un tipo denominato (INamedTypeSymbol) dall'oggetto informazioni sui simboli per completare l'analisi.

**Confrontare i tipi.** Poiché è disponibile un tipo generico aperto di T che stiamo cercando e il tipo nel codice è un tipo generico concreto, `immutableArrayOfTType`si esegue una query sulle informazioni sui simboli per ciò da cui viene costruito il tipo (un tipo generico aperto) e confrontare tale risultato con . Immettere quanto segue alla fine del metodo:

```csharp
if (symbolInfo != null &&
    symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
{}
```

**Segnalare la diagnostica.** Segnalare la diagnostica è abbastanza facile. Utilizzare la regola creata automaticamente nel modello di progetto, che viene definito prima di Initialize metodo. Poiché questa situazione nel codice è un errore, è possibile `DiagnosticSeverity.Warning` modificare la riga che `DiagnosticSeverity.Error` ha inizializzato Rule da sostituire (linea ondulata verde) con (linea ondulata rossa). Il resto della regola viene inizializzato dalle risorse modificate vicino all'inizio della procedura dettagliata. È inoltre necessario segnalare la posizione per la sottolineadettaglia, ovvero la posizione della specifica del tipo dell'espressione di creazione oggetto. Inserisci questo codice `if` nel blocco:

```csharp
context.ReportDiagnostic(Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
```

La funzione dovrebbe essere simile alla seguente (forse formattata in modo diverso):Your function should look like this (perhaps formatted differently):

```csharp
private void AnalyzeObjectCreation(SyntaxNodeAnalysisContext context)
{
    var objectCreation = (ObjectCreationExpressionSyntax)context.Node;
    var immutableArrayOfTType =
        context.SemanticModel
               .Compilation
               .GetTypeByMetadataName(
                   "System.Collections.Immutable.ImmutableArray`1");
    var symbolInfo = context.SemanticModel.GetSymbolInfo(objectCreation.Type) as
        INamedTypeSymbol;
    if (symbolInfo != null &&
        symbolInfo.ConstructedFrom.Equals(immutableArrayOfTType))
    {
        context.ReportDiagnostic(
            Diagnostic.Create(Rule, objectCreation.Type.GetLocation()));
    }
}

```

Rimuovere il punto di interruzione in modo da poter vedere l'analizzatore di lavoro (e interrompere il ritorno alla prima istanza di Visual Studio). Trascinare il puntatore di esecuzione all'inizio del metodo e premere **F5** per continuare l'esecuzione. Quando si torna alla seconda istanza di Visual Studio, il compilatore inizierà a esaminare nuovamente il codice e chiamerà nell'analizzatore. È possibile visualizzare uno scarabocchiato sotto `ImmutableType<int>`.

## <a name="adding-a-code-fix-for-the-code-issue"></a>Aggiunta di una "correzione del codice" per il problema del codice
Prima di iniziare, chiudere la seconda istanza di Visual Studio e interrompere il debug nella prima istanza di Visual Studio (dove si sta sviluppando l'analizzatore).

**Aggiungere una nuova classe.** Utilizzare il menu di scelta rapida (pulsante destro del mouse) nel nodo del progetto in Esplora soluzioni e scegliere di aggiungere un nuovo elemento. Aggiungere una `BuildCodeFixProvider`classe denominata . Questa classe deve `CodeFixProvider`derivare da , ed è necessario utilizzare **CTRL.** (punto) per richiamare la correzione `using` del codice che aggiunge l'istruzione corretta. Questa classe deve anche essere annotata con `ExportCodeFixProvider` attributo e `using` sarà necessario `LanguageNames` aggiungere un'istruzione per risolvere l'enumerazione. Si dovrebbe avere un file di classe con il codice seguente:You should have a class file with the following code in it:

```csharp
using Microsoft.CodeAnalysis;
using Microsoft.CodeAnalysis.CodeFixes;

namespace ImmutableArrayAnalyzer
{
    [ExportCodeFixProvider(LanguageNames.CSharp)]
    class BuildCodeFixProvider : CodeFixProvider
    {}

```

**Stub fuori membri derivati.** A questo punto, inserire il punto `CodeFixProvider` di inserimento dell'editor nell'identificatore e premere **CTRL.** (punto) per eseguire lo stub dell'implementazione per questa classe base astratta. Questo genera una proprietà e un metodo per voi.

**Implementare la proprietà.** Compilare `FixableDiagnosticIds` il corpo `get` della proprietà con il codice seguente:

```csharp
return ImmutableArray.Create(ImmutableArrayAnalyzerAnalyzer.DiagnosticId);
```

Roslyn riunisce diagnostica e correzioni abbinando questi identificatori, che sono solo stringhe. Il modello di progetto ha generato automaticamente un ID di diagnostica e l'utente è libero di modificarlo. Il codice nella proprietà restituisce semplicemente l'ID dalla classe analyzer.

**Il RegisterCodeFixAsync metodo accetta un contesto.** Il contesto è importante perché una correzione del codice può essere applicata a più diagnostica o potrebbe essere presente più di un problema in una riga di codice. Se si digita "contesto". nel corpo del metodo, l'elenco di completamento Intellisense vi mostrerà alcuni membri utili. C'è un membro CancellationToken che è possibile controllare per vedere se qualcosa vuole annullare la correzione. C'è un membro Document che ha un sacco di membri utili e consente di accedere agli oggetti del modello di progetto e soluzione. È presente un membro Span che è l'inizio e la fine del percorso del codice specificato quando è stata segnalata la diagnostica.

**Rendere il metodo asincrono.** La prima cosa da fare è correggere la `async` dichiarazione di metodo generato per essere un metodo. La correzione del codice per eseguire lo stubbing dell'implementazione di una classe astratta non include la `async` parola chiave anche se il metodo restituisce un `Task`oggetto .

**Ottenere la radice dell'albero della sintassi.** Per modificare il codice è necessario produrre un nuovo albero della sintassi con le modifiche apportate dalla correzione del codice. È necessario `Document` il dal `GetSyntaxRootAsync`contesto per chiamare . Si tratta di un metodo asincrono perché non esiste alcun lavoro per ottenere l'albero della sintassi, includendo eventualmente ottenere il file dal disco, analizzarlo e compilare il modello di codice Roslyn per esso. L'interfaccia utente di Visual Studio deve `async` essere reattiva durante questo periodo, che l'uso abilita. Sostituire la riga di codice nel metodo con quanto segue:

```csharp
var root = await context.Document
                        .GetSyntaxRootAsync(context.CancellationToken);
```

**Trovare il nodo con il problema.** Si passa nell'intervallo del contesto, ma il nodo trovato potrebbe non essere il codice che è necessario modificare. La diagnostica segnalata ha fornito solo l'intervallo per l'identificatore di tipo (a cui `new` apparteneva la scheda ondulata), ma è necessario sostituire l'intera espressione di creazione dell'oggetto, incluso il keywoard all'inizio e le parentesi alla fine. Aggiungere il codice riportato di seguito al metodo e utilizzare **CTRL .** per aggiungere `using` un'istruzione per `ObjectCreationExpressionSyntax`):

```csharp

var objectCreation = root.FindNode(context.Span)
                         .FirstAncestorOrSelf<ObjectCreationExpressionSyntax>();
```

 **Registrare la correzione del codice per l'interfaccia utente della lampadina.** Quando si registra la correzione del codice, Roslyn si collega automaticamente all'interfaccia utente della lampadina di Visual Studio.When you register your code fix, Roslyn plugs into the Visual Studio light bulb UI automatically. Gli utenti finali vedranno che possono utilizzare **CTRL.** (punto) quando l'analizzatore ondula un utilizzo non valido `ImmutableArray<T>` del costruttore. Poiché il provider di correzione del codice viene eseguito solo quando si verifica un problema, è possibile presupporre di disporre dell'espressione di creazione dell'oggetto che si stava cercando. Dal parametro context è possibile registrare la nuova correzione del `RegisterCodeFixAsync` codice aggiungendo il codice seguente alla fine del metodo:

```csharp

context.RegisterCodeFix(
            CodeAction.Create("Use ImmutableArray<T>.Empty",
                              c => ChangeToImmutableArrayEmpty(objectCreation,
                                                               context.Document,
                                                               c)),
            context.Diagnostics[0]);
```

È necessario inserire il punto di inserimento `CodeAction`dell'editor nell'identificatore , quindi utilizzare **CTRL .** (punto) per aggiungere `using` l'istruzione appropriata per questo tipo.

Posizionare quindi il punto di `ChangeToImmutableArrayEmpty` inserimento dell'editor nell'identificatore e utilizzare **CTRL .** per generare questo stub di metodo per voi.

Quest'ultimo frammento di codice aggiunto registra `CodeAction` la correzione del codice passando un e l'ID di diagnostica per il tipo di problema rilevato. In questo esempio è disponibile un solo ID di diagnostica per cui questo codice fornisce correzioni, pertanto è possibile passare semplicemente il primo elemento della matrice di ID di diagnostica. Quando si `CodeAction`crea , si passa il testo che l'interfaccia utente lampadina deve utilizzare come descrizione della correzione del codice. Si passa anche una funzione che accetta un CancellationToken e restituisce un nuovo Document.You also pass in a function that takes a CancellationToken and returns a new Document. Il nuovo documento ha un nuovo albero della `ImmutableArray.Empty`sintassi che include il codice patchato che chiama . Questo frammento di codice usa un'espressione lambda in modo che possa chiudere il nodo objectCreation e il documento del contesto.

**Costruire il nuovo albero della sintassi.** Nel `ChangeToImmutableArrayEmpty` metodo di cui è stato generato in `ImmutableArray<int>.Empty;`precedenza lo stub, immettere la riga di codice: . Se si visualizza nuovamente la finestra degli strumenti del visualizzatore di sintassi, è possibile visualizzare questa sintassi è un nodo SimpleMemberAccessExpression.If you view the Syntax Visualizer tool window again, you can see this syntax is a SimpleMemberAccessExpression node. Questo è ciò che questo metodo deve costruire e restituire in un nuovo documento.

La prima `ChangeToImmutableArrayEmpty` modifica a `async` `Task<Document>` consiste nell'aggiungere prima perché i generatori di codice non possono presupporre che il metodo deve essere asincrono.

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

È necessario inserire il punto di inserimento dell'editor nell'identificatore `SyntaxGenerator` e utilizzare CTRL **.** (punto) per aggiungere `using` l'istruzione appropriata per questo tipo.

Questo codice `SyntaxGenerator`usa , che è un tipo molto utile per la costruzione di nuovo codice. Dopo aver ottenuto un generatore per `ChangeToImmutableArrayEmpty` il `MemberAccessExpression`documento che presenta il problema di codice, chiama , passando il tipo che contiene il membro a cui si desidera accedere e passando il nome del membro come stringa.

Successivamente, il metodo recupera la radice del documento e, poiché ciò può comportare operazioni arbitrarie nel caso generale, il codice attende questa chiamata e passa il token di annullamento. I modelli di codice Roslyn non sono modificabili, ad esempio l'utilizzo di una stringa .NET; quando si aggiorna la stringa, si ottiene un nuovo oggetto stringa in cambio. Quando si `ReplaceNode`chiama , si ottiene un nuovo nodo radice. La maggior parte dell'albero della sintassi è condiviso `objectCreation` (perché non `memberAccess` è modificabile), ma il nodo viene sostituito con il nodo, nonché tutti i nodi padre fino alla radice dell'albero della sintassi.

## <a name="trying-your-code-fix"></a>Provare la correzione del codice
È ora possibile premere F5 per eseguire l'analizzatore in una seconda istanza di Visual Studio.You can now press **F5** to execute your analyzer in a second instance of Visual Studio. Aprire il progetto console utilizzato in precedenza. Ora dovresti vedere la lampadina apparire dove la `ImmutableArray<int>`tua nuova espressione di creazione oggetto è per . Se si preme **CTRL .** (punto), quindi vedrai la correzione del codice e vedrai un'anteprima della differenza di codice generata automaticamente nell'interfaccia utente della lampadina. Roslyn crea questo per te.

Suggerimento Pro: se si avvia la seconda istanza di Visual Studio e non viene visualizzata la lampadina con la correzione del codice, potrebbe essere necessario cancellare la cache dei componenti di Visual Studio. La cancellazione della cache forza Visual Studio a riesaminare i componenti, pertanto Visual Studio deve quindi prelevare il componente più recente. Arrestare innanzitutto la seconda istanza di Visual Studio. Quindi, in Esplora risorse, passare alla directory\\ dell'utente (c:, gli utenti<userid\>) e\\trovare AppData Locale Microsoft VisualStudio 14.0Roslyn . In questa directory eliminare la sottodirectory ComponentModelCache. Il "14" cambia la versione alla versione con Visual Studio.

## <a name="talk-video-and-finish-code-project"></a>Progetto Di seguito video di discussione e codice di finitura
Potete vedere questo esempio sviluppato e discusso ulteriormente in [questo discorso](https://channel9.msdn.com/events/Build/2015/3-725). Il discorso dimostra l'analizzatore di lavoro e ti guida attraverso la costruzione.

È possibile visualizzare tutto il codice finito [qui](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers). Le sottocartelle DoNotUseImmutableArrayCollectionInitializer e DoNotUseImmutableArrayCtor dispongono ciascuna di un file in linguaggio C, per la ricerca di problemi, e un file in linguaggio C, che implementa le correzioni del codice visualizzate nell'interfaccia utente della lampadina di Visual Studio. Si noti che il codice finito ha un po' più\<di astrazione per evitare di recuperare l'oggetto tipo ImmutableArray T> più e più volte. Utilizza azioni registrate annidate per salvare l'oggetto tipo in un contesto disponibile ogni volta che vengono eseguite le azioni secondarie (analizzare la creazione di oggetti e analizzare le inizializzazioni della raccolta).

## <a name="see-also"></a>Vedere anche
[\\-Build 2015 talk](https://channel9.msdn.com/events/Build/2015/3-725)
[Codice completato su GitHub](https://github.com/DustinCampbell/CoreFxAnalyzers/tree/master/Source/CoreFxAnalyzers) 
[Diversi esempi su GitHub, raggruppati in tre tipi di analizzatori](https://github.com/dotnet/roslyn/blob/master/docs/analyzers/Analyzer%20Samples.md) 
Altri documenti sul sito 
[DiSS GitHub](https://github.com/dotnet/roslyn/tree/master/docs/analyzers)[FxCop regole implementate con analizzatori Roslyn su GitHub](https://github.com/dotnet/roslyn/tree/master/src/Features/Core/Portable/Diagnostics/Analyzers)
