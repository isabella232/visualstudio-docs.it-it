---
title: 'Diagrammi delle dipendenze: linee guida'
description: Informazioni su come descrivere l'architettura dell'app a un livello elevato creando diagrammi delle dipendenze in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f46e2b774cd4da2ef9cdb9ddef7efd19f731ade7
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112391023"
---
# <a name="dependency-diagrams-guidelines"></a>Diagrammi delle dipendenze: linee guida

Descrivere l'architettura dell'app a un livello elevato creando diagrammi *delle dipendenze* in Visual Studio. Assicurarsi che il codice rimanga coerente con questa progettazione convalidando il codice con un diagramma delle dipendenze. È anche possibile includere la convalida dei livelli nel processo di compilazione. Vedere [Channel 9 Video: Progettare e convalidare l'architettura usando i diagrammi delle dipendenze.](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture)

Per informazioni su quali edizioni di Visual Studio questa funzionalità, vedere Supporto dell'edizione per gli strumenti di [architettura e modellazione](../modeling/analyze-and-model-your-architecture.md#VersionSupport).

> [!NOTE]
> I diagrammi delle dipendenze per i progetti .NET Core sono supportati a partire Visual Studio 2019 versione 16.2.

## <a name="what-is-a-dependency-diagram"></a>Che cos'è un diagramma delle dipendenze?

Come un diagramma dell'architettura tradizionale, un diagramma delle dipendenze identifica i componenti principali o le unità funzionali della progettazione e le relative interdipendenze. Ogni nodo del diagramma, denominato *livello*, rappresenta un gruppo logico di spazi dei nomi, progetti o altri elementi. È possibile tracciare le dipendenze che devono esistere nella progettazione. A differenza di un diagramma architettura tradizionale, è possibile verificare che le dipendenze effettive nel codice sorgente siano conformi alle dipendenze desiderate specificate. Includendo la convalida nel normale processo di compilazione in [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], sarà possibile assicurare che il codice programma continui ad essere coerente con l'architettura del sistema anche in caso di modifiche future. Vedere [Diagrammi di dipendenza: Riferimento](../modeling/layer-diagrams-reference.md).

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Come progettare o aggiornare l'app con diagrammi delle dipendenze

La procedura seguente offre una panoramica dell'uso dei diagrammi delle dipendenze all'interno del processo di sviluppo. Le sezioni successive in questo argomento descrivono in modo più dettagliato ogni passaggio. Se si sviluppa una nuova progettazione, omettere i passaggi relativi al codice esistente.

> [!NOTE]
> I passaggi sono visualizzati in ordine approssimativo. Potrebbe essere necessario sovrapporre alcune attività, riordinarle per adattarle alla situazione specifica ed eseguirle di nuovo all'inizio di ogni iterazione nel progetto.

1. [Creare un diagramma delle dipendenze](#Create) per l'intera applicazione o per un livello al suo interno.

2. [Definire i livelli per rappresentare le aree funzionali principali o i componenti](#CreateLayers) dell'applicazione. Assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se si dispone di una soluzione Visual Studio, è possibile associare ogni livello a una raccolta di elementi *,* ad esempio progetti, spazi dei nomi, file e così via.

3. [Individuare le dipendenze esistenti tra](#Generate) i livelli.

4. [Modificare i livelli e le dipendenze](#EditArchitecture) per visualizzare la progettazione aggiornata che si vuole riflettere nel codice.

5. [Progettare nuove aree dell'applicazione](#NewAreas) creando livelli per rappresentare i principali blocchi o componenti dell'architettura e definendo le dipendenze per mostrare come ogni livello usa gli altri.

6. [Modificare il layout e l'aspetto del diagramma](#EditLayout) per illustrarlo con i colleghi.

7. [Convalidare il codice rispetto al diagramma delle](#Validate) dipendenze per evidenziare i conflitti tra il codice e l'architettura necessaria.

8. [Aggiornare il codice in modo che sia conforme alla nuova architettura](#UpdateCode). Sviluppare in modo iterativo ed effettuare il refactoring del codice fino a ottenere una convalida senza conflitti.

9. [Includere la convalida dei livelli nel processo di](#BuildValidation) compilazione per garantire che il codice continui a rispettare la progettazione.

## <a name="create-a-dependency-diagram"></a><a name="Create"></a> Creare un diagramma delle dipendenze

È necessario creare un diagramma delle dipendenze all'interno di un progetto di modellazione. È possibile aggiungere un nuovo diagramma dipendenze a un progetto di modellazione esistente, creare un nuovo progetto di modellazione per il diagramma delle dipendenze o copiare un diagramma delle dipendenze esistente all'interno dello stesso progetto di modellazione.

> [!IMPORTANT]
> Non aggiungere, trascinare o copiare un diagramma delle dipendenze esistente da un progetto di modellazione a un altro progetto di modellazione o in un'altra posizione nella soluzione. Un diagramma delle dipendenze copiato in questo modo avrà gli stessi riferimenti del diagramma originale, anche se si modifica il diagramma. Ciò impedirà il corretto funzionamento della convalida dei livelli e potrebbe provocare altri problemi, ad esempio la mancanza di elementi o altri errori durante il tentativo di apertura del diagramma.

Vedere [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> Definire i livelli per rappresentare le aree funzionali o i componenti

I livelli rappresentano gruppi logici *di elementi*, ad esempio progetti, file di codice, spazi dei nomi, classi e metodi. È possibile creare livelli da elementi di progetti Visual C# e Visual Basic oppure collegare specifiche o piani a un livello collegando documenti, ad esempio file di Word o presentazioni di PowerPoint. Ogni livello viene visualizzato come un rettangolo nel diagramma e viene indicato il numero di artefatti collegati a ogni livello. Un livello può contenere livelli annidati che descrivono attività più specifiche.

È in genere consigliabile assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se gli artefatti sono strettamente interdipendenti, posizionarli nello stesso livello. Se gli artefatti possono essere aggiornati separatamente o possono essere usati in applicazioni distinte, posizionarli in livelli diversi. Per informazioni sui modelli di strating, visitare il sito Patterns & Practices all'indirizzo [http://go.microsoft.com/fwlink/?LinkId=145794](https://archive.codeplex.com/?p=apparch) .

> [!TIP]
> Esistono alcuni tipi di elementi che è possibile collegare ai livelli, ma che non supportano la convalida rispetto al diagramma delle dipendenze. Per verificare se l'artefatto supporta la convalida, aprire **Esplora** livelli per esaminare la proprietà **Supports Validation** del collegamento all'elemento. Vedere [Individuare le dipendenze esistenti tra i livelli](#Generate).

Quando si aggiorna un'applicazione poco nota, è anche possibile creare mappe codice. Questi diagrammi consentono di individuare i motivi e le dipendenze durante l'esplorazione del codice. Usare Esplora soluzioni per esplorare spazi dei nomi e classi, che spesso corrispondono correttamente ai livelli esistenti. Assegnare questi elementi di codice ai livelli trascinandoli dal Esplora soluzioni ai diagrammi delle dipendenze. È quindi possibile usare i diagrammi delle dipendenze per aggiornare il codice e mantenerlo coerente con la progettazione.

Vedere:

- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)

- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Individuare le dipendenze esistenti tra i livelli

È presente una dipendenza quando un elemento associato a un livello dispone di un riferimento a un elemento associato a un altro livello. Ad esempio, una classe di un livello dichiara una variabile che dispone di una classe in un altro livello. Per individuare le dipendenze esistenti, è possibile decompilarle.

> [!NOTE]
> Non è possibile decompilare dipendenze per determinati tipi di elementi. Ad esempio, non è possibile decompilare dipendenze da e verso un livello collegato a un file di testo. Per visualizzare gli artefatti con dipendenze che è possibile decodificare, fare clic con il pulsante destro del mouse su uno o più livelli e quindi scegliere **Visualizza collegamenti**. In **Esplora livelli** esaminare la colonna Supporto **convalida.** Le dipendenze non verranno decodificate per gli artefatti per i quali questa colonna mostra **False**.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Per decompilare le dipendenze esistenti tra i livelli

Selezionare uno o più livelli, fare clic con il pulsante destro del mouse su un livello selezionato e quindi scegliere **Genera dipendenze**.

In genere vengono visualizzate alcune dipendenze che non dovrebbero esistere. È possibile modificare queste dipendenze per allinearle con la progettazione desiderata.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> Modificare livelli e dipendenze per visualizzare la progettazione prevista

Per descrivere le modifiche che si prevede di apportare al sistema o all'architettura prevista, seguire questa procedura per modificare il diagramma delle dipendenze. È anche possibile prendere in considerazione alcune modifiche relative al refactoring per migliorare la struttura del codice prima di estenderlo. Vedere [Miglioramento della struttura del codice](#Improving).

|**To**|**Eseguire questi passaggi**|
|-|-|
|Eliminare una dipendenza che non dovrebbe essere presente|Fare clic sulla dipendenza e quindi premere **CANC.**|
|Modificare o limitare la direzione di una dipendenza|Impostarne **la proprietà Direction.**|
|Creare nuove dipendenze|Usare gli **strumenti Dipendenza** e **Dipendenza bidirezionale.**<br /><br /> Per disegnare più dipendenze, fare doppio clic sullo strumento. Al termine, fare clic su **Strumento** Puntatore o premere **ESC.**|
|Specificare che gli elementi associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi nella proprietà **Dipendenze** spazio dei nomi non consentite del livello. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli elementi associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi nella proprietà **Spazi dei nomi** non consentiti del livello. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi nella proprietà **Spazi dei nomi obbligatori del** livello. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> Miglioramento della struttura del codice

Le modifiche relative al refactoring sono miglioramenti che non influiscono sul comportamento dell'applicazione, ma contribuiscono a rendere il codice più semplice da modificare ed estendere nel futuro. Il codice ben strutturato ha una progettazione facile da astrarre da un diagramma delle dipendenze.

Ad esempio, se si crea un livello per ogni spazio dei nomi nel codice e quindi si decompilano le dipendenze, dovrebbe essere presente un insieme minimo di dipendenze unidirezionali tra i livelli. Se si crea un diagramma più dettagliato usando classi o metodi come livelli, il risultato dovrebbe avere le stesse caratteristiche.

In caso contrario, il codice sarà più difficile da modificare nel corso del ciclo di vita e sarà meno adatto per la convalida tramite diagrammi delle dipendenze.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Progettare nuove aree dell'applicazione

Quando si inizia a sviluppare un nuovo progetto o una nuova area in un nuovo progetto, è possibile tracciare livelli e dipendenze per semplificare l'identificazione dei componenti principali prima di iniziare a sviluppare il codice.

- **Mostrare modelli di architettura identificabili** nei diagrammi delle dipendenze, se possibile. Ad esempio, un diagramma delle dipendenze che descrive un'applicazione desktop può includere livelli come Presentazione, Logica di dominio e Archivio dati. Un diagramma delle dipendenze che copre una singola funzionalità all'interno di un'applicazione può avere livelli quali Modello, Visualizzazione e Controller. Per altre informazioni su questi modelli, vedere [Patterns & Practices: Application Architecture](https://archive.codeplex.com/?p=apparch).

- **Creare un artefatto di codice per ogni livello,** ad esempio uno spazio dei nomi, una classe o un componente. In questo modo sarà più semplice seguire il codice e collegare gli elementi di codice ai livelli. Non appena si crea ogni artefatto, collegarlo al livello appropriato.

- **Non è necessario collegare la** maggior parte delle classi e di altri elementi ai livelli perché rientrano in artefatti più grandi, ad esempio gli spazi dei nomi già collegati ai livelli.

- **Creare un nuovo diagramma per una nuova funzionalità.** In genere, saranno presenti uno o più diagrammi delle dipendenze che descrivono l'intera applicazione. Se si progetta una nuova funzionalità nell'applicazione, non apportare aggiunte o modifiche ai diagrammi esistenti. Creare invece un diagramma personalizzato che rispecchia nuove parti del codice. I livelli nel nuovo diagramma possono includere livelli relativi a presentazione, logica di dominio e database per la nuova funzionalità.

     Quando si compila l'applicazione, il codice verrà convalidato rispetto al diagramma complessivo e al diagramma più dettagliato relativo alle funzionalità.

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> Modificare il layout per la presentazione e la discussione

Per semplificare l'identificazione di livelli e dipendenze o per esaminarli con i membri del team, modificare l'aspetto e il layout del diagramma nei modi seguenti:

- Modificare le dimensioni, le forme e le posizioni dei livelli.

- Cambiare i colori dei livelli e le dipendenze.

  - Selezionare uno o più livelli o dipendenze, fare clic con il pulsante destro del mouse e quindi scegliere **Proprietà.** Nella finestra **Proprietà** modificare la **proprietà** Colore.

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> Convalidare il codice rispetto al diagramma

Dopo aver modificato il diagramma, è possibile convalidarlo in base al codice manualmente in qualsiasi momento o automaticamente ogni volta che si esegue la compilazione.

Vedere:

- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)

- [Includere la convalida dei livelli nel processo di compilazione](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> Aggiornare il codice in modo che sia conforme alla nuova architettura

In genere, gli errori vengono visualizzati la prima volta che si convalida il codice rispetto a un diagramma delle dipendenze aggiornato. Gli errori possono avere cause diverse:

- Un artefatto viene assegnato al livello errato. In questo caso, spostare l'elemento.

- Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.

Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. Si tratta in genere di un processo iterativo. Per altre informazioni su questi errori, vedere [Convalidare il codice con diagrammi delle dipendenze.](../modeling/validate-code-with-layer-diagrams.md)

> [!NOTE]
> Durante lo sviluppo o il refactoring del codice, è possibile che si abbia a che fare con nuovi artefatti per il collegamento al diagramma delle dipendenze. È tuttavia possibile che ciò non sia necessario, ad esempio se sono presenti livelli che rappresentano spazi dei nomi esistenti e il nuovo codice aggiunge altri elementi a questi spazi dei nomi.

Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è consigliabile registrare un elemento di lavoro in Team Foundation. Per eseguire questa attività, vedere [Convalidare il codice con diagrammi delle dipendenze.](../modeling/validate-code-with-layer-diagrams.md)

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Includere la convalida dei livelli nel processo di compilazione

Per garantire che le modifiche future nel codice siano conformi ai diagrammi delle dipendenze, includere la convalida dei livelli nel processo di compilazione standard della soluzione. Ogni volta che altri membri del team compilano la soluzione, eventuali differenze tra le dipendenze nel codice e il diagramma delle dipendenze verranno segnalate come errori di compilazione. Per altre informazioni sull'inclusione della convalida dei livelli nel processo di compilazione, vedere [Convalidare il codice con diagrammi delle dipendenze.](../modeling/validate-code-with-layer-diagrams.md)

## <a name="see-also"></a>Vedi anche

- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)
