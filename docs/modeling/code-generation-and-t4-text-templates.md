---
title: Generazione di codice e modelli di testo T4
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.ToolsOptionsPages.TextTemplating.TextTemplating
helpviewer_keywords:
- generating text
- .tt files
- code generation
- text templates
- generating code
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 125ddff4bded1a58a7e68e6c8058d24ff16b2be1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62423094"
---
# <a name="code-generation-and-t4-text-templates"></a>Generazione di codice e modelli di testo T4

In Visual Studio, un *modello di testo T4* è una combinazione di blocchi di testo e logica di controllo che può generare un file di testo. La logica di controllo è scritta come frammenti di codice programma in [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] o [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]. In Visual Studio 2015 Update 2 e versioni successive è possibile usare le funzionalità di C# versione 6.0 nelle direttive dei modelli T4. Il file generato può essere testo di qualsiasi tipo, ad esempio una pagina web, un file di risorse o codice di origine di programma in qualsiasi linguaggio.

Esistono due tipi di modelli di testo T4: eseguono ora e fase di progettazione.

## <a name="run-time-t4-text-templates"></a>Modelli di testo T4 di fase di esecuzione

Noto anche come modelli 'pre-elaborati', modelli fase di esecuzione vengono eseguiti nell'applicazione per produrre stringhe di testo, in genere come parte dell'output. È ad esempio possibile creare un modello per definire una pagina HTML:

```
<html><body>
 The date and time now is: <#= DateTime.Now #>
</body></html>
```

Si noti che il modello è simile all'output generato. La somiglianza del modello all'output risultante consente di evitare errori quando lo si vuole modificare.

Inoltre, il modello contiene frammenti di codice programma. È possibile usare questi frammenti per ripetere sezioni di testo, creare sezioni condizionali e visualizzare dati dell'applicazione.

Per generare l'output, l'applicazione chiama una funzione che viene generata dal modello. Ad esempio:

```csharp
string webResponseText = new MyTemplate().TransformText();
```

L'applicazione può essere eseguita in un computer che non è installato Visual Studio.

Per creare un modello in fase di esecuzione, aggiungere un file di **modello di testo pre-elaborato** al progetto. In alternativa, è possibile aggiungere un file di testo normale e impostare la relativa proprietà **Strumento personalizzato** su **TextTemplatingFilePreprocessor**.

Per altre informazioni, vedere [generazione di testo in fase di esecuzione con modelli di testo T4](../modeling/run-time-text-generation-with-t4-text-templates.md). Per altre informazioni sulla sintassi dei modelli, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).

## <a name="design-time-t4-text-templates"></a>Modelli testo T4 in fase di progettazione

Modelli in fase di progettazione definiscono parte del codice sorgente e altre risorse dell'applicazione. In genere si usano diversi modelli che leggono i dati in un database o un singolo file di input e generare alcune delle *cs*, *vb*, o altri file di origine. Ogni modello genera un file. Vengono eseguiti all'interno di Visual Studio o MSBuild.

I dati di input potrebbero ad esempio essere un file XML di dati di configurazione. Quando si modifica il file XML durante lo sviluppo, i modelli di testo rigenerare parte del codice dell'applicazione. Uno dei modelli potrebbe assomigliare all'esempio seguente:

```
<#@ output extension=".cs" #>
<#@ assembly name="System.Xml" #>
<#
 System.Xml.XmlDocument configurationData = ...; // Read a data file here.
#>
namespace Fabrikam.<#= configurationData.SelectSingleNode("jobName").Value #>
{
  ... // More code here.
}
```

A seconda dei valori nel file XML generato *cs* file sarà simile al seguente:

```
namespace Fabrikam.FirstJob
{
  ... // More code here.
}
```

Facendo un altro esempio, l'input potrebbe essere un diagramma di flusso di lavoro in un'attività aziendale. Quando gli utenti modificano il flusso di lavoro aziendale o quando si inizia a lavorare con nuovi utenti che dispongono di un flusso di lavoro diverso, è facile rigenerare il codice per adattarlo al nuovo modello.

I modelli in fase di progettazione rendono più veloce e affidabile la modifica della configurazione quando cambiano i requisiti. In genere l'input è definito in termini di requisiti aziendali, come illustrato nell'esempio del flusso di lavoro. Questo rende più semplice discutere le modifiche con gli utenti. I modelli in fase di progettazione sono pertanto un utile strumento in un processo di sviluppo agile.

Per creare un modello in fase di progettazione, aggiungere un file di **modello di testo** al progetto. In alternativa, è possibile aggiungere un file di testo normale e impostare la relativa proprietà **Strumento personalizzato** su **TextTemplatingFileGenerator**.

Per altre informazioni, vedere [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Per altre informazioni sulla sintassi dei modelli, vedere [scrittura di un modello di testo T4](../modeling/writing-a-t4-text-template.md).

> [!NOTE]
> Il termine *modello* talvolta viene usato per descrivere i dati letti da uno o più modelli. Il modello può avere qualsiasi formato, in qualsiasi tipo di file o database. Non deve essere un modello UML o un modello di linguaggio specifico di dominio. "Modello" indica semplicemente che i dati possono essere definiti in termini di concetti aziendali, invece di essere simili al codice.

La funzionalità di trasformazione del modello di testo è denominata *T4*.

## <a name="see-also"></a>Vedere anche

- [Generare codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)
