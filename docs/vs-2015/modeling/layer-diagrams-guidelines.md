---
title: 'Diagrammi livello: linee guida | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aee4ddc6062e465384921fa2632636c480736a77
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72646129"
---
# <a name="layer-diagrams-guidelines"></a>Diagrammi livello: linee guida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descrivere l'architettura dell'app a un livello elevato creando *diagrammi livello* in Visual Studio. Assicurarsi che il codice rimanga coerente con la progettazione convalidando il codice con un diagramma livello. È anche possibile includere la convalida dei livelli nel processo di compilazione. Vedere [video di Channel 9: progettare e convalidare l'architettura usando i diagrammi livello](http://go.microsoft.com/fwlink/?LinkID=252073).

 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="what-is-a-layer-diagram"></a>Informazioni sul diagramma livello
 Analogamente a un diagramma architettura tradizionale, un diagramma livello identifica i componenti principali o le unità funzionali della progettazione e le relative interdipendenze. Ogni nodo del diagramma, denominato *livello*, rappresenta un gruppo logico di spazi dei nomi, progetti o altri artefatti. È possibile tracciare le dipendenze che devono esistere nella progettazione. A differenza di un diagramma architettura tradizionale, è possibile verificare che le dipendenze effettive nel codice sorgente siano conformi alle dipendenze desiderate specificate. Includendo la convalida nel normale processo di compilazione in [!INCLUDE[esprtfs](../includes/esprtfs-md.md)], sarà possibile assicurare che il codice programma continui ad essere coerente con l'architettura del sistema anche in caso di modifiche future. Vedere [diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md).

## <a name="Update"></a>Come progettare o aggiornare l'app con diagrammi livello
 I passaggi seguenti offrono una panoramica di come usare i diagrammi livello nel processo di sviluppo. Le sezioni successive in questo argomento descrivono in modo più dettagliato ogni passaggio. Se si sviluppa una nuova progettazione, omettere i passaggi relativi al codice esistente.

> [!NOTE]
> I passaggi sono visualizzati in ordine approssimativo. Potrebbe essere necessario sovrapporre alcune attività, riordinarle per adattarle alla situazione specifica ed eseguirle di nuovo all'inizio di ogni iterazione nel progetto.

1. [Creare un diagramma livello](#Create) per l'intera applicazione o per un livello al suo interno.

2. [Definire i livelli per rappresentare aree funzionali primarie o componenti](#CreateLayers) dell'applicazione. Assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se si dispone di una soluzione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è possibile associare ogni livello a una raccolta di *elementi*, ad esempio progetti, spazi dei nomi, file e così via.

3. [Individuare le dipendenze esistenti tra i](#Generate) livelli.

4. [Modificare i livelli e le dipendenze](#EditArchitecture) per visualizzare la progettazione aggiornata che si desidera venga riflessa nel codice.

5. [Progettare nuove aree dell'applicazione](#NewAreas) creando livelli per rappresentare i blocchi o i componenti dell'architettura principale e definendo le dipendenze per mostrare il modo in cui ogni livello usa gli altri.

6. [Modificare il layout e l'aspetto del diagramma](#EditLayout) per illustrarlo con i colleghi.

7. [Convalidare il codice rispetto al diagramma livello](#Validate) per evidenziare i conflitti tra il codice e l'architettura necessaria.

8. [Aggiornare il codice per conformità alla nuova architettura](#UpdateCode). Sviluppare in modo iterativo ed effettuare il refactoring del codice fino a ottenere una convalida senza conflitti.

9. [Includere la convalida dei livelli nel processo di compilazione](#BuildValidation) per garantire che il codice continui a rispettare la progettazione.

## <a name="Create"></a>Creare un diagramma livello
 Un diagramma livello deve essere creato in un progetto di modello. È possibile aggiungere un nuovo diagramma livello a un progetto di modello esistente, creare un nuovo progetto di modello per il diagramma livello oppure copiare un diagramma livello esistente nello stesso progetto di modello.

> [!IMPORTANT]
> Non aggiungere, trascinare o copiare alcun diagramma livello esistente da un progetto di modello a un altro né a un altro percorso nella soluzione. Un diagramma livello copiato in questo modo includerà gli stessi riferimenti del diagramma originale, anche se si modifica il diagramma. Ciò impedirà il corretto funzionamento della convalida dei livelli e potrebbe provocare altri problemi, ad esempio la mancanza di elementi o altri errori durante il tentativo di apertura del diagramma.

 Vedere [creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md).

## <a name="CreateLayers"></a>Definire i livelli per rappresentare aree funzionali o componenti
 I livelli rappresentano gruppi logici di *artefatti*, ad esempio progetti, file di codice, spazi dei nomi, classi e metodi. È possibile creare livelli da artefatti da progetti Visual C# .NET e Visual Basic .NET oppure collegare specifiche o piani a un livello collegando documenti, quali file di Word o presentazioni di PowerPoint. Ogni livello viene visualizzato come un rettangolo nel diagramma e viene indicato il numero di artefatti collegati a ogni livello. Un livello può contenere livelli annidati che descrivono attività più specifiche.

 È in genere consigliabile assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se gli artefatti sono strettamente interdipendenti, posizionarli nello stesso livello. Se gli artefatti possono essere aggiornati separatamente o possono essere usati in applicazioni distinte, posizionarli in livelli diversi. Per informazioni sui modelli di livello, visitare il sito modelli & Practices [http://go.microsoft.com/fwlink/?LinkId=145794](http://go.microsoft.com/fwlink/?LinkId=145794).

> [!TIP]
> Alcuni tipi di artefatti possono essere collegati ai livelli ma non supportano la convalida rispetto al diagramma livello. Per verificare se l'artefatto supporta la convalida, aprire **Esplora livello** per esaminare la proprietà **convalida supportata** del collegamento dell'elemento. Vedere [individuare le dipendenze esistenti tra i livelli](#Generate).

 Quando si aggiorna un'applicazione poco nota, è anche possibile creare mappe codice. Questi diagrammi consentono di individuare i motivi e le dipendenze durante l'esplorazione del codice. Usare Esplora soluzioni per esplorare spazi dei nomi e classi, che spesso corrispondono correttamente ai livelli esistenti. Assegnare questi elementi di codice ai livelli trascinandoli da Esplora soluzioni in diagrammi livello. È quindi possibile usare i diagrammi livello per aggiornare il codice e mantenerlo coerente con la progettazione.

 Vedere:

- [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)

- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)

## <a name="Generate"></a>Individuare le dipendenze esistenti tra i livelli
 È presente una dipendenza quando un elemento associato a un livello dispone di un riferimento a un elemento associato a un altro livello. Ad esempio, una classe di un livello dichiara una variabile che dispone di una classe in un altro livello. Per individuare le dipendenze esistenti, è possibile decompilarle.

> [!NOTE]
> Non è possibile decompilare dipendenze per determinati tipi di elementi. Ad esempio, non è possibile decompilare dipendenze da e verso un livello collegato a un file di testo. Per verificare quali elementi presentano dipendenze che è possibile decodificare, fare clic con il pulsante destro del mouse su uno o più livelli, quindi scegliere **Visualizza collegamenti**. In **Esplora livello**esaminare la colonna **supporta la convalida** . Le dipendenze non verranno decodificate per gli artefatti per i quali la colonna Visualizza **false**.

#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Per decompilare le dipendenze esistenti tra i livelli

- Selezionare un livello o più livelli, fare clic con il pulsante destro del mouse su un livello selezionato, quindi scegliere **Genera dipendenze**.

  In genere vengono visualizzate alcune dipendenze che non dovrebbero esistere. È possibile modificare queste dipendenze per allinearle con la progettazione desiderata.

## <a name="EditArchitecture"></a>Modificare i livelli e le dipendenze per visualizzare la progettazione desiderata
 Per descrivere le modifiche da apportare al sistema o all'architettura desiderata, eseguire i passaggi seguenti per modificare il diagramma livello. È anche possibile prendere in considerazione alcune modifiche relative al refactoring per migliorare la struttura del codice prima di estenderlo. Vedere [miglioramento della struttura del codice](#Improving).

|**Per**|**Eseguire questi passaggi**|
|------------|-----------------------------|
|Eliminare una dipendenza che non dovrebbe essere presente|Fare clic sulla dipendenza, quindi premere **Canc**.|
|Modificare o limitare la direzione di una dipendenza|Impostarne la proprietà **Direction** .|
|Creare nuove dipendenze|Usare gli **strumenti di dipendenza e dipendenza** **bidirezionale** .<br /><br /> Per disegnare più dipendenze, fare doppio clic sullo strumento. Al termine, fare clic sullo strumento **puntatore** o premere **ESC** .|
|Specificare che gli elementi associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi nella proprietà delle **dipendenze dello spazio dei nomi non consentito** del livello. Utilizzare un punto e virgola ( **;** ) per separare gli spazi dei nomi.|
|Specificare che gli elementi associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi nella proprietà **Forbidden Namespaces** del livello. Utilizzare un punto e virgola ( **;** ) per separare gli spazi dei nomi.|
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi nella proprietà **obbligatoria Namespaces** del livello. Utilizzare un punto e virgola ( **;** ) per separare gli spazi dei nomi.|

### <a name="Improving"></a>Miglioramento della struttura del codice
 Le modifiche relative al refactoring sono miglioramenti che non influiscono sul comportamento dell'applicazione, ma contribuiscono a rendere il codice più semplice da modificare ed estendere nel futuro. Il codice ben strutturato è progettato in modo da facilitarne l'astrazione in un diagramma livello.

 Ad esempio, se si crea un livello per ogni spazio dei nomi nel codice e quindi si decompilano le dipendenze, dovrebbe essere presente un insieme minimo di dipendenze unidirezionali tra i livelli. Se si crea un diagramma più dettagliato usando classi o metodi come livelli, il risultato dovrebbe avere le stesse caratteristiche.

 In caso contrario, la modifica del codice risulterà più difficile e il codice sarà meno idoneo alla convalida tramite i diagrammi livello.

## <a name="NewAreas"></a>Progettare nuove aree dell'applicazione
 Quando si inizia a sviluppare un nuovo progetto o una nuova area in un nuovo progetto, è possibile tracciare livelli e dipendenze per semplificare l'identificazione dei componenti principali prima di iniziare a sviluppare il codice.

- **Mostra i modelli di architettura identificabili** nei diagrammi livello, se possibile. Ad esempio, un diagramma livello che descrive un'applicazione desktop può includere livelli quali Presentazione, Logica di dominio e Archivio dati. Un diagramma livello che riguarda una singola funzionalità in un'applicazione può includere livelli quali Modello, Visualizzazione e Controller. Per ulteriori informazioni su tali modelli, vedere [patterns & Practices: Application Architecture](http://go.microsoft.com/fwlink/?LinkId=145794).

     Se si creano spesso modelli di questo tipo, creare uno strumento personalizzato. Vedere [definire un elemento personalizzato della casella degli strumenti di modellazione](../modeling/define-a-custom-modeling-toolbox-item.md).

- **Creare un elemento di codice per ogni livello** , ad esempio uno spazio dei nomi, una classe o un componente. In questo modo sarà più semplice seguire il codice e collegare gli elementi di codice ai livelli. Non appena si crea ogni artefatto, collegarlo al livello appropriato.

- **Non è necessario collegare la maggior parte delle classi e altri elementi ai livelli** perché rientrano in elementi più grandi, ad esempio gli spazi dei nomi già collegati ai livelli.

- Consente **di creare un nuovo diagramma per una nuova funzionalità**. In genere, saranno presenti uno o più diagrammi livello che descrivono l'intera applicazione. Se si progetta una nuova funzionalità nell'applicazione, non apportare aggiunte o modifiche ai diagrammi esistenti. Creare invece un diagramma personalizzato che rispecchia nuove parti del codice. I livelli nel nuovo diagramma possono includere livelli relativi a presentazione, logica di dominio e database per la nuova funzionalità.

     Quando si compila l'applicazione, il codice verrà convalidato rispetto al diagramma complessivo e al diagramma più dettagliato relativo alle funzionalità.

## <a name="EditLayout"></a>Modificare il layout per la presentazione e la discussione
 Per semplificare l'identificazione di livelli e dipendenze o per esaminarli con i membri del team, modificare l'aspetto e il layout del diagramma nei modi seguenti:

- Modificare le dimensioni, le forme e le posizioni dei livelli.

- Cambiare i colori dei livelli e le dipendenze.

  - Selezionare uno o più livelli o dipendenze, fare clic con il pulsante destro del mouse su, quindi scegliere **Proprietà**. Nella finestra **Proprietà** modificare la proprietà **color** .

## <a name="Validate"></a>Convalidare il codice rispetto al diagramma
 Dopo avere modificato il diagramma, sarà possibile convalidarlo manualmente rispetto al codice in qualsiasi momento oppure automaticamente ogni volta che si esegue una compilazione locale o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].

 Vedere:

- [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)

- [Includere la convalida dei livelli nel processo di compilazione](#BuildValidation)

## <a name="UpdateCode"></a>Aggiornare il codice per conformità alla nuova architettura
 In genere, alla prima convalida del codice rispetto a un diagramma livello aggiornato vengono visualizzati errori. Gli errori possono avere cause diverse:

- Un artefatto viene assegnato al livello errato. In questo caso, spostare l'elemento.

- Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.

  Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. Si tratta in genere di un processo iterativo. Per altre informazioni su questi errori, vedere [convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md).

> [!NOTE]
> Quando si sviluppa codice o se ne effettua il refactoring, è possibile che siano presenti nuovi artefatti da collegare al diagramma livello. È tuttavia possibile che ciò non sia necessario, ad esempio se sono presenti livelli che rappresentano spazi dei nomi esistenti e il nuovo codice aggiunge altri elementi a questi spazi dei nomi.

 Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è buona norma registrare un elemento di lavoro in [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Per eseguire questa attività, vedere [convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md).

## <a name="BuildValidation"></a>Includere la convalida dei livelli nel processo di compilazione
 Per assicurare che eventuali modifiche future al codice siano conformi ai diagrammi livello, includere la convalida dei livelli nel processo di compilazione standard della soluzione. Quando altri membri del team compilano la soluzione, eventuali differenze tra le dipendenze nel codice e il diagramma livello verranno segnalate come errori di compilazione. Per altre informazioni sull'inclusione della convalida dei livelli nel processo di compilazione, vedere [convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md).

## <a name="see-also"></a>Vedere anche
 [Diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md) [creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)
