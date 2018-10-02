---
title: Creare diagrammi delle dipendenze dal codice
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- architecture, dependency diagrams
- dependency diagrams
- diagrams - modeling, layer
- constraints, architectural
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 511234a1a577bbad87fa9ceecc2afe34945cce5c
ms.sourcegitcommit: ad5fb20f18b23eb8bd2568717f61edc6b7eee5e7
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/01/2018
ms.locfileid: "47860114"
---
# <a name="create-dependency-diagrams-from-your-code"></a>Creare diagrammi delle dipendenze dal codice

Per visualizzare l'architettura di alto livello, logica del sistema software, creare un *diagramma delle dipendenze* in Visual Studio. Per assicurarsi che il codice rimanga coerente con questa progettazione, convalidare il codice con un diagramma delle dipendenze. È possibile creare diagrammi delle dipendenze per progetti Visual c# e Visual Basic. Per informazioni su quali edizioni di Visual Studio supportano questa funzionalità, vedere [supporto di edizione per un'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

![Creare un diagramma delle dipendenze](../modeling/media/layerdiagramvisualizecode.png)

Un diagramma di dipendenza consente di organizzare gli elementi di soluzione di Visual Studio in gruppi logici astratti, chiamati *livelli*. È possibile utilizzare i livelli per descrivere le attività principali che tali artefatti eseguono oppure i componenti principali del sistema. Ogni livello può contenere altri livelli che descrivono attività più dettagliate. È inoltre possibile specificare il desiderate o esistenti *dipendenze* tra livelli. Tali dipendenze, rappresentate come frecce, mostrano quali livelli possono utilizzare o utilizzano attualmente la funzionalità rappresentata da altri livelli. Per gestire controllo a livello di architettura nel codice, mostrare le dipendenze desiderate nel diagramma, quindi convalidare il codice in base al diagramma.

[Video: Convalidare le dipendenze dell'architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="CreateDiagram"></a> Creare un diagramma delle dipendenze

Prima di creare un diagramma delle dipendenze, assicurarsi che la soluzione contiene un progetto di modellazione.

> [!IMPORTANT]
> Non aggiungere, trascinare o copiare alcun diagramma di dipendenza esistente da un progetto di modellazione a un altro progetto di modellazione o in un'altra posizione nella soluzione. In questo modo i riferimenti del diagramma originale verranno mantenuti, anche se si modifica il diagramma. In caso contrario, il funzionamento della convalida dei livelli non sarà corretto e potrebbero verificarsi altri problemi, quali la mancanza di elementi o altri errori quando si tenta di aprire il diagramma.
>
> Al contrario, aggiungere un nuovo diagramma di dipendenza al progetto di modellazione. copiare gli elementi dal diagramma di origine al nuovo diagramma Salvare il progetto di modellazione sia il nuovo diagramma di dipendenza.

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>Aggiungere un nuovo diagramma di dipendenza a un progetto di modellazione

> [!NOTE]
> I diagrammi delle dipendenze non sono supportati per i progetti .NET Core in Visual Studio 2017.

1.  Nel **Architecture** menu, scegliere **nuovo diagramma di dipendenza**.

2.  Sotto **modelli**, scegliere **diagramma delle dipendenze**.

3.  Assegnare un nome al diagramma.

4.  Nelle **Aggiungi a progetto di modello**, individuare e selezionare un progetto di modellazione esistente nella soluzione.

     oppure

     Scegli **creare un nuovo progetto di modellazione** per aggiungere un nuovo progetto di modellazione alla soluzione.

    > [!NOTE]
    > Il diagramma di dipendenza deve esistere all'interno di un progetto di modellazione. È tuttavia possibile collegarlo a elementi in qualsiasi punto della soluzione.

5.  Assicurarsi di salvare il progetto di modellazione sia nel diagramma delle dipendenze.

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Trascinare e rilasciare, oppure copiare e incollare, da una mappa codice

1. Generare una mappa codici per la soluzione tramite il **architettura** menu.

2. È possibile applicare un filtro mappa del codice per rimuovere le cartelle della soluzione e "Gli asset di Test" Se si desidera applicare le dipendenze nel codice del prodotto.

3. Nella mappa del codice generato, rimuovere il nodo "External", o espandere in modo da visualizzare gli assembly esterni, a seconda che si voglia imporre dipendenze dello spazio dei nomi ed eliminare gli assembly non obbligatori dalla mappa del codice.

4. Creare un nuovo diagramma di dipendenza per la soluzione tramite il **architettura** menu

5. Selezionare tutti i nodi nella mappa del codice (usare _Ctrl_ + _oggetto_, o utilizzare il rettangolo di selezione premendo la _MAIUSC_ chiave prima di fare clic su, trascinare e rilasciare.

6. Trascinamento e rilascio, o una copia e Incolla, gli elementi selezionati per il nuovo diagramma di convalida delle dipendenze.

7. Mostra l'architettura di app corrente. Decidere quale sia l'architettura e modificare di conseguenza il diagramma delle dipendenze.

![Diagramma di dipendenze generato da una mappa codice](media/dependency-validation-01.png)

## <a name="CreateLayers"></a> Creare livelli da artefatti
 È possibile creare livelli da elementi presenti in una soluzione di Visual Studio, ad esempio progetti, file di codice, spazi dei nomi, classi e metodi. In questo modo vengono creati automaticamente collegamenti tra livelli ed elementi, che vengono inclusi nel processo di convalida dei livelli.

 È inoltre possibile collegare livelli a elementi che non supportano la convalida, ad esempio documenti Word o presentazioni PowerPoint, in modo da associare un livello con specifiche o piani. È anche possibile collegare livelli a file di progetti condivisi tra più applicazioni, ma il processo di convalida non includerà tali livelli, che vengano visualizzati con nomi generici come "Livello 1" e "Livello 2".

 Per vedere se un elemento collegato supporta la convalida, aprire **Esplora livello** ed esaminare le **supporta la convalida** proprietà dell'elemento. Visualizzare [gestione dei collegamenti agli elementi](#Managing).

|**Per**|**Seguire questi passaggi**|
|------------|----------------------------|
|Creare un livello per un solo artefatto|<ol><li>Trascinare l'elemento nel diagramma delle dipendenze da queste origini:<br /><br /> <ul><li>**Esplora soluzioni**<br /><br />         Ad esempio, è possibile trascinare file o progetti.</li><li>Mappe codice<br /><br />         Visualizzare [mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md) e [usare le mappe codice per il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Visualizzazione classi** o **Visualizzatore oggetti**</li></ul><br />     Nel diagramma viene visualizzato un livello collegato all'artefatto.</li><li>Rinominare il livello per riflettere le responsabilità del codice o degli artefatti associati.</li></ol> **Importante:** si trascinano file binari per il diagramma delle dipendenze non vengono aggiunti automaticamente i riferimenti al progetto di modellazione. ma è necessario aggiungere manualmente i file binari desiderati per convalidare il progetto di modellazione. **Per aggiungere i file binari al progetto di modellazione** <ol><li>Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto di modellazione e quindi scegliere **Aggiungi elemento esistente**.</li><li>Nel **Aggiungi elemento esistente** della finestra di dialogo selezionare i file binari, selezionarli e quindi scegliere **OK**.     I file binari verranno visualizzati nel progetto di modellazione.</li><li>Nelle **Esplora soluzioni**, scegliere un file binario che aggiunto e quindi premere **F4** per aprire il **proprietà** finestra.</li><li>Per ogni file binario, impostare il **Build Action** proprietà **Validate**.</li></ol>|
|Creare un solo livello per tutti gli artefatti selezionati|Trascinare tutti gli artefatti nel diagramma delle dipendenze nello stesso momento.<br /><br /> Nel diagramma viene visualizzato un livello collegato a tutti gli artefatti.|
|Creare un livello per ogni artefatto selezionato|Premere e tenere premuto il **MAIUSC** mentre si trascinano contemporaneamente tutti gli elementi nel diagramma delle dipendenze. **Nota:** se si usano i **MAIUSC** chiave per selezionare un intervallo di elementi, rilasciare il tasto dopo avere selezionato gli artefatti. Premerlo e tenerlo premuto nuovamente quando si trascinano gli artefatti nel diagramma. <br /><br /> Per ogni elemento nel diagramma viene visualizzato un livello collegato a ciascun elemento.|
|Aggiungere un elemento a un livello|Trascinare l'elemento sul livello.|
|Creare un nuovo livello non collegato|Nel **della casella degli strumenti**, espandere il **diagramma delle dipendenze** sezione e quindi trascinare un' **livello** nel diagramma delle dipendenze.<br /><br /> Per aggiungere più livelli, fare doppio clic sullo strumento. Al termine, scegliere il **puntatore** degli strumenti oppure premere la **ESC** chiave.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per il diagramma delle dipendenze, scegliere **Add**, quindi scegliere **Layer**.|
|Creare livelli annidati|Trascinare un livello esistente su un altro livello.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per un livello, scegliere **Add**, quindi scegliere **Layer**.|
|Creare un nuovo livello contenente due o più livelli esistenti|Selezionare i livelli, aprire il menu di scelta rapida per la selezione e quindi scegliere **gruppo**.|
|Modificare il colore di un livello|Impostare relativi **colore** proprietà sul colore desiderato.|
|Specificare che gli artefatti associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **Forbidden Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli artefatti associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **dipendenze Namespace non è consentito** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi del livello **Required Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|

 Il numero raffigurato sul livello indica il numero di artefatti a esso collegati. Tuttavia, nell'interpretazione di tale numero, considerare quanto segue:

-   Se un livello è collegato a un elemento contenente altri elementi, ma non è collegato direttamente ad altri elementi, il numero include solo l'elemento collegato. Tuttavia, gli altri elementi vengono inclusi per l'analisi durante la convalida dei livelli.

     Ad esempio, se un livello è collegato a un solo spazio dei nomi, il numero degli elementi collegati sarà 1, anche se lo spazio dei nomi contiene classi. Se il livello è collegato anche a ciascuna classe dello spazio dei nomi, il numero includerà le classi collegate.

-   Se un livello contiene altri livelli collegati a elementi, anche il livello contenitore sarà collegato a tali elementi nonostante il numero raffigurato sul livello contenitore non includa quegli elementi.

## <a name="Managing"></a> Gestire collegamenti tra livelli e artefatti

1.  Nel diagramma delle dipendenze, aprire il menu di scelta rapida per il livello e quindi scegliere **Visualizza collegamenti**.

     **Esplora livello** vengono visualizzati i collegamenti dell'artefatto per il livello selezionato.

2.  Usare le seguenti attività per gestire tali collegamenti:

|**Per**|**In Esplora livello**|
|------------|---------------------------|
|Eliminare il collegamento tra il livello e un artefatto|Aprire il menu di scelta rapida per il collegamento all'artefatto e quindi scegliere **Elimina**.|
|Spostare il collegamento da un livello a un altro|Trascinare il collegamento dell'elemento in un livello esistente del diagramma.<br /><br /> -oppure-<br /><br /> 1.  Aprire il menu di scelta rapida per il collegamento all'artefatto e quindi scegliere **Taglia**.<br />2.  Nel diagramma delle dipendenze, aprire il menu di scelta rapida per il livello e quindi scegliere **Incolla**.|
|Copiare il collegamento da un livello a un altro|1.  Aprire il menu di scelta rapida per il collegamento all'artefatto e quindi scegliere **copia**.<br />2.  Nel diagramma delle dipendenze, aprire il menu di scelta rapida per il livello e quindi scegliere **Incolla**.|
|Creare un nuovo livello da un collegamento dell'artefatto esistente|Trascinare il collegamento dell'artefatto in un'area vuota del diagramma.|
|Verificare che un elemento collegato supporti la convalida rispetto al diagramma di dipendenza.|Esaminare i **supporta la convalida** colonna per il collegamento dell'artefatto.|

## <a name="Discovering"></a> Decompilare dipendenze esistenti
 È presente una dipendenza quando un artefatto associato a un livello dispone di un riferimento a un artefatto associato a un altro livello. Ad esempio, una classe di un livello dichiara una variabile che dispone di una classe in un altro livello. È possibile decompilare dipendenze esistenti per elementi collegati a livelli nel diagramma.

> [!NOTE]
> Non è possibile decompilare dipendenze per determinati tipi di elementi. Ad esempio, non è possibile decompilare dipendenze da e verso un livello collegato a un file di testo. Per vedere quali artefatti sono associate dipendenze che è possibile decompilare, aprire il menu di scelta rapida per uno o più livelli e quindi scegliere **Visualizza collegamenti**. Nelle **Esplora livello**, esaminare le **supporta la convalida** colonna. Le dipendenze non verranno decompilate per artefatti per cui questa colonna viene visualizzato **False**.

-   Selezionare uno o più livelli, aprire il menu di scelta rapida per un livello selezionato e quindi scegliere **genera dipendenze**.

 In genere vengono visualizzate alcune dipendenze che non dovrebbero esistere. È possibile modificare queste dipendenze per allinearle con la progettazione desiderata.

## <a name="EditDependencies"></a> Modificare livelli e dipendenze per visualizzare la progettazione desiderata
 Per descrivere le modifiche che si prevede di apportare al sistema o l'architettura desiderata, modificare il diagramma delle dipendenze:

|**Per**|**Eseguire questi passaggi**|
|------------|-----------------------------|
|Modificare o limitare la direzione di una dipendenza|Impostare relativi **direzione** proprietà.|
|Creare nuove dipendenze|Usare la **Dependency** e **dipendenza bidirezionale** strumenti.<br /><br /> Per disegnare più dipendenze, fare doppio clic sullo strumento. Al termine, scegliere il **puntatore** degli strumenti oppure premere la **ESC** chiave.|
|Specificare che gli artefatti associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **dipendenze Namespace non è consentito** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli artefatti associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **Forbidden Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi del livello **Required Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|

## <a name="EditLayout"></a> Modificare l'aspetto gli elementi del diagramma
 È possibile modificare la dimensione, la forma, il colore e la posizione dei livelli o il colore delle dipendenze modificandone le proprietà.

## <a name="Codemaps"></a> Individuare i motivi e le dipendenze in una mappa codici
 Quando si creano i diagrammi delle dipendenze, è possibile creare anche **mappe codici**. Questi diagrammi consentono di individuare i motivi e le dipendenze durante l'esplorazione del codice. Usare Esplora soluzioni, Visualizzazione classi o Visualizzatore oggetti per esplorare assembly, spazi dei nomi e classi, che spesso corrispondono ai livelli esistenti. Per altre informazioni sulle mappe codice, vedere:

-   [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)

-   [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)

-   [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Video: Convalidare le dipendenze dell'architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)
- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)
- [Visualizzare il codice](../modeling/visualize-code.md)
