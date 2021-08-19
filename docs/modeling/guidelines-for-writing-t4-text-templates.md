---
title: Linee guida per la scrittura di modelli di testo T4
description: Informazioni sulle linee guida generali utili se si genera codice di programma o altre risorse dell'applicazione in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: b0cb319b488bf080b95ce2651ccf21bad3c33d6a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122157514"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Linee guida per la scrittura di modelli di testo T4

Queste linee guida generali possono essere utili se si genera codice di programma o altre risorse dell'applicazione in Visual Studio. Non sono regole fisse.

## <a name="guidelines-for-design-time-t4-templates"></a>Linee guida per Design-Time modelli T4

I modelli T4 in fase di progettazione sono modelli che generano codice nel progetto Visual Studio in fase di progettazione. Per altre informazioni, vedere [Generazione di codice in fase di progettazione tramite modelli di testo T4.](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

Generare aspetti variabili dell'applicazione.

La generazione del codice è particolarmente utile per gli aspetti dell'applicazione che potrebbero cambiare durante il progetto o cambieranno tra versioni diverse dell'applicazione. Separare questi aspetti variabili dagli aspetti più invarianti in modo da poter determinare più facilmente cosa deve essere generato. Ad esempio, se l'applicazione fornisce un sito Web, separare le funzioni standard di gestione delle pagine dalla logica che definisce i percorsi di navigazione da una pagina a un'altra.

Codificare gli aspetti della variabile in uno o più modelli di origine.

Un modello è un file o un database letto da ogni modello per ottenere valori specifici per le parti variabili del codice da generare. I modelli possono essere database, file XML di progettazione, diagrammi o linguaggi specifici del dominio. In genere, un modello viene usato per generare molti file in un Visual Studio progetto. Ogni file viene generato da un modello separato.

È possibile usare più di un modello in un progetto. Ad esempio, è possibile definire un modello per lo spostamento tra le pagine Web e un modello separato per il layout delle pagine.

Concentrare il modello sulle esigenze e sul vocabolario degli utenti, non sull'implementazione.

Ad esempio, in un'applicazione per siti Web si prevede che il modello faccia riferimento a pagine Web e collegamenti ipertestuali.

Idealmente, scegliere una forma di presentazione adatta al tipo di informazioni rappresentate dal modello. Ad esempio, un modello di percorsi di navigazione tramite un sito Web potrebbe essere un diagramma di caselle e frecce.

Testare il codice generato.

Usare test manuali o automatizzati per verificare che il codice risultante funzioni come richiesto dagli utenti. Evitare di generare test dallo stesso modello da cui viene generato il codice.

In alcuni casi, i test generali possono essere eseguiti direttamente sul modello. È ad esempio possibile scrivere un test che garantisca che ogni pagina del sito Web possa essere raggiunta tramite la navigazione da qualsiasi altra pagina.

Consenti codice personalizzato: generare classi parziali.

Consentire il codice scritto manualmente oltre al codice generato. È insolito che uno schema di generazione del codice sia in grado di includere tutte le possibili variazioni che potrebbero verificarsi. È pertanto consigliabile aggiungere o eseguire l'override di parte del codice generato. Quando il materiale generato si trova in un linguaggio .NET come C# o Visual Basic, due strategie sono particolarmente utili:

- Le classi generate devono essere parziali. In questo modo è possibile aggiungere contenuto al codice generato.

- Le classi devono essere generate in coppie, una che eredita dall'altra. La classe di base deve contenere tutti i metodi e le proprietà generati e la classe derivata deve contenere solo i costruttori. Ciò consente al codice scritto a mano di eseguire l'override di uno dei metodi generati.

In altri linguaggi generati, ad esempio XML, usare la direttiva per creare semplici combinazioni di contenuto scritto a mano `<#@include#>` e generato. Nei casi più complessi potrebbe essere necessario scrivere un passaggio di post-elaborazione che combina il file generato con qualsiasi file scritto manualmente.

Spostare materiale comune in file di inclusione o modelli di runtime.

Per evitare di ripetere blocchi di testo e codice simili in più modelli, usare la `<#@ include #>` direttiva . Per altre informazioni, vedere [Direttiva Include T4.](../modeling/t4-include-directive.md)

È anche possibile compilare modelli di testo in fase di esecuzione in un progetto separato e quindi chiamarli dal modello in fase di progettazione. A tale scopo, usare la `<#@ assembly #>` direttiva per accedere al progetto separato.

Prendere in considerazione lo spostamento di blocchi di codice di grandi dimensioni in un assembly separato.

Se sono presenti blocchi di codice di grandi dimensioni e blocchi di funzionalità di classe, potrebbe essere utile spostare parte di questo codice nei metodi compilati in un progetto separato. È possibile usare `<#@ assembly #>` la direttiva per accedere al codice nel modello. Per altre informazioni, vedere [Direttiva assembly T4](../modeling/t4-assembly-directive.md).

È possibile inserire i metodi in una classe astratta che il modello può ereditare. La classe astratta deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> . Per altre informazioni, vedere [Direttiva del modello T4.](../modeling/t4-template-directive.md)

Generare codice, non file di configurazione.

Un metodo per scrivere un'applicazione variabile è scrivere codice di programma generico che accetta un file di configurazione. Un'applicazione scritta in questo modo è molto flessibile e può essere riconfigurata quando cambiano i requisiti aziendali, senza ricompilare l'applicazione. Tuttavia, uno svantaggio di questo approccio è che l'applicazione avrà prestazioni inferiori rispetto a un'applicazione più specifica. Inoltre, il codice del programma sarà più difficile da leggere e gestire, in parte perché deve sempre gestire i tipi più generici.

Al contrario, un'applicazione le cui parti variabili vengono generate prima della compilazione può essere fortemente tipizzato. In questo modo è molto più semplice e affidabile scrivere codice scritto a mano e integrarlo con le parti generate del software.

Per ottenere il vantaggio completo della generazione del codice, provare a generare il codice del programma anziché i file di configurazione.

Usare una cartella Codice generato.

Inserire i modelli e i file generati in una cartella di progetto denominata **Codice** generato per chiarire che non si tratta di file che devono essere modificati direttamente. Se si crea codice personalizzato per eseguire l'override o aggiungerlo alle classi generate, inserire tali classi in una cartella denominata **Codice personalizzato**. La struttura di un progetto tipico è simile alla seguente:

```
MyProject
   Custom Code
      Class1.cs
      Class2.cs
   Generated Code
      Class1.tt
          Class1.cs
      Class2.tt
          Class2.cs
   AnotherClass.cs
```

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Linee guida per Run-Time modelli T4 (pre-elaborati)

Spostare materiale comune in modelli ereditati.

È possibile usare l'ereditarietà per condividere metodi e blocchi di testo tra modelli di testo T4. Per altre informazioni, vedere [Direttiva del modello T4.](../modeling/t4-template-directive.md)

È anche possibile usare file di inclusione con modelli di run-time.

Spostare grandi corpi di codice in una classe parziale.

Ogni modello di run-time genera una definizione di classe parziale con lo stesso nome del modello. È possibile scrivere un file di codice che contiene un'altra definizione parziale della stessa classe. È possibile aggiungere metodi, campi e costruttori alla classe in questo modo. Questi membri possono essere chiamati dai blocchi di codice nel modello.

Un vantaggio di questa operazione è che il codice è più facile da scrivere, perché IntelliSense è disponibile. È anche possibile ottenere una migliore separazione tra la presentazione e la logica sottostante.

Ad esempio, in **MyReportText.tt**:

`The total is: <#= ComputeTotal() #>`

In **MyReportText-Methods.cs**:

`private string ComputeTotal() { ... }`

Consenti codice personalizzato: specificare i punti di estensione.

Provare a generare metodi virtuali in \<#+ class feature blocks #> . In questo modo è possibile usare un singolo modello in molti contesti senza modifiche. Anziché modificare il modello, è possibile costruire una classe derivata che fornisce la logica aggiuntiva minima. La classe derivata può essere codice normale o può essere un modello di run-time.

Ad esempio, in MyStandardRunTimeTemplate.tt:

```
This page is copyright <#= CompanyName() #>.
<#+ protected virtual string CompanyName() { return ""; } #>
```

Nel codice di un'applicazione:

```
class FabrikamTemplate : MyStandardRunTimeTemplate
{
  protected override string CompanyName() { return "Fabrikam"; }
}
...
  string PageToDisplay = new FabrikamTemplate().TextTransform();
```

## <a name="guidelines-for-all-t4-templates"></a>Linee guida per tutti i modelli T4

Separare la raccolta dei dati dalla generazione di testo.

Provare a evitare di combinare i blocchi di calcolo e di testo. In ogni modello di testo usare il primo \<# code block #> per impostare le variabili ed eseguire calcoli complessi. Dal primo blocco di testo fino alla fine del modello o del primo , evitare espressioni lunghe ed evitare cicli e condizionali a meno che non \<#+ class feature block #> contengano blocchi di testo. Questa procedura semplifica la lettura e la manutenzione del modello.

Non usare per `.tt` i file di inclusione.

Usare un'estensione di file diversa, ad esempio `.ttinclude` per i file di inclusione. Usare solo per i file che si desidera elaborare come modelli di testo in fase di esecuzione o `.tt` in fase di progettazione. In alcuni casi, Visual Studio riconosce i `.tt` file e imposta automaticamente le relative proprietà per l'elaborazione.

Avviare ogni modello come prototipo fisso.

Scrivere un esempio del codice o del testo da generare e assicurarsi che sia corretto. Modificare quindi l'estensione in .tt e inserire in modo incrementale il codice che modifica il contenuto leggendo il modello.

Prendere in considerazione l'uso di modelli tipi di dati.

Anche se è possibile creare uno schema XML o di database per i modelli, può essere utile creare un linguaggio specifico di dominio (DSL). Un DSL ha il vantaggio di generare una classe per rappresentare ogni nodo nello schema e le proprietà per rappresentare gli attributi. Ciò significa che è possibile programmare in termini di modello aziendale. Esempio:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

È consigliabile usare i diagrammi per i modelli.

Molti modelli vengono presentati e gestiti in modo più efficace semplicemente come tabelle di testo, soprattutto se sono molto grandi.

Tuttavia, per alcuni tipi di requisiti aziendali, è importante chiarire set complessi di relazioni e flussi di lavoro e i diagrammi sono il supporto più adatto. Un vantaggio di un diagramma è che è facile discutere con utenti e altri stakeholder. Generando codice da un modello a livello di requisiti aziendali, è possibile rendere il codice più flessibile quando i requisiti cambiano.

È anche possibile progettare un tipo di diagramma personalizzato come linguaggio specifico di dominio (DSL). Il codice può essere generato sia da UML che da DSL. Per altre informazioni, vedere [Analisi e modellazione dell'architettura.](../modeling/analyze-and-model-your-architecture.md)

## <a name="see-also"></a>Vedi anche

- [Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
