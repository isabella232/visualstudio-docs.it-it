---
title: 'Diagrammi livello: Linee guida | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 2903bec7-a93b-46a6-aac6-994ac4f3f1a7
caps.latest.revision: 57
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2307bb0bfbc366ab1d2d1636f5e289ac0f4b4bfa
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49202579"
---
# <a name="layer-diagrams-guidelines"></a>Diagrammi livello: linee guida
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Descrivere l'architettura dell'app ad alto livello creando *diagrammi livello* in Visual Studio. Assicurarsi che il codice rimanga coerente con la progettazione convalidando il codice con un diagramma livello. È anche possibile includere la convalida dei livelli nel processo di compilazione. Visualizzare [Video di Channel 9: progettazione e convalidare l'architettura utilizzando i diagrammi livello](http://go.microsoft.com/fwlink/?LinkID=252073).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="what-is-a-layer-diagram"></a>Informazioni sul diagramma livello  
 Analogamente a un diagramma architettura tradizionale, un diagramma livello identifica i componenti principali o le unità funzionali della progettazione e le relative interdipendenze. Ogni nodo nel diagramma, denominato un *layer*, rappresenta un gruppo logico di spazi dei nomi, progetti o altri elementi. È possibile tracciare le dipendenze che devono esistere nella progettazione. A differenza di un diagramma architettura tradizionale, è possibile verificare che le dipendenze effettive nel codice sorgente siano conformi alle dipendenze desiderate specificate. Includendo la convalida nel normale processo di compilazione in [!INCLUDE[esprtfs](../includes/esprtfs-md.md)], sarà possibile assicurare che il codice programma continui ad essere coerente con l'architettura del sistema anche in caso di modifiche future. Visualizzare [diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md).  
  
##  <a name="Update"></a> Come progettare o aggiornare l'applicazione con diagrammi livello  
 I passaggi seguenti offrono una panoramica di come usare i diagrammi livello nel processo di sviluppo. Le sezioni successive in questo argomento descrivono in modo più dettagliato ogni passaggio. Se si sviluppa una nuova progettazione, omettere i passaggi relativi al codice esistente.  
  
> [!NOTE]
>  I passaggi sono visualizzati in ordine approssimativo. Potrebbe essere necessario sovrapporre alcune attività, riordinarle per adattarle alla situazione specifica ed eseguirle di nuovo all'inizio di ogni iterazione nel progetto.  
  
1.  [Creare un diagramma livello](#Create) per l'intera applicazione o per un livello all'interno di esso.  
  
2.  [Definire livelli per rappresentare aree funzionali primarie o componenti](#CreateLayers) dell'applicazione. Assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se si dispone di un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] soluzione, è possibile associare ogni livello a una raccolta di *artefatti*, ad esempio progetti, gli spazi dei nomi, i file e così via.  
  
3.  [Individuare le dipendenze esistenti](#Generate) tra livelli.  
  
4.  [Modificare i livelli e dipendenze](#EditArchitecture) per mostrare l'aggiornamento che si vuole rispecchiare nel codice di progettazione.  
  
5.  [Progettare nuove aree dell'applicazione](#NewAreas) la creazione di livelli per rappresentare i blocchi di architettura principali o i componenti e definendo le dipendenze per mostrare come ogni livello Usa gli altri.  
  
6.  [Modificare il layout e l'aspetto del diagramma](#EditLayout) per semplificarne l'analisi con i colleghi.  
  
7.  [Convalidare il codice rispetto al diagramma livello](#Validate) per evidenziare i conflitti tra il codice e l'architettura necessaria.  
  
8.  [Aggiornare il codice per garantire la conformità alla nuova architettura](#UpdateCode). Sviluppare in modo iterativo ed effettuare il refactoring del codice fino a ottenere una convalida senza conflitti.  
  
9. [Includere la convalida dei livelli nel processo di compilazione](#BuildValidation) per assicurarsi che il codice sia sempre conforme alla progettazione.  
  
##  <a name="Create"></a> Creare un diagramma livello  
 Un diagramma livello deve essere creato in un progetto di modello. È possibile aggiungere un nuovo diagramma livello a un progetto di modello esistente, creare un nuovo progetto di modello per il diagramma livello oppure copiare un diagramma livello esistente nello stesso progetto di modello.  
  
> [!IMPORTANT]
>  Non aggiungere, trascinare o copiare alcun diagramma livello esistente da un progetto di modello a un altro né a un altro percorso nella soluzione. Un diagramma livello copiato in questo modo includerà gli stessi riferimenti del diagramma originale, anche se si modifica il diagramma. Ciò impedirà il corretto funzionamento della convalida dei livelli e potrebbe provocare altri problemi, ad esempio la mancanza di elementi o altri errori durante il tentativo di apertura del diagramma.  
  
 Visualizzare [creare i diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md).  
  
##  <a name="CreateLayers"></a> Definire livelli per rappresentare aree funzionali o componenti  
 I livelli rappresentano gruppi logici di *artefatti*, ad esempio progetti, file di codice, gli spazi dei nomi, classi e metodi. È possibile creare livelli da artefatti da progetti Visual C# .NET e Visual Basic .NET oppure collegare specifiche o piani a un livello collegando documenti, quali file di Word o presentazioni di PowerPoint. Ogni livello viene visualizzato come un rettangolo nel diagramma e viene indicato il numero di elementi collegati a ogni livello. Un livello può contenere livelli annidati che descrivono attività più specifiche.  
  
 È in genere consigliabile assegnare a questi livelli nomi conformi alla relativa funzione, ad esempio "Presentazione" o "Servizi". Se gli elementi sono strettamente interdipendenti, posizionarli nello stesso livello. Se gli artefatti possono essere aggiornati separatamente o possono essere usati in applicazioni distinte, posizionarli in livelli diversi. Per altre informazioni sui modelli di livello, visitare il sito modelli e procedure all'indirizzo [ http://go.microsoft.com/fwlink/?LinkId=145794 ](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
> [!TIP]
>  Alcuni tipi di elementi possono essere collegati ai livelli ma non supportano la convalida rispetto al diagramma livello. Per vedere se l'elemento supporta la convalida, aprire **Esplora livello** esaminare le **supporta la convalida** proprietà del collegamento dell'artefatto. Visualizzare [individua le dipendenze esistenti tra livelli](#Generate).  
  
 Quando si aggiorna un'applicazione poco nota, è anche possibile creare mappe codice. Questi diagrammi consentono di individuare i motivi e le dipendenze durante l'esplorazione del codice. Usare Esplora soluzioni per esplorare spazi dei nomi e classi, che spesso corrispondono correttamente ai livelli esistenti. Assegnare questi elementi di codice ai livelli trascinandoli da Esplora soluzioni in diagrammi livello. È quindi possibile usare i diagrammi livello per aggiornare il codice e mantenerlo coerente con la progettazione.  
  
 Vedere:  
  
-   [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)  
  
-   [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)  
  
-   [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)  
  
##  <a name="Generate"></a> Individuare le dipendenze esistenti tra livelli  
 È presente una dipendenza quando un artefatto associato a un livello dispone di un riferimento a un artefatto associato a un altro livello. Ad esempio, una classe di un livello dichiara una variabile che dispone di una classe in un altro livello. Per individuare le dipendenze esistenti, è possibile decompilarle.  
  
> [!NOTE]
>  Non è possibile decompilare dipendenze per determinati tipi di elementi. Ad esempio, non è possibile decompilare dipendenze da e verso un livello collegato a un file di testo. Per vedere quali artefatti sono associate dipendenze che è possibile decompilare, fare doppio clic su uno o più livelli e quindi fare clic su **Visualizza collegamenti**. Nelle **Esplora livello**, esaminare le **supporta la convalida** colonna. Le dipendenze non verranno decompilate per artefatti per cui questa colonna viene visualizzato **False**.  
  
#### <a name="to-reverse-engineer-existing-dependencies-between-layers"></a>Per decompilare le dipendenze esistenti tra i livelli  
  
-   Selezionare uno o più livelli, fare doppio clic su un livello selezionato e quindi fare clic su **genera dipendenze**.  
  
 In genere vengono visualizzate alcune dipendenze che non dovrebbero esistere. È possibile modificare queste dipendenze per allinearle con la progettazione desiderata.  
  
##  <a name="EditArchitecture"></a> Modificare livelli e dipendenze per visualizzare la progettazione desiderata  
 Per descrivere le modifiche da apportare al sistema o all'architettura desiderata, eseguire i passaggi seguenti per modificare il diagramma livello. È anche possibile prendere in considerazione alcune modifiche relative al refactoring per migliorare la struttura del codice prima di estenderlo. Visualizzare [miglioramento della struttura del codice](#Improving).  
  
|**Per**|**Eseguire questi passaggi**|  
|------------|-----------------------------|  
|Eliminare una dipendenza che non dovrebbe essere presente|Fare clic sulla dipendenza e quindi premere **Elimina**.|  
|Modificare o limitare la direzione di una dipendenza|Impostare relativi **direzione** proprietà.|  
|Creare nuove dipendenze|Usare la **Dependency** e **dipendenza bidirezionale** strumenti.<br /><br /> Per disegnare più dipendenze, fare doppio clic sullo strumento. Al termine, fare clic sui **puntatore** degli strumenti oppure premere la **ESC** chiave.|  
|Specificare che gli artefatti associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **dipendenze Namespace non è consentito** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **Forbidden Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi del livello **Required Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
  
###  <a name="Improving"></a> Miglioramento della struttura del codice  
 Le modifiche relative al refactoring sono miglioramenti che non influiscono sul comportamento dell'applicazione, ma contribuiscono a rendere il codice più semplice da modificare ed estendere nel futuro. Il codice ben strutturato è progettato in modo da facilitarne l'astrazione in un diagramma livello.  
  
 Ad esempio, se si crea un livello per ogni spazio dei nomi nel codice e quindi si decompilano le dipendenze, dovrebbe essere presente un insieme minimo di dipendenze unidirezionali tra i livelli. Se si crea un diagramma più dettagliato usando classi o metodi come livelli, il risultato dovrebbe avere le stesse caratteristiche.  
  
 In caso contrario, la modifica del codice risulterà più difficile e il codice sarà meno idoneo alla convalida tramite i diagrammi livello.  
  
##  <a name="NewAreas"></a> Progettare nuove aree dell'applicazione  
 Quando si inizia a sviluppare un nuovo progetto o una nuova area in un nuovo progetto, è possibile tracciare livelli e dipendenze per semplificare l'identificazione dei componenti principali prima di iniziare a sviluppare il codice.  
  
-   **Visualizzare i modelli di architettura identificabili** nei diagrammi livello, se possibile. Ad esempio, un diagramma livello che descrive un'applicazione desktop può includere livelli quali Presentazione, Logica di dominio e Archivio dati. Un diagramma livello che riguarda una singola funzionalità in un'applicazione può includere livelli quali Modello, Visualizzazione e Controller. Per altre informazioni su tali modelli, vedere [modelli e procedure: architettura dell'applicazione](http://go.microsoft.com/fwlink/?LinkId=145794).  
  
     Se si creano spesso modelli di questo tipo, creare uno strumento personalizzato. Visualizzare [definire un oggetto personalizzato elemento della casella degli strumenti di modellazione](../modeling/define-a-custom-modeling-toolbox-item.md).  
  
-   **Creare un elemento di codice per ogni livello** come spazio dei nomi, classe o componente. In questo modo sarà più semplice seguire il codice e collegare gli artefatti di codice ai livelli. Non appena si crea ogni artefatto, collegarlo al livello appropriato.  
  
-   **Non è necessario collegare la maggior parte delle classi e altri elementi ai livelli** poiché si trovano all'interno di elementi più grandi quali spazi dei nomi che sono già stati collegati ai livelli.  
  
-   **Creare un nuovo diagramma di una nuova caratteristica**. In genere, saranno presenti uno o più diagrammi livello che descrivono l'intera applicazione. Se si progetta una nuova funzionalità nell'applicazione, non apportare aggiunte o modifiche ai diagrammi esistenti. Creare invece un diagramma personalizzato che rispecchia nuove parti del codice. I livelli nel nuovo diagramma possono includere livelli relativi a presentazione, logica di dominio e database per la nuova funzionalità.  
  
     Quando si compila l'applicazione, il codice verrà convalidato rispetto al diagramma complessivo e al diagramma più dettagliato relativo alle funzionalità.  
  
##  <a name="EditLayout"></a> Modificare il layout per la presentazione e discussione  
 Per semplificare l'identificazione di livelli e dipendenze o per esaminarli con i membri del team, modificare l'aspetto e il layout del diagramma nei modi seguenti:  
  
-   Modificare le dimensioni, le forme e le posizioni dei livelli.  
  
-   Cambiare i colori dei livelli e le dipendenze.  
  
    -   Selezionare uno o più livelli o dipendenze, pulsante destro del mouse e quindi fare clic su **proprietà**. Nel **delle proprietà** finestra, modificare il **colore** proprietà.  
  
##  <a name="Validate"></a> Convalidare il codice rispetto al diagramma  
 Dopo avere modificato il diagramma, sarà possibile convalidarlo manualmente rispetto al codice in qualsiasi momento oppure automaticamente ogni volta che si esegue una compilazione locale o [!INCLUDE[esprbuild](../includes/esprbuild-md.md)].  
  
 Vedere:  
  
-   [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)  
  
-   [Includere la convalida dei livelli nel processo di compilazione](#BuildValidation)  
  
##  <a name="UpdateCode"></a> Aggiornare il codice per garantire la conformità alla nuova architettura  
 In genere, alla prima convalida del codice rispetto a un diagramma livello aggiornato vengono visualizzati errori. Gli errori possono avere cause diverse:  
  
-   Un elemento viene assegnato al livello errato. In questo caso, spostare l'elemento.  
  
-   Un elemento, ad esempio una classe, usa un'altra classe in un modo che causa conflitti con l'architettura. In questo caso, eseguire il refactoring del codice per rimuovere la dipendenza.  
  
 Per risolvere gli errori, aggiornare il codice finché non verranno più visualizzati errori di convalida. Si tratta in genere di un processo iterativo. Per altre informazioni su questi errori, vedere [convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md).  
  
> [!NOTE]
>  Quando si sviluppa codice o se ne effettua il refactoring, è possibile che siano presenti nuovi artefatti da collegare al diagramma livello. È tuttavia possibile che ciò non sia necessario, ad esempio se sono presenti livelli che rappresentano spazi dei nomi esistenti e il nuovo codice aggiunge altri elementi a questi spazi dei nomi.  
  
 Durante il processo di sviluppo, potrebbe essere necessario eliminare alcuni conflitti segnalati durante la convalida. Ad esempio, è possibile eliminare gli errori che sono già stati corretti o che non sono attinenti allo scenario in questione. Quando si elimina un errore, è buona norma registrare un elemento di lavoro in [!INCLUDE[esprfound](../includes/esprfound-md.md)]. Per eseguire questa attività, vedere [convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md).  
  
##  <a name="BuildValidation"></a> Includere la convalida dei livelli nel processo di compilazione  
 Per assicurare che eventuali modifiche future al codice siano conformi ai diagrammi livello, includere la convalida dei livelli nel processo di compilazione standard della soluzione. Quando altri membri del team compilano la soluzione, eventuali differenze tra le dipendenze nel codice e il diagramma livello verranno segnalate come errori di compilazione. Per altre informazioni sull'inclusione della convalida dei livelli nel processo di compilazione, vedere [convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Diagrammi livello: riferimento](../modeling/layer-diagrams-reference.md)   
 [Creare diagrammi livello dal codice](../modeling/create-layer-diagrams-from-your-code.md)



