---
title: Aggiungere strumenti di convalida dell'architettura personalizzati ai diagrammi delle dipendenze
description: Vengono fornite informazioni su come aggiungere la convalida dell'architettura personalizzata ai diagrammi delle dipendenze.
ms.date: 11/04/2016
ms.topic: how-to
titleSuffix: ''
helpviewer_keywords:
- dependency diagrams, adding custom validation
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.custom: SEO-VS-2020
ms.workload:
- multiple
ms.openlocfilehash: cc00f86bafebd14177400ffa0ee596a733e9fb28
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384629"
---
# <a name="add-custom-architecture-validation-to-dependency-diagrams"></a>Aggiungere strumenti di convalida dell'architettura personalizzati ai diagrammi delle dipendenze

In Visual Studio, gli utenti possono convalidare il codice sorgente in un progetto rispetto a un modello di livello in modo che possano verificare che il codice sorgente sia conforme alle dipendenze in un diagramma delle dipendenze. Benché sia disponibile un algoritmo di convalida standard, è possibile definire estensioni di convalida personalizzate.

Quando l'utente seleziona il comando **Convalida** architettura in un diagramma delle dipendenze, viene richiamato il metodo di convalida standard, seguito da eventuali estensioni di convalida installate.

> [!NOTE]
> In un diagramma delle dipendenze lo scopo principale della convalida è confrontare il diagramma con il codice del programma in altre parti della soluzione.

È possibile creare un pacchetto dell'estensione di convalida dei livelli in un progetto VSIX (Visual Studio Integration Extension), che è possibile distribuire ad altri utenti di Visual Studio. È possibile inserire solo il validator in un progetto VSIX oppure combinarlo con altre estensioni nello stesso progetto VSIX. È consigliabile scrivere il codice del validator in un progetto di Visual Studio a se stante anziché nello stesso progetto di altre estensioni.

> [!WARNING]
> Dopo aver creato un progetto di convalida, copiare il [codice di esempio](#example) disponibile alla fine di questo argomento e quindi modificarlo in base alle esigenze.

## <a name="requirements"></a>Requisiti

Vedere [Requisiti](../modeling/extend-layer-diagrams.md#requirements).

## <a name="defining-a-layer-validator-in-a-new-vsix"></a>Definizione di un validator dei livelli in un nuovo progetto VSIX

Il modo più rapido per creare un validator è usare il modello di progetto. In questo modo il codice e il manifesto VSIX vengono inseriti nello stesso progetto.

### <a name="to-define-an-extension-by-using-a-project-template"></a>Per definire un'estensione tramite un modello di progetto

1. Creare un nuovo **progetto estensione di convalida di Progettazione** livelli.

    Il modello crea un progetto che contiene un piccolo esempio.

   > [!WARNING]
   > Per fare in modo che il modello funzioni correttamente:
   >
   > - Modificare le chiamate a `LogValidationError` in modo da rimuovere gli argomenti facoltativi `errorSourceNodes` e `errorTargetNodes`.
   > - Se si usano proprietà personalizzate, applicare l'aggiornamento indicato in [Aggiungere proprietà personalizzate ai diagrammi delle dipendenze](../modeling/add-custom-properties-to-layer-diagrams.md).

2. Modificare il codice per definire la convalida. Per altre informazioni, vedere [Programmazione della convalida](#programming).

3. Per testare l'estensione, vedere [Debug della convalida dei livelli](#debugging).

   > [!NOTE]
   > Il metodo verrà chiamato solo in casi specifici e i punti di interruzione non funzioneranno automaticamente. Per altre informazioni, vedere [Debug della convalida dei livelli](#debugging).

::: moniker range="vs-2017"

4. Per installare l'estensione nell'istanza principale di Visual Studio o in un altro computer, trovare il file *vsix* nella directory *bin.* Copiare il file nel computer in cui si vuole installare l'estensione e fare doppio clic sul file stesso. Per disinstallarlo, scegliere **Estensioni e aggiornamenti** dal menu Strumenti. 

::: moniker-end

::: moniker range=">=vs-2019"

4. Per installare l'estensione nell'istanza principale di Visual Studio o in un altro computer, trovare il file *vsix* nella directory *bin.* Copiare il file nel computer in cui si vuole installare l'estensione e fare doppio clic sul file stesso. Per disinstallarlo, scegliere **Gestisci estensioni** **dal** menu Estensioni.

::: moniker-end

## <a name="adding-a-layer-validator-to-a-separate-vsix"></a>Aggiunta di validator dei livelli a un progetto VSIX separato

Se si vuole creare un progetto VSIX contenente validator dei livelli, comandi e altre estensioni, è consigliabile creare un unico progetto per definire l'estensione VSIX e progetti separati per i gestori.

### <a name="to-add-layer-validation-to-a-separate-vsix"></a>Per aggiungere la convalida dei livelli a un progetto VSIX separato

1. Creare un nuovo progetto **Libreria di classi**. Questo progetto conterrà la classe di convalida dei livelli.

2. Trovare o creare un **progetto VSIX** nella soluzione. Un progetto VSIX contiene un file denominato **source.extension.vsixmanifest**.

3. In **Esplora soluzioni** scegliere Imposta come progetto di avvio dal menu di scelta rapida del progetto **VSIX.**

4. In **source.extension.vsixmanifest** aggiungere il progetto di convalida dei livelli come componente MEF in **Asset**.

    1. Scegliere **Nuovo**.

    2. Nella finestra di dialogo **Aggiungi nuovo asset** impostare:

         **Tipo**  =  **Microsoft.VisualStudio.MefComponent**

         **Origine**  =  **Un progetto nella soluzione corrente**

         **Progetto**  =  *progetto di convalida*

5. È anche necessario aggiungere il progetto come convalida dei livelli:

    1. Scegliere **Nuovo**.

    2. Nella finestra di dialogo **Aggiungi nuovo asset** impostare:

         **Tipo**  =  **Microsoft.VisualStudio.ArchitectureTools.Layer.Validator**. Questa opzione non è inclusa nell'elenco a discesa. È necessario immetterla usando la tastiera.

         **Origine**  =  **Un progetto nella soluzione corrente**

         **Progetto**  =  *progetto di convalida*

6. Tornare al progetto di convalida dei livelli e aggiungere i riferimenti al progetto seguenti:

    |**Riferimento**|**Operazioni consentite**|
    |-|-|
    |Microsoft.VisualStudio.GraphModel.dll|Leggere il grafico dell'architettura|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema.dll|Leggere il code DOM associato ai livelli|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer.dll|Leggere il modello di livello|
    |Microsoft.VisualStudio.ArchitectureTools.Extensibility|Leggere e aggiornare forme e diagrammi|
    |System.ComponentModel.Composition|Definire il componente di convalida mediante Managed Extensibility Framework (MEF)|
    |Microsoft.VisualStudio.Modeling.Sdk.[versione]|Definire le estensioni di modellazione|

7. Copiare il codice di esempio disponibile alla fine di questo argomento nel file di classe nel progetto della libreria del validator in modo che contenga il codice per la convalida. Per altre informazioni, vedere [Programmazione della convalida](#programming).

8. Per testare l'estensione, vedere [Debug della convalida dei livelli](#debugging).

    > [!NOTE]
    > Il metodo verrà chiamato solo in casi specifici e i punti di interruzione non funzioneranno automaticamente. Per altre informazioni, vedere [Debug della convalida dei livelli](#debugging).

9. Per installare VSIX nell'istanza principale di Visual Studio o in un altro computer, trovare il file **vsix** nella directory **bin** del progetto VSIX. Copiare il file nel computer in cui si vuole installare il progetto VSIX. Fare doppio clic sul file VSIX in Esplora risorse

## <a name="programming-validation"></a><a name="programming"></a> Programmazione della convalida

Per definire un'estensione di convalida dei livelli, è necessario definire una classe con le caratteristiche seguenti:

- Il formato complessivo della dichiarazione è il seguente:

  ```csharp
  using System.ComponentModel.Composition;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
  using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
  using Microsoft.VisualStudio.GraphModel;
  ...
   [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator1Extension :
                    IValidateArchitectureExtension
    {
      public void ValidateArchitecture(Graph graph)
      {
         GraphSchema schema = graph.DocumentSchema;
        ...
    } }
  ```

- Quando si individua un errore, è possibile segnalarlo usando `LogValidationError()`.

  > [!WARNING]
  > Non usare i parametri facoltativi di `LogValidationError`.

Quando l'utente richiama il comando di menu **Convalida architettura** , il sistema di runtime dei livelli analizza i livelli e i rispettivi elementi per generare un grafico. Il grafico è costituito da quattro parti:

- I modelli di livello della Visual Studio che sono rappresentati come nodi e collegamenti nel grafico.

- Il codice, gli elementi di progetto e altri elementi definiti nella soluzione e rappresentati come nodi, insieme ai collegamenti che rappresentano le dipendenze individuate dal processo di analisi.

- I collegamenti dai nodi di livello ai nodi elemento del codice.

- I nodi che rappresentano gli errori individuati dal validator.

Una volta creato il grafico, viene chiamato il metodo di convalida standard. Al termine, tutti i metodi di convalida delle eventuali estensioni installate vengono chiamati in base a un ordine non specificato. Il grafico viene passato a ogni metodo `ValidateArchitecture` , che può analizzarlo e segnalare gli eventuali errori trovati.

> [!NOTE]
> Non corrisponde al processo di convalida che può essere usato nei linguaggi specifici del dominio.

I metodi di convalida non devono modificare il modello di livello o il codice convalidato.

Il modello di grafico è definito in <xref:Microsoft.VisualStudio.GraphModel>. Le classi principali sono <xref:Microsoft.VisualStudio.GraphModel.GraphNode> e <xref:Microsoft.VisualStudio.GraphModel.GraphLink>.

Ogni nodo e ogni collegamento hanno una o più categorie che specificano il tipo di elemento o la relazione che rappresenta. I nodi di un grafico tipico hanno le categorie seguenti:

- Dsl.LayerModel

- Dsl.Layer

- Dsl.Reference

- CodeSchema_Type

- CodeSchema_Namespace

- CodeSchema_Type

- CodeSchema_Method

- CodeSchema_Field

- CodeSchema_Property

I collegamenti dai livelli agli elementi nel codice sono associati alla categoria "Rappresenta".

## <a name="debugging-validation"></a><a name="debugging"></a> Debug della convalida

Per eseguire il debug dell'estensione di convalida dei livelli, premere CTRL+F5. Viene aperta un'istanza sperimentale di Visual Studio. In questa istanza aprire o creare un modello di livello. Questo modello deve essere associato al codice e deve avere almeno una dipendenza.

### <a name="test-with-a-solution-that-contains-dependencies"></a>Eseguire il test con una soluzione che contiene dipendenze

La convalida non viene eseguita se non sono presenti le caratteristiche seguenti:

- È presente almeno un collegamento di dipendenza nel diagramma delle dipendenze.

- Alcuni livelli nel modello sono associati a elementi del codice.

La prima volta che si avvia un'istanza sperimentale di Visual Studio testare l'estensione di convalida, aprire o creare una soluzione con queste caratteristiche.

### <a name="run-clean-solution-before-validate-architecture"></a>Eseguire Pulisci soluzione prima di Convalida architettura

Ogni volta che si aggiorna il codice di convalida, usare il comando **Pulisci soluzione** del menu **Compila** nella soluzione sperimentale prima di testare il comando Convalida. Questa operazione è necessaria perché i risultati della convalida vengono memorizzati nella cache. Se non è stato aggiornato il diagramma delle dipendenze di test o il relativo codice, i metodi di convalida non verranno eseguiti.

### <a name="launch-the-debugger-explicitly"></a>Avviare il debugger in modo esplicito

La convalida viene eseguita in un processo separato. Di conseguenza, i punti di interruzione nel metodo di convalida non verranno attivati. È necessario connettere il debugger al processo in modo esplicito all'avvio della convalida.

Per connettere il debugger al processo di convalida, inserire una chiamata a `System.Diagnostics.Debugger.Launch()` all'avvio del metodo di convalida. Quando viene visualizzata la finestra di dialogo di debug, selezionare l'istanza principale di Visual Studio.

In alternativa, è possibile inserire una chiamata a `System.Windows.Forms.MessageBox.Show()`. Quando viene visualizzata la finestra di messaggio, passare all'istanza principale di Visual Studio e scegliere Collega a processo dal **menu** **Debug**. Selezionare il processo denominato **Graphcmd.exe**.

Avviare sempre l'istanza sperimentale premendo CTRL+F5 (**Avvia senza eseguire debug**).

### <a name="deploying-a-validation-extension"></a>Distribuzione di un'estensione di convalida

Per installare l'estensione di convalida in un computer in cui è installata una versione appropriata di Visual Studio, aprire il file VSIX nel computer di destinazione.

## <a name="example-code"></a><a name="example"></a> Codice di esempio

```csharp
using System;
using System.ComponentModel.Composition;
using System.Globalization;
using System.Linq;
using System.Text.RegularExpressions;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.CodeSchema;
using Microsoft.VisualStudio.ArchitectureTools.Extensibility.Layer;
using Microsoft.VisualStudio.GraphModel;

namespace Validator3
{
    [Export(typeof(IValidateArchitectureExtension))]
    public partial class Validator3Extension : IValidateArchitectureExtension
    {
        /// <summary>
        /// Validate the architecture
        /// </summary>
        /// <param name="graph">The graph</param>
        public void ValidateArchitecture(Graph graph)
        {
            if (graph == null) throw new ArgumentNullException("graph");

            // Uncomment the line below to debug this extension during validation
            // System.Windows.Forms.MessageBox.Show("Attach 2 to GraphCmd.exe with process id " + System.Diagnostics.Process.GetCurrentProcess().Id);

            // Get all layers on the diagram
            foreach (GraphNode layer in graph.Nodes.GetByCategory("Dsl.Layer"))
            {
                System.Threading.Thread.Sleep(100);
                // Get the required regex property from the layer node
                string regexPattern = "^[a-zA-Z]+$"; //layer[customPropertyCategory] as string;
                if (!string.IsNullOrEmpty(regexPattern))
                {
                    Regex regEx = new Regex(regexPattern);

                    // Get all referenced types in this layer including those from nested layers so each
                    // type is validated against all containing layer constraints.
                    foreach (GraphNode containedType in layer.FindDescendants().Where(node => node.HasCategory("CodeSchema_Type")))
                    {
                        // Check the type name against the required regex
                        CodeGraphNodeIdBuilder builder = new CodeGraphNodeIdBuilder(containedType.Id, graph);
                        string typeName = builder.Type.Name;
                        if (!regEx.IsMatch(typeName))
                        {
                            // Log an error
                            string message = string.Format(CultureInfo.CurrentCulture, Resources.InvalidTypeNameMessage, typeName);
                            this.LogValidationError(graph, typeName + "TypeNameError", message, GraphErrorLevel.Error, layer);
                        }
                    }
                }

            }

        }
    }
}
```

## <a name="see-also"></a>Vedi anche

- [Estendere i diagrammi delle dipendenze](../modeling/extend-layer-diagrams.md)
