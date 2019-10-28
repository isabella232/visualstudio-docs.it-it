---
title: Scrittura di un modello di testo T4
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- text templates, syntax
- text templates, guide
- text templates, functions that generate text
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: df653dbd449429b6995c987328a401866751fd5e
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981255"
---
# <a name="writing-a-t4-text-template"></a>Scrittura di un modello di testo T4
Un modello di testo contiene il testo che verrà generato dal modello stesso. Ad esempio, un modello che crea una pagina Web conterrà "\<html >..." e tutte le altre parti standard di una pagina HTML. I *blocchi di controllo*inseriti nel modello sono frammenti del codice del programma. forniscono i valori variabili e consentono ad alcune parti del testo di essere ripetute e usate in modo condizionale.

 Questa struttura facilita lo sviluppo di un modello, perché consente di partire da un prototipo del file generato inserendo in modo incrementale i blocchi di controllo che variano il risultato.

 I modelli di testo sono costituiti dalle parti seguenti:

- **Direttive** : elementi che controllano la modalità di elaborazione del modello.

- **Blocchi di testo** : contenuto copiato direttamente nell'output.

- **Blocchi di controllo** : codice programma che inserisce valori variabili nel testo e controlla parti condizionali o ripetute del testo.

Per provare gli esempi in questo argomento, copiarli in un file modello come descritto in [generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md). Dopo aver modificato il file di modello, salvarlo e quindi ispezionare il file output **. txt** .

## <a name="directives"></a>Direttive
 Le direttive del modello di testo forniscono al motore del modello di testo le istruzioni generali che stabiliscono come generare il codice di trasformazione e il file di output.

 Ad esempio, la direttiva seguente specifica che il file di output deve avere l'estensione .txt:

```
<#@ output extension=".txt" #>
```

 Per ulteriori informazioni sulle direttive, vedere [direttive di modello di testo T4](../modeling/t4-text-template-directives.md).

## <a name="text-blocks"></a>Blocchi di testo
 Un blocco di testo inserisce del testo direttamente nel file di output. Non esiste una formattazione speciale per i blocchi di testo. Ad esempio, il modello di testo seguente produrrà un file di testo contenente la parola "Hello":

```
<#@ output extension=".txt" #>
Hello
```

## <a name="control-blocks"></a>Blocchi di controllo
 I blocchi di controllo sono sezioni del codice programma usate per trasformare i modelli. Il linguaggio predefinito è C#, ma è possibile usare [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] scrivendo la seguente direttiva all'inizio del file:

```
<#@ template language="VB" #>
```

 Il linguaggio nel quale si scrive il codice nei blocchi di controllo non è correlato al linguaggio del testo generato.

### <a name="standard-control-blocks"></a>Blocchi di controllo standard
 Un blocco di controllo standard è una sezione del codice programma che genera una parte del file di output.

 In un file di modello è possibile usare insieme blocchi di testo e blocchi di controllo standard ma non è possibile inserire un blocco di controllo all'interno di un altro. Ciascun blocco di controllo standard è delimitato dai simboli `<# ... #>`.

 Ad esempio, il blocco di controllo e il blocco di testo seguenti inseriscono nel file di output la riga "0, 1, 2, 3, 4 Hello!":

```
<#
    for(int i = 0; i < 4; i++)
    {
        Write(i + ", ");
    }
    Write("4");
#> Hello!
```

 Anziché utilizzare le istruzioni `Write()` esplicite, è possibile alternare testo e codice. L'esempio seguente stampa "Hello!" quattro volte:

```
<#
    for(int i = 0; i < 4; i++)
    {
#>
Hello!
<#
    }
#>
```

 Un blocco di testo può essere inserito ovunque sia possibile usare nel codice un'istruzione `Write();`.

> [!NOTE]
> Quando si incorpora un blocco di testo all'interno di un'istruzione composta, ad esempio un ciclo o un condizionale, utilizzare sempre le parentesi graffe {...} per contenere il blocco di testo.

### <a name="expression-control-blocks"></a>Blocchi di controllo dell'espressione
 Un blocco di controllo dell'espressione valuta un'espressione e la converte in una stringa, che verrà quindi inserita nel file di output.

 I blocchi di controllo dell'espressione sono delimitati dai simboli `<#= ... #>`.

 Ad esempio, il blocco di controllo seguente inserisce nel file di output "5":

```
<#= 2 + 3 #>
```

 Si noti che il simbolo di apertura contiene tre caratteri "< # =".

 L'espressione può includere qualsiasi variabile che fa parte dell'ambito. Ad esempio, il blocco seguente visualizza righe con numeri:

```
<#@ output extension=".txt" #>
<#
    for(int i = 0; i < 4; i++)
    {
#>
This is hello number <#= i+1 #>: Hello!
<#
    }
#>
```

### <a name="class-feature-control-blocks"></a>Blocchi di controllo della funzionalità di classe
 Un blocco di controllo della funzionalità di classe definisce le proprietà, i metodi o qualsiasi altro codice che non deve essere incluso nella trasformazione principale. I blocchi della funzionalità di classe vengono spesso usati per le funzioni di supporto.  In genere, i blocchi di funzionalità di classe vengono inseriti in file distinti, in modo che possano essere [inclusi](#Include) da più di un modello di testo.

 I blocchi di controllo della funzionalità di classe sono delimitati dai simboli `<#+ ... #>`.

 Ad esempio, nel file di modello seguente viene dichiarato e usato un metodo:

```
<#@ output extension=".txt" #>
Squares:
<#
    for(int i = 0; i < 4; i++)
    {
#>
    The square of <#= i #> is <#= Square(i+1) #>.
<#
    }
#>
That is the end of the list.
<#+   // Start of class feature block
private int Square(int i)
{
    return i*i;
}
#>
```

 Le funzionalità di classe devono essere inserite alla fine del file nel quale vengono scritte. Tuttavia, è possibile usare un file con `<#@include#>` che contiene una funzionalità di classe anche se la direttiva `include` è seguita da testo e blocchi standard.

 Per ulteriori informazioni sui blocchi di controllo, vedere la pagina relativa ai [blocchi di controllo del modello di testo](../modeling/text-template-control-blocks.md).

### <a name="class-feature-blocks-can-contain-text-blocks"></a>I blocchi della funzionalità di classe possono contenere blocchi di testo
 È possibile scrivere un metodo che generi il testo. Esempio:

```
List of Squares:
<#
   for(int i = 0; i < 4; i++)
   {  WriteSquareLine(i); }
#>
End of list.
<#+   // Class feature block
private void WriteSquareLine(int i)
{
#>
   The square of <#= i #> is <#= i*i #>.
<#+
}
#>
```

 È particolarmente utile inserire un metodo che generi il testo in un file separato che possa essere incluso da più modelli.

## <a name="using-external-definitions"></a>Uso di definizioni esterne

### <a name="assemblies"></a>Assembly
 I blocchi di codice del modello possono usare i tipi definiti negli assembly .NET usati più di frequente come ad esempio System.dll. Inoltre, è possibile fare riferimento ad altri assembly .NET o ad assembly personalizzati. È possibile fornire un percorso o il nome sicuro di un assembly:

```
<#@ assembly name="System.Xml" #>
```

 Nel nome del percorso è consigliabile usare nomi di percorso assoluto o nomi di macro standard. Esempio:

```
<#@ assembly name="$(SolutionDir)library\MyAssembly.dll" #>
```

 La direttiva dell'assembly non ha alcun effetto in un [modello di testo pre-elaborato](../modeling/run-time-text-generation-with-t4-text-templates.md).

 Per altre informazioni, vedere [direttiva dell'assembly T4](../modeling/t4-assembly-directive.md).

### <a name="namespaces"></a>Namespaces
 La direttiva import è uguale alla clausola `using` in C# o alla clausola `imports` in Visual Basic. Consente di fare riferimento ai tipi nel codice senza usare un nome completo:

```
<#@ import namespace="System.Xml" #>
```

 È possibile usare il numero di direttive `assembly` e `import` desiderato. È necessario posizionarle prima dei blocchi di testo e di controllo.

 Per altre informazioni, vedere [direttiva import T4](../modeling/t4-import-directive.md).

### <a name="Include"></a>Inclusione di codice e testo
 La direttiva `include` inserisce il testo da un altro file di modello. Ad esempio, questa direttiva inserisce il contenuto del file `test.txt`.

```
<#@ include file="c:\test.txt" #>
```

 Il contenuto incluso viene elaborato più o meno come se facesse parte del modello di testo che include. Tuttavia, è possibile includere un file che contiene un blocco della funzionalità di classe `<#+...#>` anche se la direttiva include è seguita da testo ordinario e blocchi di controllo standard.

 Per altre informazioni, vedere [direttiva include T4](../modeling/t4-include-directive.md).

### <a name="utility-methods"></a>Metodi di utilità
 In un blocco di controllo esistono diversi metodi come ad esempio `Write()` che sono sempre disponibili. Tra questi ci sono i metodi che consentono di impostare un rientro nell'output e di segnalare errori.

 È anche possibile scrivere un set di metodi di utilità personalizzato.

 Per altre informazioni, vedere [metodi di utilità modello di testo](../modeling/text-template-utility-methods.md).

## <a name="transforming-data-and-models"></a>Trasformazioni di dati e modelli
 L'applicazione più utile per un modello di testo è generare materiale in base al contenuto di un'origine, ad esempio un modello, un database o un file di dati. Il modello estrae e riformatta i dati. Una raccolta di modelli può trasformare tale origine in più file.

 Esistono diversi approcci alla lettura del file di origine.

 **Leggere un file nel modello di testo**. Si tratta del modo più semplice per ottenere i dati nel modello:

```
<#@ import namespace="System.IO" #>
<# string fileContent = File.ReadAllText(@"C:\myData.txt"); ...
```

 **Caricare un file come modello esplorabile**. Un metodo più efficace è leggere i dati come un modello, in cui è possibile spostarsi con il codice del modello di testo. Ad esempio, è possibile caricare un file XML e spostarsi al suo interno con espressioni XPath. È inoltre possibile utilizzare [xsd. exe](/dotnet/standard/serialization/xml-schema-definition-tool-xsd-exe) per creare un set di classi con cui è possibile leggere i dati XML.

 **Modificare il file del modello in un diagramma o in un form.** [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] fornisce strumenti che consentono di modificare un modello come diagramma o Windows Form. In questo modo diventa più semplice illustrare il modello agli utenti dell'applicazione generata. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] crea anche un set di classi fortemente tipizzate che riflettono la struttura del modello. Per ulteriori informazioni, vedere [generazione di codice da un Domain-Specific Language](../modeling/generating-code-from-a-domain-specific-language.md).

### <a name="relative-file-paths-in-design-time-templates"></a>Percorsi di file relativi in modelli della fase di progettazione
 In un [modello di testo della fase di progettazione](../modeling/design-time-code-generation-by-using-t4-text-templates.md), se si desidera fare riferimento a un file in un percorso relativo al modello di testo, utilizzare `this.Host.ResolvePath()`. È inoltre necessario impostare `hostspecific="true"` nella direttiva `template`:

```
<#@ template hostspecific="true" language="C#" #>
<#@ output extension=".txt" #>
<#@ import namespace="System.IO" #>
<#
 // Find a path within the same project as the text template:
 string myFile = File.ReadAllText(this.Host.ResolvePath("MyFile.txt"));
#>
Content of MyFile.txt is:
<#= myFile #>
```

È anche possibile ottenere altri servizi forniti dall'host. Per ulteriori informazioni, vedere [accesso a Visual Studio o altri host da un modello](/previous-versions/visualstudio/visual-studio-2010/gg604090\(v\=vs.100\)).

### <a name="design-time-text-templates-run-in-a-separate-appdomain"></a>Modelli di testo della fase di progettazione eseguiti in un AppDomain separato

 È necessario tenere presente che un [modello di testo in fase di progettazione](../modeling/design-time-code-generation-by-using-t4-text-templates.md) viene eseguito in un AppDomain separato dall'applicazione principale. Nella maggior parte dei casi tale aspetto non è importante, ma in determinati casi complessi potrebbero verificarsi delle restrizioni. Se ad esempio si desidera passare i dati all'intero o all'esterno del modello da un servizio separato, il servizio deve fornire un'API serializzabile.

 Questo non è vero per un [modello di testo](../modeling/run-time-text-generation-with-t4-text-templates.md)in fase di esecuzione, che fornisce il codice compilato insieme al resto del codice.

## <a name="editing-templates"></a>Modifica dei modelli
 È possibile scaricare editor di modelli di testo specializzati dalla Raccolta online di Gestione estensioni. Scegliere **Gestione estensioni**dal menu **strumenti** . Fare clic su **raccolta online**e quindi usare lo strumento di ricerca.

## <a name="related-topics"></a>Argomenti correlati

|Attività|Argomento|
|-|-|
|Scrivere un modello.|[Linee guida per la scrittura di modelli di testo T4](../modeling/guidelines-for-writing-t4-text-templates.md)|
|Generare testo usando il codice programma.|[Struttura del modello di testo](../modeling/writing-a-t4-text-template.md)|
|Genera i file in una soluzione di Visual Studio.|[Generazione di codice in fase di progettazione tramite modelli di testo T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)|
|Eseguire la generazione di testo all'esterno di Visual Studio.|[Generazione di file con l'utilità TextTransform](../modeling/generating-files-with-the-texttransform-utility.md)|
|Trasformare i dati nel formato di un linguaggio specifico di dominio.|[Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Scrivere processori di direttive per trasformare le origini dati.|[Personalizzazione della trasformazione del testo T4](../modeling/customizing-t4-text-transformation.md)|
