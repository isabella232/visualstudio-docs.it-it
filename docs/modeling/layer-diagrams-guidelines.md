---
title: 'Diagrammi delle dipendenze: Indicazioni'
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb6908db6b111f2ff67f2e1ca3761b11c302f5d4
ms.sourcegitcommit: 87d7123c09812534b7b08743de4d11d6433eaa13
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/01/2019
ms.locfileid: "57223819"
---
# <a name="dependency-diagrams-guidelines"></a>I diagrammi delle dipendenze: linee guida

Descrivere l'architettura dell'app ad alto livello creando *diagrammi delle dipendenze* in Visual Studio. Assicurarsi che il codice rimanga coerenza con la progettazione convalidando il codice con un diagramma delle dipendenze. È anche possibile includere la convalida dei livelli nel processo di compilazione. Vedere [Video di Channel 9: Progettare e convalidare l'architettura utilizzando i diagrammi delle dipendenze](http://go.microsoft.com/fwlink/?LinkID=252073).

Per informazioni su quali edizioni di Visual Studio supportano questa funzionalità, vedere [supporto di edizione per un'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> I diagrammi delle dipendenze non sono supportati per i progetti .NET Core in Visual Studio.

## <a name="what-is-a-dependency-diagram"></a>Che cos'è un diagramma delle dipendenze?

Ad esempio un diagramma architettura tradizionale, un diagramma delle dipendenze identifica i componenti principali o unità funzionali della progettazione e le relative interdipendenze. Ogni nodo nel diagramma, denominato un *layer*, rappresenta un gruppo logico di spazi dei nomi, progetti o altri elementi. È possibile tracciare le dipendenze che devono esistere nella progettazione. A differenza di un diagramma architettura tradizionale, è possibile verificare che le dipendenze effettive nel codice sorgente siano conformi alle dipendenze desiderate specificate. Includendo la convalida nel normale processo di compilazione in [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], sarà possibile assicurare che il codice programma continui ad essere coerente con l'architettura del sistema anche in caso di modifiche future. Vedere [diagrammi delle dipendenze: informazioni di riferimento](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Come progettare o aggiornare l'app con i diagrammi delle dipendenze

I passaggi seguenti offrono una panoramica di come usare i diagrammi delle dipendenze all'interno del processo di sviluppo. Le sezioni successive in questo argomento descrivono in modo più dettagliato ogni passaggio. Se si sviluppa una nuova progettazione, omettere i passaggi relativi al codice esistente.

> [!NOTE]
> I passaggi sono visualizzati in ordine approssimativo. Potrebbe essere necessario sovrapporre alcune attività, riordinarle per adattarle alla situazione specifica ed eseguirle di nuovo all'inizio di ogni iterazione nel progetto.

1.  [Creare un diagramma di dipendenza](#Create) per l'intera applicazione o per un livello all'interno di esso.

2.  [Definire livelli per rappresentare aree funzionali primarie o componenti](#CreateLayers) dell'applicazione. Assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se si dispone di una soluzione di Visual Studio, è possibile associare ogni livello a una raccolta di *artefatti*, ad esempio progetti, gli spazi dei nomi, i file e così via.

3.  [Individuare le dipendenze esistenti](#Generate) tra livelli.

4.  [Modificare i livelli e dipendenze](#EditArchitecture) per mostrare l'aggiornamento che si vuole rispecchiare nel codice di progettazione.

5.  [Progettare nuove aree dell'applicazione](#NewAreas) la creazione di livelli per rappresentare i blocchi di architettura principali o i componenti e definendo le dipendenze per mostrare come ogni livello Usa gli altri.

6.  [Modificare il layout e l'aspetto del diagramma](#EditLayout) per semplificarne l'analisi con i colleghi.

7.  [Convalidare il codice rispetto al diagramma di dipendenza](#Validate) per evidenziare i conflitti tra il codice e l'architettura necessaria.

8.  [Aggiornare il codice per garantire la conformità alla nuova architettura](#UpdateCode). Sviluppare in modo iterativo ed effettuare il refactoring del codice fino a ottenere una convalida senza conflitti.

9. [Includere la convalida dei livelli nel processo di compilazione](#BuildValidation) per assicurarsi che il codice sia sempre conforme alla progettazione.

## <a name="Create"></a> Creare un diagramma delle dipendenze

All'interno di un progetto di modellazione, è necessario creare un diagramma delle dipendenze. È possibile aggiungere un nuovo diagramma di dipendenza a un progetto di modellazione esistente, creare un nuovo progetto di modellazione delle minacce per il diagramma delle dipendenze o copiare alcun diagramma di dipendenza esistente nello stesso progetto di modellazione.

> [!IMPORTANT]
> Non aggiungere, trascinare o copiare alcun diagramma di dipendenza esistente da un progetto di modellazione a un altro progetto di modellazione o in un'altra posizione nella soluzione. Un diagramma di dipendenza che viene copiato in questo modo avranno gli stessi riferimenti del diagramma originale, anche se si modifica il diagramma. Ciò impedirà il corretto funzionamento della convalida dei livelli e potrebbe provocare altri problemi, ad esempio la mancanza di elementi o altri errori durante il tentativo di apertura del diagramma.

Visualizzare [creare i diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a> Definire livelli per rappresentare aree funzionali o componenti

I livelli rappresentano gruppi logici di *artefatti*, ad esempio progetti, file di codice, gli spazi dei nomi, classi e metodi. È possibile creare livelli da artefatti da progetti Visual c# e Visual Basic, oppure è possibile collegare specifiche o piani a un livello collegando documenti, ad esempio file di Word o presentazioni di PowerPoint. Ogni livello viene visualizzato come un rettangolo nel diagramma e viene indicato il numero di artefatti collegati a ogni livello. Un livello può contenere livelli annidati che descrivono attività più specifiche.

È in genere consigliabile assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se gli elementi sono strettamente interdipendenti, posizionarli nello stesso livello. Se gli artefatti possono essere aggiornati separatamente o possono essere usati in applicazioni distinte, posizionarli in livelli diversi. Per altre informazioni sui modelli di livello, visitare il sito modelli e procedure all'indirizzo [ http://go.microsoft.com/fwlink/?LinkId=145794 ](http://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> Esistono alcuni tipi di elementi possono essere collegati ai livelli ma che non supportano la convalida rispetto al diagramma di dipendenza. Per vedere se l'elemento supporta la convalida, aprire **Esplora livello** esaminare le **supporta la convalida** proprietà del collegamento dell'artefatto. Visualizzare [individua le dipendenze esistenti tra livelli](#Generate).

Quando si aggiorna un'applicazione poco nota, è anche possibile creare mappe codice. Questi diagrammi consentono di individuare i motivi e le dipendenze durante l'esplorazione del codice. Usare Esplora soluzioni per esplorare spazi dei nomi e classi, che spesso corrispondono correttamente ai livelli esistenti. Assegnare questi elementi di codice ai livelli trascinandoli da Esplora soluzioni per i diagrammi delle dipendenze. È quindi possibile usare i diagrammi delle dipendenze che consentono di aggiornare il codice e mantenerlo coerente con la progettazione.

Vedere:

-   [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)

-   [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)

-   [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a> Individuare le dipendenze esistenti tra livelli

È presente una dipendenza quando un elemento associato a un livello dispone di un riferimento a un elemento associato a un altro livello. Ad esempio, una classe di un livello dichiara una variabile che dispone di una classe in un altro livello. Per individuare le dipendenze esistenti, è possibile decompilarle.

> [!NOTE]
> Non è possibile decompilare dipendenze per determinati tipi di elementi. Ad esempio, non è possibile decompilare dipendenze da e verso un livello collegato a un file di testo. Per vedere quali artefatti sono associate dipendenze che è possibile decompilare, fare doppio clic su uno o più livelli e quindi fare clic su **Visualizza collegamenti**. Nelle **Esplora livello**, esaminare le **supporta la convalida** colonna. Le dipendenze non verranno decompilate per artefatti per cui questa colonna viene visualizzato **False**.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Per decompilare le dipendenze esistenti tra i livelli

Selezionare uno o più livelli, fare doppio clic su un livello selezionato e quindi fare clic su **genera dipendenze**.

In genere vengono visualizzate alcune dipendenze che non dovrebbero esistere. È possibile modificare queste dipendenze per allinearle con la progettazione desiderata.

## <a name="EditArchitecture"></a> Modificare livelli e dipendenze per visualizzare la progettazione desiderata

Per descrivere le modifiche che si prevede di apportare al sistema o l'architettura desiderata, usare la procedura seguente per modificare il diagramma delle dipendenze. È anche possibile prendere in considerazione alcune modifiche relative al refactoring per migliorare la struttura del codice prima di estenderlo. Visualizzare [miglioramento della struttura del codice](#Improving).

|**Per**|**Eseguire questi passaggi**|
|-|-|
|Eliminare una dipendenza che non dovrebbe essere presente|Fare clic sulla dipendenza e quindi premere **Elimina**.|
|Modificare o limitare la direzione di una dipendenza|Impostare relativi **direzione** proprietà.|
|Creare nuove dipendenze|Usare la **Dependency** e **dipendenza bidirezionale** strumenti.<br /><br /> Per disegnare più dipendenze, fare doppio clic sullo strumento. Al termine, fare clic sui **puntatore** degli strumenti oppure premere la **ESC** chiave.|
|Specificare che gli elementi associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **dipendenze Namespace non è consentito** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli elementi associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **Forbidden Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi del livello **Required Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|

### <a name="Improving"></a> Miglioramento della struttura del codice

Le modifiche relative al refactoring sono miglioramenti che non influiscono sul comportamento dell'applicazione, ma contribuiscono a rendere il codice più semplice da modificare ed estendere nel futuro. Codice ben strutturato è una progettazione semplice eseguire un'astrazione per un diagramma delle dipendenze.

Ad esempio, se si crea un livello per ogni spazio dei nomi nel codice e quindi si decompilano le dipendenze, dovrebbe essere presente un insieme minimo di dipendenze unidirezionali tra i livelli. Se si crea un diagramma più dettagliato usando classi o metodi come livelli, il risultato dovrebbe avere le stesse caratteristiche.

Se ciò non avviene, il codice sarà più difficile da modificare per tutta la vita e sarà meno idoneo per la convalida usando i diagrammi delle dipendenze.

## <a name="NewAreas"></a> Progettare nuove aree dell'applicazione

Quando si inizia a sviluppare un nuovo progetto o una nuova area in un nuovo progetto, è possibile tracciare livelli e dipendenze per semplificare l'identificazione dei componenti principali prima di iniziare a sviluppare il codice.

-   **Visualizzare i modelli di architettura identificabili** nei diagrammi delle dipendenze, se possibile. Ad esempio, un diagramma di dipendenza che descrive un'applicazione desktop può includere livelli quali presentazione, logica di dominio e Data Store. Un diagramma di dipendenza che riguarda una singola funzionalità all'interno di un'applicazione può includere livelli quali modello, visualizzazione e Controller. Per altre informazioni su tali modelli, vedere [Patterns & Practices: Architettura dell'applicazione](http://go.microsoft.com/fwlink/?LinkId=145794).

-   **Creare un elemento di codice per ogni livello** come spazio dei nomi, classe o componente. In questo modo sarà più semplice seguire il codice e collegare gli elementi di codice ai livelli. Non appena si crea ogni artefatto, collegarlo al livello appropriato.

-   **Non è necessario collegare la maggior parte delle classi e altri elementi ai livelli** poiché si trovano all'interno di elementi più grandi quali spazi dei nomi che sono già stati collegati ai livelli.

-   **Creare un nuovo diagramma di una nuova caratteristica**. In genere, saranno presenti uno o più diagrammi delle dipendenze che descrivono l'intera applicazione. Se si progetta una nuova funzionalità nell'applicazione, non apportare aggiunte o modifiche ai diagrammi esistenti. Creare invece un diagramma personalizzato che rispecchia nuove parti del codice. I livelli nel nuovo diagramma possono includere livelli relativi a presentazione, logica di dominio e database per la nuova funzionalità.

     Quando si compila l'applicazione, il codice verrà convalidato rispetto al diagramma complessivo e al diagramma più dettagliato relativo alle funzionalità.

## <a name="EditLayout"></a> Modificare il layout per la presentazione e discussione

Per semplificare l'identificazione di livelli e dipendenze o per esaminarli con i membri del team, modificare l'aspetto e il layout del diagramma nei modi seguenti:

-   Modificare le dimensioni, le forme e le posizioni dei livelli.

-   Cambiare i colori dei livelli e le dipendenze.

    -   Selezionare uno o più livelli o dipendenze, pulsante destro del mouse e quindi fare clic su **proprietà**. Nel **delle proprietà** finestra, modificare il **colore** proprietà.

## <a name="Validate"></a> Convalidare il codice rispetto al diagramma

Dopo avere modificato il diagramma, è possibile convalidarlo rispetto al codice manualmente in qualsiasi momento oppure automaticamente ogni volta che compila.

Vedere:

-   [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)

-   [Includere la convalida dei livelli nel processo di compilazione](#BuildValidation)

## <a name="UpdateCode"></a> Aggiornare il codice per garantire la conformità alla nuova architettura

In genere, alla prima convalida del codice in base a un diagramma delle dipendenze aggiornato vengono visualizzati errori. Gli errori possono avere cause diverse:

-   Un elemento viene assegnato al livello errato. In questo caso, spostare l'elemento.

-   Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.

Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. Si tratta in genere di un processo iterativo. Per altre informazioni su questi errori, vedere [convalidare il codice con diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Durante lo sviluppo o il refactoring del codice, potrebbe essere nuovi artefatti da collegare al diagramma di dipendenza. È tuttavia possibile che ciò non sia necessario, ad esempio se sono presenti livelli che rappresentano spazi dei nomi esistenti e il nuovo codice aggiunge altri elementi a questi spazi dei nomi.

Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è buona norma registrare un elemento di lavoro in Team Foundation. Per eseguire questa attività, vedere [convalidare il codice con diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a> Includere la convalida dei livelli nel processo di compilazione

Per garantire che le modifiche future nel codice siano conformi ai diagrammi delle dipendenze, includere la convalida dei livelli per il processo di compilazione standard della soluzione. Ogni volta che altri membri del team compilano la soluzione, eventuali differenze tra le dipendenze nel codice e il diagramma delle dipendenze verranno segnalate come errori di compilazione. Per altre informazioni sull'inclusione della convalida dei livelli nel processo di compilazione, vedere [convalidare il codice con diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Vedere anche

- [Diagrammi delle dipendenze: Riferimento](../modeling/layer-diagrams-reference.md)
- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)