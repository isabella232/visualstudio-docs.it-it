---
title: Linee guida per la scrittura di modelli di testo T4 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 04dd3fc4-10e8-488a-bdea-4d615f50f063
caps.latest.revision: 11
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d1e15a8c00a0614d020defd2df7b06665289a8b2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666060"
---
# <a name="guidelines-for-writing-t4-text-templates"></a>Linee guida per la scrittura di modelli di testo T4
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Queste linee guida generali potrebbero essere utili se si genera codice programma o altre risorse dell'applicazione in [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] . Non sono regole fisse.

## <a name="guidelines-for-design-time-t4-templates"></a>Linee guida per i modelli T4 della fase di progettazione
 I modelli T4 della fase di progettazione sono modelli che generano codice nel progetto in fase [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] di progettazione. Per altre informazioni, vedere [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md).

 Genera aspetti variabili dell'applicazione.
La generazione di codice è particolarmente utile per gli aspetti dell'applicazione che potrebbero cambiare durante il progetto o cambierà tra versioni diverse dell'applicazione. Separare questi aspetti variabili dagli aspetti più invarianti, in modo da poter determinare più facilmente quali elementi devono essere generati. Se, ad esempio, l'applicazione fornisce un sito Web, separare le funzioni della pagina standard dalla logica che definisce i percorsi di navigazione da una pagina all'altra.

 Codificare gli aspetti variabili in uno o più modelli di origine.
Un modello è un file o un database letto da ogni modello per ottenere valori specifici per le parti variabili del codice da generare. I modelli possono essere database, file XML di progettazione, diagrammi o linguaggi specifici del dominio. In genere, un modello viene utilizzato per generare molti file in un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] progetto. Ogni file viene generato da un modello separato.

 È possibile utilizzare più di un modello in un progetto. Ad esempio, è possibile definire un modello per lo spostamento tra pagine Web e un modello separato per il layout delle pagine.

 Concentrare il modello in base alle esigenze e al vocabolario degli utenti, non all'implementazione.
In un'applicazione del sito Web, ad esempio, si prevede che il modello faccia riferimento a pagine Web e collegamenti ipertestuali.

 Idealmente, scegliere una forma di presentazione adatta al tipo di informazioni rappresentate dal modello. Un modello di percorsi di navigazione in un sito Web, ad esempio, potrebbe essere un diagramma di caselle e frecce.

 Testare il codice generato.
Usare i test manuali o automatizzati per verificare che il codice risultante funzioni come richiesto dagli utenti. Evitare di generare test dallo stesso modello da cui viene generato il codice.

 In alcuni casi, i test generali possono essere eseguiti direttamente sul modello. Ad esempio, è possibile scrivere un test che garantisce che ogni pagina nel sito Web possa essere raggiunta tramite navigazione da qualsiasi altro.

 Consenti codice personalizzato: genera classi parziali.
Consentire il codice scritto manualmente oltre al codice generato. È insolito che uno schema di generazione del codice sia in grado di tenere conto di tutte le possibili varianti che possono verificarsi. Pertanto, è prevedibile aggiungere o eseguire l'override di parte del codice generato. Se il materiale generato si trova in un linguaggio .NET, ad esempio [!INCLUDE[csprcs](../includes/csprcs-md.md)] o [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] , due strategie sono particolarmente utili:

- Le classi generate devono essere parziali. In questo modo è possibile aggiungere contenuto al codice generato.

- Le classi devono essere generate in coppie, una che eredita dall'altra. La classe base deve contenere tutti i metodi e le proprietà generati e la classe derivata deve contenere solo i costruttori. Ciò consente al codice scritto manualmente di eseguire l'override dei metodi generati.

  In altre lingue generate, ad esempio XML, usare la `<#@include#>` direttiva per creare semplici combinazioni di contenuto scritto manualmente e generato. In casi più complessi, potrebbe essere necessario scrivere un passaggio di post-elaborazione che combina il file generato con tutti i file scritti manualmente.

  Spostare il materiale comune in file di inclusione o modelli di runtime per evitare la ripetizione di blocchi di testo e codice simili in più modelli, utilizzare la `<#@ include #>` direttiva. Per altre informazioni, vedere [direttiva include T4](../modeling/t4-include-directive.md).

  È anche possibile compilare modelli di testo in fase di esecuzione in un progetto separato e quindi chiamarli dal modello della fase di progettazione. A tale scopo, utilizzare la `<#@ assembly #>` direttiva per accedere al progetto separato.

  Si consiglia di trasferire blocchi di codice di grandi dimensioni in un assembly separato.
  Se si dispone di blocchi di codice e di funzionalità di classe di grandi dimensioni, potrebbe essere utile spostare parte del codice in metodi compilati in un progetto separato. È possibile utilizzare la `<#@ assembly #>` direttiva per accedere al codice nel modello. Per altre informazioni, vedere [direttiva dell'assembly T4](../modeling/t4-assembly-directive.md).

  È possibile inserire i metodi in una classe astratta che il modello può ereditare. La classe astratta deve ereditare da <xref:Microsoft.VisualStudio.TextTemplating.TextTransformation?displayProperty=fullName> . Per altre informazioni, vedere [direttiva template T4](../modeling/t4-template-directive.md).

  Genera codice, non file di configurazione. un metodo di scrittura di un'applicazione variabile consiste nel scrivere codice programma generico che accetta un file di configurazione. Un'applicazione scritta in questo modo è molto flessibile e può essere riconfigurata quando cambiano i requisiti aziendali, senza ricompilare l'applicazione. Tuttavia, uno svantaggio di questo approccio è che l'applicazione verrà eseguita in modo meno efficace rispetto a un'applicazione più specifica. Inoltre, il codice programma sarà più difficile da leggere e gestire, in parte perché è sempre necessario gestire i tipi più generici.

  Al contrario, un'applicazione le cui parti variabili vengono generate prima che la compilazione possa essere fortemente tipizzata. In questo modo è molto più semplice e affidabile scrivere codice scritto manualmente e integrarlo con le parti del software generate.

  Per ottenere il massimo vantaggio dalla generazione del codice, provare a generare il codice programma invece dei file di configurazione.

  Usare una cartella di codice generata per inserire i modelli e i file generati in una cartella di progetto denominata **codice generato**, per chiarire che non si tratta di file che devono essere modificati direttamente. Se si crea codice personalizzato per eseguire l'override o aggiungere le classi generate, inserire le classi in una cartella denominata **codice personalizzato**. La struttura di un progetto tipico ha un aspetto simile al seguente:

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

## <a name="guidelines-for-run-time-preprocessed-t4-templates"></a>Linee guida per i modelli T4 in fase di esecuzione (pre-elaborata)
 Spostare il materiale comune in modelli ereditati è possibile usare l'ereditarietà per condividere i metodi e i blocchi di testo tra i modelli di testo T4. Per altre informazioni, vedere [direttiva template T4](../modeling/t4-template-directive.md).

 È anche possibile usare i file di inclusione con modelli di run-time.

 Spostare corpi di grandi dimensioni di codice in una classe parziale.
Ogni modello della fase di esecuzione genera una definizione di classe parziale con lo stesso nome del modello. È possibile scrivere un file di codice contenente un'altra definizione parziale della stessa classe. In questo modo è possibile aggiungere metodi, campi e costruttori alla classe. Questi membri possono essere chiamati dai blocchi di codice nel modello.

 Un vantaggio di questa operazione è che il codice è più facile da scrivere perché IntelliSense è disponibile. Inoltre, è possibile ottenere una migliore separazione tra la presentazione e la logica sottostante.

 Ad esempio, in **MyReportText.TT**:

 `The total is: <#= ComputeTotal() #>`

 In **MyReportText-methods.cs**:

 `private string ComputeTotal() { ... }`

 Consenti codice personalizzato: fornire punti di estensione provare a generare metodi virtuali in \<#+ class feature blocks #> . In questo modo, è possibile usare un singolo modello in molti contesti senza alcuna modifica. Anziché modificare il modello, è possibile costruire una classe derivata che fornisca la logica aggiuntiva minima. La classe derivata può essere di codice normale oppure può essere un modello in fase di esecuzione.

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
 Raccolta dati separata dalla generazione del testo provare a evitare di combinare i blocchi di calcolo e di testo. In ogni modello di testo usare il primo \<# code block #> per impostare le variabili ed eseguire calcoli complessi. Dal primo blocco di testo fino alla fine del modello o della prima \<#+ class feature block #> , evitare espressioni lunghe ed evitare cicli e condizionali a meno che non contengano blocchi di testo. Questa procedura rende il modello più semplice da leggere e gestire.

 Non utilizzare `.tt` per i file di inclusione utilizzare un'estensione di file diversa, ad esempio `.ttinclude` per i file di inclusione. Utilizzare `.tt` solo per i file che si desidera elaborare come modelli di testo in fase di esecuzione o di progettazione. In alcuni casi, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] riconosce `.tt` i file e imposta automaticamente le relative proprietà per l'elaborazione.

 Avviare ogni modello come prototipo fisso.
Scrivere un esempio del codice o del testo che si desidera generare e verificare che sia corretto. Modificare quindi l'estensione in. TT e inserire in modo incrementale il codice che modifica il contenuto leggendo il modello.

 Provare a usare i modelli tipizzati.
Sebbene sia possibile creare uno schema di database o XML per i modelli, può essere utile creare un linguaggio specifico di dominio (DSL). Un linguaggio DSL presenta il vantaggio di generare una classe per rappresentare ogni nodo nello schema e le proprietà per rappresentare gli attributi. Ciò significa che è possibile programmare in termini di modello di business. Ad esempio:

```
Team Members:
<# foreach (Person p in team.Members)
 { #>
    <#= p.Name #>
<# } #>
```

 Si consiglia di utilizzare diagrammi per i modelli.
Molti modelli vengono presentati e gestiti in modo più efficace semplicemente come tabelle di testo, soprattutto se sono molto grandi.

 Tuttavia, per alcuni tipi di requisiti aziendali, è importante chiarire set complessi di relazioni e flussi di lavoro e i diagrammi rappresentano il supporto più adatto. Il vantaggio di un diagramma è che è facile discutere con gli utenti e le altre parti interessate. La generazione di codice da un modello a livello di requisiti aziendali consente di rendere il codice più flessibile quando cambiano i requisiti.

 I diagrammi classi e attività UML possono essere spesso adattati per questi scopi. È anche possibile progettare un tipo di diagramma personalizzato come linguaggio specifico di dominio (DSL). Il codice può essere generato sia da UML che da DSLs. Per altre informazioni, vedere [analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md) e [analisi e modellazione dell'architettura](../modeling/analyze-and-model-your-architecture.md).

## <a name="see-also"></a>Vedere anche
 [Generazione di codice in fase di progettazione tramite modelli di testo T4 generazione di](../modeling/design-time-code-generation-by-using-t4-text-templates.md) [testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md)
