---
title: 'Diagrammi delle dipendenze: linee guida'
description: Informazioni su come descrivere l'architettura dell'app a un livello elevato creando diagrammi di dipendenza in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 09/28/2018
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5bfef2f9397fbe8dfeceaa8789cf8d118315b26d
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363965"
---
# <a name="dependency-diagrams-guidelines"></a>Diagrammi di dipendenza: linee guida

Descrivere l'architettura dell'app a un livello elevato creando *diagrammi di dipendenza* in Visual Studio. Verificare che il codice rimanga coerente con questa progettazione convalidando il codice con un diagramma delle dipendenze. È anche possibile includere la convalida dei livelli nel processo di compilazione. Vedere [video di Channel 9: progettare e convalidare l'architettura usando i diagrammi delle dipendenze](https://channel9.msdn.com/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Using-layer-diagrams-to-design-and-validate-your-architecture).

Per visualizzare le edizioni di Visual Studio che supportano questa funzionalità, vedere [supporto dell'edizione per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

> [!NOTE]
> I diagrammi di dipendenza per i progetti .NET Core sono supportati a partire da Visual Studio 2019 versione 16,2.

## <a name="what-is-a-dependency-diagram"></a>Che cos'è un diagramma delle dipendenze?

Analogamente a un diagramma di architettura tradizionale, un diagramma delle dipendenze identifica i componenti principali o le unità funzionali della progettazione e le relative interdipendenze. Ogni nodo del diagramma, denominato *livello*, rappresenta un gruppo logico di spazi dei nomi, progetti o altri artefatti. È possibile tracciare le dipendenze che devono esistere nella progettazione. A differenza di un diagramma architettura tradizionale, è possibile verificare che le dipendenze effettive nel codice sorgente siano conformi alle dipendenze desiderate specificate. Includendo la convalida nel normale processo di compilazione in [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)], sarà possibile assicurare che il codice programma continui ad essere coerente con l'architettura del sistema anche in caso di modifiche future. Vedere [diagrammi di dipendenza:](../modeling/layer-diagrams-reference.md)informazioni di riferimento.

## <a name="how-to-design-or-update-your-app-with-dependency-diagrams"></a>Come progettare o aggiornare l'app con i diagrammi delle dipendenze

Nei passaggi seguenti viene fornita una panoramica dell'utilizzo dei diagrammi di dipendenza all'interno del processo di sviluppo. Le sezioni successive in questo argomento descrivono in modo più dettagliato ogni passaggio. Se si sviluppa una nuova progettazione, omettere i passaggi relativi al codice esistente.

> [!NOTE]
> I passaggi sono visualizzati in ordine approssimativo. Potrebbe essere necessario sovrapporre alcune attività, riordinarle per adattarle alla situazione specifica ed eseguirle di nuovo all'inizio di ogni iterazione nel progetto.

1. [Creare un diagramma delle dipendenze](#Create) per l'intera applicazione o per un livello al suo interno.

2. [Definire i livelli per rappresentare aree funzionali primarie o componenti](#CreateLayers) dell'applicazione. Assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se si dispone di una soluzione di Visual Studio, è possibile associare ogni livello a una raccolta di *elementi*, ad esempio progetti, spazi dei nomi, file e così via.

3. [Individuare le dipendenze esistenti tra i](#Generate) livelli.

4. [Modificare i livelli e le dipendenze](#EditArchitecture) per visualizzare la progettazione aggiornata che si desidera venga riflessa nel codice.

5. [Progettare nuove aree dell'applicazione](#NewAreas) creando livelli per rappresentare i blocchi o i componenti dell'architettura principale e definendo le dipendenze per mostrare il modo in cui ogni livello usa gli altri.

6. [Modificare il layout e l'aspetto del diagramma](#EditLayout) per illustrarlo con i colleghi.

7. [Convalidare il codice rispetto al diagramma delle dipendenze](#Validate) per evidenziare i conflitti tra il codice e l'architettura richiesta.

8. [Aggiornare il codice per conformità alla nuova architettura](#UpdateCode). Sviluppare in modo iterativo ed effettuare il refactoring del codice fino a ottenere una convalida senza conflitti.

9. [Includere la convalida dei livelli nel processo di compilazione](#BuildValidation) per garantire che il codice continui a rispettare la progettazione.

## <a name="create-a-dependency-diagram"></a><a name="Create"></a> Creazione di un diagramma delle dipendenze

È necessario creare un diagramma delle dipendenze all'interno di un progetto di modello. È possibile aggiungere un nuovo diagramma delle dipendenze a un progetto di modello esistente, creare un nuovo progetto di modello per il diagramma delle dipendenze oppure copiare un diagramma delle dipendenze esistente nello stesso progetto di modello.

> [!IMPORTANT]
> Non aggiungere, trascinare o copiare un diagramma delle dipendenze esistente da un progetto di modello a un altro progetto di modello o a un altro percorso nella soluzione. Un diagramma delle dipendenze copiato in questo modo avrà gli stessi riferimenti del diagramma originale, anche se si modifica il diagramma. Ciò impedirà il corretto funzionamento della convalida dei livelli e potrebbe provocare altri problemi, ad esempio la mancanza di elementi o altri errori durante il tentativo di apertura del diagramma.

Vedere [creare diagrammi di dipendenza dal codice](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="define-layers-to-represent-functional-areas-or-components"></a><a name="CreateLayers"></a> Definire i livelli per rappresentare aree funzionali o componenti

I livelli rappresentano gruppi logici di *artefatti*, ad esempio progetti, file di codice, spazi dei nomi, classi e metodi. È possibile creare livelli da artefatti da progetti Visual C# e Visual Basic oppure è possibile collegare specifiche o piani a un livello collegando documenti, ad esempio file di Word o presentazioni di PowerPoint. Ogni livello viene visualizzato come un rettangolo nel diagramma e viene indicato il numero di artefatti collegati a ogni livello. Un livello può contenere livelli annidati che descrivono attività più specifiche.

È in genere consigliabile assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se gli artefatti sono strettamente interdipendenti, posizionarli nello stesso livello. Se gli artefatti possono essere aggiornati separatamente o possono essere usati in applicazioni distinte, posizionarli in livelli diversi. Per informazioni sui modelli di livello, visitare il sito modelli & Practices all'indirizzo [http://go.microsoft.com/fwlink/?LinkId=145794](https://archive.codeplex.com/?p=apparch) .

> [!TIP]
> Esistono alcuni tipi di artefatti che è possibile collegare ai livelli ma che non supportano la convalida rispetto al diagramma delle dipendenze. Per verificare se l'artefatto supporta la convalida, aprire **Esplora livello** per esaminare la proprietà **convalida supportata** del collegamento dell'elemento. Vedere [individuare le dipendenze esistenti tra i livelli](#Generate).

Quando si aggiorna un'applicazione poco nota, è anche possibile creare mappe codice. Questi diagrammi consentono di individuare i motivi e le dipendenze durante l'esplorazione del codice. Usare Esplora soluzioni per esplorare spazi dei nomi e classi, che spesso corrispondono correttamente ai livelli esistenti. Assegnare questi elementi di codice ai livelli trascinandoli dal Esplora soluzioni ai diagrammi delle dipendenze. È quindi possibile usare i diagrammi delle dipendenze per aggiornare il codice e mantenerlo coerente con la progettazione.

Vedere:

- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)

- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)

## <a name="discover-existing-dependencies-between-layers"></a><a name="Generate"></a> Individuare le dipendenze esistenti tra i livelli

È presente una dipendenza quando un elemento associato a un livello dispone di un riferimento a un elemento associato a un altro livello. Ad esempio, una classe di un livello dichiara una variabile che dispone di una classe in un altro livello. Per individuare le dipendenze esistenti, è possibile decompilarle.

> [!NOTE]
> Non è possibile decompilare dipendenze per determinati tipi di elementi. Ad esempio, non è possibile decompilare dipendenze da e verso un livello collegato a un file di testo. Per verificare quali elementi presentano dipendenze che è possibile decodificare, fare clic con il pulsante destro del mouse su uno o più livelli, quindi scegliere **Visualizza collegamenti**. In **Esplora livello** esaminare la colonna **supporta la convalida** . Le dipendenze non verranno decodificate per gli artefatti per i quali la colonna Visualizza **false**.

### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Per decompilare le dipendenze esistenti tra i livelli

Selezionare un livello o più livelli, fare clic con il pulsante destro del mouse su un livello selezionato, quindi scegliere **Genera dipendenze**.

In genere vengono visualizzate alcune dipendenze che non dovrebbero esistere. È possibile modificare queste dipendenze per allinearle con la progettazione desiderata.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditArchitecture"></a> Modificare i livelli e le dipendenze per visualizzare la progettazione desiderata

Per descrivere le modifiche da apportare al sistema o all'architettura desiderata, attenersi alla procedura seguente per modificare il diagramma delle dipendenze. È anche possibile prendere in considerazione alcune modifiche relative al refactoring per migliorare la struttura del codice prima di estenderlo. Vedere [miglioramento della struttura del codice](#Improving).

|**To**|**Eseguire questi passaggi**|
|-|-|
|Eliminare una dipendenza che non dovrebbe essere presente|Fare clic sulla dipendenza, quindi premere **Canc**.|
|Modificare o limitare la direzione di una dipendenza|Impostarne la proprietà **Direction** .|
|Creare nuove dipendenze|Usare gli **strumenti di dipendenza e dipendenza** **bidirezionale** .<br /><br /> Per disegnare più dipendenze, fare doppio clic sullo strumento. Al termine, fare clic sullo strumento **puntatore** o premere **ESC** .|
|Specificare che gli elementi associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi nella proprietà delle **dipendenze dello spazio dei nomi non consentito** del livello. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli elementi associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi nella proprietà **Forbidden Namespaces** del livello. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi nella proprietà **obbligatoria Namespaces** del livello. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|

### <a name="improving-the-structure-of-the-code"></a><a name="Improving"></a> Miglioramento della struttura del codice

Le modifiche relative al refactoring sono miglioramenti che non influiscono sul comportamento dell'applicazione, ma contribuiscono a rendere il codice più semplice da modificare ed estendere nel futuro. Il codice ben strutturato ha una progettazione facile da astrarre in un diagramma delle dipendenze.

Ad esempio, se si crea un livello per ogni spazio dei nomi nel codice e quindi si decompilano le dipendenze, dovrebbe essere presente un insieme minimo di dipendenze unidirezionali tra i livelli. Se si crea un diagramma più dettagliato usando classi o metodi come livelli, il risultato dovrebbe avere le stesse caratteristiche.

In caso contrario, il codice sarà più difficile da modificare per tutta la sua vita e sarà meno adatto per la convalida usando i diagrammi delle dipendenze.

## <a name="design-new-areas-of-your-application"></a><a name="NewAreas"></a> Progettare nuove aree dell'applicazione

Quando si inizia a sviluppare un nuovo progetto o una nuova area in un nuovo progetto, è possibile tracciare livelli e dipendenze per semplificare l'identificazione dei componenti principali prima di iniziare a sviluppare il codice.

- **Mostra i modelli di architettura identificabili** nei diagrammi delle dipendenze, se possibile. Ad esempio, un diagramma delle dipendenze che descrive un'applicazione desktop può includere livelli quali la presentazione, la logica di dominio e l'archivio dati. Un diagramma delle dipendenze che copre una singola funzionalità all'interno di un'applicazione potrebbe avere livelli quali il modello, la visualizzazione e il controller. Per ulteriori informazioni su tali modelli, vedere [patterns & Practices: Application Architecture](https://archive.codeplex.com/?p=apparch).

- **Creare un elemento di codice per ogni livello** , ad esempio uno spazio dei nomi, una classe o un componente. In questo modo sarà più semplice seguire il codice e collegare gli elementi di codice ai livelli. Non appena si crea ogni artefatto, collegarlo al livello appropriato.

- **Non è necessario collegare la maggior parte delle classi e altri elementi ai livelli** perché rientrano in elementi più grandi, ad esempio gli spazi dei nomi già collegati ai livelli.

- Consente **di creare un nuovo diagramma per una nuova funzionalità**. In genere, saranno presenti uno o più diagrammi di dipendenza che descrivono l'intera applicazione. Se si progetta una nuova funzionalità nell'applicazione, non apportare aggiunte o modifiche ai diagrammi esistenti. Creare invece un diagramma personalizzato che rispecchia nuove parti del codice. I livelli nel nuovo diagramma possono includere livelli relativi a presentazione, logica di dominio e database per la nuova funzionalità.

     Quando si compila l'applicazione, il codice verrà convalidato rispetto al diagramma complessivo e al diagramma più dettagliato relativo alle funzionalità.

## <a name="edit-the-layout-for-presentation-and-discussion"></a><a name="EditLayout"></a> Modificare il layout per la presentazione e la discussione

Per semplificare l'identificazione di livelli e dipendenze o per esaminarli con i membri del team, modificare l'aspetto e il layout del diagramma nei modi seguenti:

- Modificare le dimensioni, le forme e le posizioni dei livelli.

- Cambiare i colori dei livelli e le dipendenze.

  - Selezionare uno o più livelli o dipendenze, fare clic con il pulsante destro del mouse su, quindi scegliere **Proprietà**. Nella finestra **Proprietà** modificare la proprietà **color** .

## <a name="validate-the-code-against-the-diagram"></a><a name="Validate"></a> Convalidare il codice rispetto al diagramma

Una volta modificato il diagramma, è possibile convalidarlo manualmente in qualsiasi momento o automaticamente a ogni compilazione.

Vedere:

- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)

- [Includere la convalida dei livelli nel processo di compilazione](#BuildValidation)

## <a name="update-the-code-to-conform-to-the-new-architecture"></a><a name="UpdateCode"></a> Aggiornare il codice per conformità alla nuova architettura

In genere, gli errori vengono visualizzati la prima volta che si convalida il codice rispetto a un diagramma delle dipendenze aggiornato. Gli errori possono avere cause diverse:

- Un artefatto viene assegnato al livello errato. In questo caso, spostare l'elemento.

- Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.

Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. Si tratta in genere di un processo iterativo. Per altre informazioni su questi errori, vedere [convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Quando si sviluppa o si effettua il refactoring del codice, è possibile che siano presenti nuovi elementi da collegare al diagramma delle dipendenze. È tuttavia possibile che ciò non sia necessario, ad esempio se sono presenti livelli che rappresentano spazi dei nomi esistenti e il nuovo codice aggiunge altri elementi a questi spazi dei nomi.

Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è consigliabile registrare un elemento di lavoro in Team Foundation. Per eseguire questa attività, vedere [convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md).

## <a name="include-layer-validation-in-the-build-process"></a><a name="BuildValidation"></a> Includere la convalida dei livelli nel processo di compilazione

Per assicurarsi che le modifiche future nel codice siano conformi ai diagrammi di dipendenza, includere la convalida dei livelli nel processo di compilazione standard della soluzione. Ogni volta che altri membri del team compilano la soluzione, eventuali differenze tra le dipendenze nel codice e il diagramma delle dipendenze verranno segnalate come errori di compilazione. Per altre informazioni sull'inclusione della convalida dei livelli nel processo di compilazione, vedere [convalidare il codice con diagrammi di dipendenza](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Vedi anche

- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Creare diagrammi delle dipendenze dal codice](../modeling/create-layer-diagrams-from-your-code.md)
