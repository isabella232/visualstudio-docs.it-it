---
title: Linee guida per la scrittura di modelli di testo T4
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 410ab74e672d29673674131b30e2412581b9b399
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55954205"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Linee guida per la scrittura di modelli di testo T4
Queste linee guida generali potrebbero essere utile se si sta generando codice programma o altre risorse dell'applicazione in Visual Studio. Le regole non sono corretti.

## <a name="guidelines-for-design-time-t4-templates"></a>Linee guida per i modelli T4 in fase di progettazione
 Modelli T4 in fase di progettazione sono modelli che generano codice nel progetto di Visual Studio in fase di progettazione. Per altre informazioni, vedere [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Generare gli aspetti variabili dell'applicazione.
Generazione di codice è particolarmente utile per gli aspetti dell'applicazione che potrebbero cambiare nel corso del progetto o verrà modificato tra versioni diverse dell'applicazione. Separare questi aspetti variabili dagli aspetti più invarianti in modo che sia possibile determinare più facilmente ciò che può essere generato. Ad esempio, se l'applicazione fornisce un sito Web, separare il servizio funzioni dalla logica che definisce i percorsi di navigazione da una pagina a un'altra pagina standard.

 Codificare gli aspetti variabili in uno o più modelli di origine.
Un modello è un file o database che legge ogni modello per ottenere valori specifici per parti variabili del codice che deve essere generato. I modelli possono essere database, file XML di propria progettazione, diagrammi o domain-specific Language. In genere, un modello consente di generare molti file in un progetto di Visual Studio. Ogni file viene generato da un modello distinto.

 È possibile usare più di un modello in un progetto. Ad esempio, si potrebbe definire un modello per la navigazione tra le pagine web e un modello distinto per il layout delle pagine.

 Concentrare il modello di fondo e vocabolario esigenze degli utenti, non l'implementazione.
In un'applicazione sito Web, ad esempio, si aspetta il modello per fare riferimento a pagine web e collegamenti ipertestuali.

 In teoria, scegliere un formato di presentazione che adatta il tipo di informazioni che rappresenta il modello. Ad esempio, un modello di percorsi di navigazione tramite un sito Web potrebbe essere un diagramma di finestre e le frecce.

 Testare il codice generato.
Utilizzare i test manuali o automatizzati per verificare che il codice risultante funziona come gli utenti richiedono. Evitare di generare test dallo stesso modello da cui viene generato il codice.

 In alcuni casi, i test generali possono essere eseguiti direttamente nel modello. Ad esempio, è possibile scrivere un test che assicura che ogni pagina del sito Web può essere raggiunta dalla navigazione da un altro.

 Attendere un codice personalizzato: generare le classi parziali.
Attendere un codice scritto a mano inoltre al codice generato. È insolito per uno schema di generazione di codice per essere in grado di tenere conto per tutte le possibili varianti che potrebbero verificarsi. Pertanto, si deve prevedere di aggiungere o modificare parte del codice generato. In cui il materiale generato è in un linguaggio .NET, ad esempio [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], due strategie sono particolarmente utili:

- Le classi generate dovrebbero essere parziali. In questo modo è possibile aggiungere contenuto al codice generato.

- Le classi devono essere generate in coppie, uno che eredita da un altro. La classe di base deve contenere tutte le proprietà e metodi generati e la classe derivata deve contenere solo i costruttori. In questo modo il codice scritto a mano a eseguire l'override dei metodi generati.

  In altri linguaggi generati, ad esempio XML, usare il `<#@include#>` direttiva per creare semplici combinazioni di contenuto generata e scritto a mano. Nei casi più complessi, potrebbe essere necessario scrivere un passaggio di post-elaborazione che combina il file generato con tutti i file scritti a mano.

  Materiale comune spostarvi i file di inclusione o i modelli in fase di esecuzione.
  Per evitare la ripetizione simile blocchi di testo e il codice in più modelli, usare il `<#@ include #>` direttiva. Per altre informazioni, vedere [direttiva Include T4](../modeling/t4-include-directive.md).

  È possibile anche creare modelli di testo in fase di esecuzione in un progetto separato e possono essere chiamati dal modello in fase di progettazione. A questo scopo, usare il `<#@ assembly #>` direttiva per accedere al progetto separato. Per esempi, vedere ["ereditarietà nel testo" modelli nel Blog di Gareth Jones](http://go.microsoft.com/fwlink/?LinkId=208373).

  Si consiglia di spostare grandi blocchi di codice in un assembly separato.
  Se sono presenti blocchi della funzionalità di classe e i blocchi di codice di grandi dimensioni, potrebbe essere utile spostare alcuni questo codice in metodi che si esegue la compilazione in un progetto separato. È possibile usare il `<#@ assembly #>` direttiva per accedere al codice nel modello. Per altre informazioni, vedere [direttiva Assembly T4](../modeling/t4-assembly-directive.md).

  È possibile inserire i metodi in una classe astratta che può ereditare il modello. La classe astratta deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName>. Per altre informazioni, vedere [direttiva Template T4](../modeling/t4-template-directive.md).

  Generare il codice, non i file di configurazione.
  Un metodo per la scrittura di un'applicazione di variabili consiste nello scrivere codice programma generico che accetta un file di configurazione. Un'applicazione scritta in questo modo è molto flessibile e può essere riconfigurata quando cambiano i requisiti aziendali, senza ricompilare l'applicazione. Tuttavia, uno svantaggio di questo approccio è che l'applicazione sarà ottimali rispetto a un'applicazione più specifica. Inoltre, il codice programma sarà più difficile da leggere e gestire, in parte perché deve sempre fare i conti con i tipi più generici.

  Al contrario, un'applicazione cui parti variabili vengono generati prima della compilazione può essere fortemente tipizzata. Questo rende molto più semplice e più affidabile per scrivere il codice scritto a mano e integrarla con generato parti del software.

  Per ottenere i massimi vantaggi della generazione del codice, provare a generare codice programma anziché i file di configurazione.

  Usare una cartella del codice generato.
  Inserire i modelli e i file generati in una cartella di progetto denominata **il codice generato**, per renderla cancellare che questi non sono file che devono essere modificati direttamente. Se si crea codice personalizzato per eseguire l'override o aggiungere le classi generate, inserire tali classi in una cartella denominata **codice personalizzato**. La struttura di un progetto tipico è simile alla seguente:

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Linee guida per i modelli T4 (pre-elaborato) in fase di esecuzione
 Spostare il materiale comune in modelli ereditati.
È possibile utilizzare l'ereditarietà per condividere i metodi e i blocchi di testo tra i modelli di testo T4. Per altre informazioni, vedere [direttiva Template T4](../modeling/t4-template-directive.md).

 È anche possibile usare file di inclusione che dispongono di modelli in fase di esecuzione.

 Spostare grandi quantità di codice in una classe parziale.
Ogni modello di runtime genera una definizione di classe parziale con lo stesso nome del modello. È possibile scrivere un file di codice che contiene un'altra definizione parziale della stessa classe. È possibile aggiungere i metodi, campi e i costruttori per la classe in questo modo. Questi membri possono essere chiamati dai blocchi di codice nel modello.

 Un vantaggio di questa operazione è che il codice è più facile da scrivere, perché IntelliSense è disponibile. Inoltre, è possibile ottenere una migliore separazione tra presentazione e la logica sottostante.

 Ad esempio, nella **MyReportText.tt**:

 `The total is: <#= ComputeTotal() #>`

 Nelle **MyReportText Methods.cs**:

 `private string ComputeTotal() { ... }`

 Attendere un codice personalizzato: forniscono punti di estensione.
Si consiglia di generare i metodi virtuali in \<funzionalità della classe & + Blocca & >. In questo modo un singolo modello da utilizzare in molti contesti senza alcuna modifica. Anziché modificare il modello, è possibile costruire una classe derivata che fornisce la logica aggiuntiva minima. La classe derivata può essere codice normale, o può essere un modello in fase di esecuzione.

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
Provare a evitare di combinare calcolo e i blocchi di testo. In ogni modello di testo, usare il primo \<codice & blocco & > per impostare le variabili ed eseguire calcoli complessi. Dal primo blocco di testo fino alla fine del modello o il primo \<funzionalità della classe & + block & >, evitare di espressioni lunghe ed evitare i cicli e istruzioni condizionali a meno che non contengono blocchi di testo. Questa pratica rende più facile da leggere e gestire il modello.

 Non usare `.tt` i file di inclusione.
Usare un'estensione nome file diverso, ad esempio `.ttinclude` i file di inclusione. Usare `.tt` solo per i file che si desidera essere elaborati come fase di esecuzione o in fase di progettazione modelli di testo. In alcuni casi, Visual Studio riconosce `.tt` i file e imposta automaticamente le relative proprietà per l'elaborazione.

 Ogni modello di avvio come prototipo fissato.
Scrivere un esempio di codice o del testo che si vuole generare e verificare che sia corretto. Quindi passare l'estensione con estensione tt e inserire in modo incrementale il codice che modifica il contenuto, vedere il modello.

 È consigliabile usare modelli tipizzati.
Sebbene sia possibile creare uno schema XML o un database per i modelli, potrebbe essere utile creare un linguaggio specifico di dominio (DSL). Un linguaggio DSL ha il vantaggio che genera una classe per rappresentare ogni nodo nello schema e le proprietà per rappresentare gli attributi. Ciò significa che è possibile programmare in termini di modello aziendale. Ad esempio:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 È consigliabile usare i diagrammi per i modelli.
Molti modelli in modo più efficace sono presentati e gestiti semplicemente come tabelle di testo, in particolare se sono molto grandi.

 Tuttavia, per alcuni tipi di requisiti aziendali, è importante chiarire set complessi di relazioni e i flussi di lavoro e i diagrammi sono il supporto più adatto. Un vantaggio di un diagramma è che è facile parlare con gli utenti e altre parti interessate. Generazione di codice da un modello a livello di requisiti aziendali, rendere il codice più flessibile quando cambiano i requisiti.

 È anche possibile progettare un nuovo tipo di diagramma come un linguaggio specifico di dominio (DSL). Codice può essere generato da UML e DSL. Per altre informazioni, vedere [analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Vedere anche

- [Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
- [Generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
