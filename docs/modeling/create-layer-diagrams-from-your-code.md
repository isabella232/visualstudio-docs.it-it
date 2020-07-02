---
title: Creare diagrammi delle dipendenze dal codice
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: 463e73a989deecf90e6bbfb7e8b92409b15695a5
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/30/2020
ms.locfileid: "85545730"
---
# <a name="create-dependency-diagrams-from-your-code"></a>Creare diagrammi delle dipendenze dal codice

Per visualizzare l'architettura logica di alto livello del sistema software, creare un diagramma delle *dipendenze* in Visual Studio. Per assicurarsi che il codice rimanga coerente con questa progettazione, convalidare il codice con un diagramma delle dipendenze. È possibile creare diagrammi di dipendenza per i progetti Visual C# e Visual Basic. Per visualizzare le edizioni di Visual Studio che supportano questa funzionalità, vedere [supporto dell'edizione per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools).

![Creazione di un diagramma delle dipendenze](../modeling/media/layerdiagramvisualizecode.png)

Un diagramma di dipendenza consente di organizzare gli elementi della soluzione di Visual Studio in gruppi logici astratti denominati *livelli*. È possibile utilizzare i livelli per descrivere le attività principali che tali elementi eseguono oppure i componenti principali del sistema. Ogni livello può contenere altri livelli che descrivono attività più dettagliate. È inoltre possibile specificare le *dipendenze* desiderate o esistenti tra i livelli. Tali dipendenze, rappresentate come frecce, mostrano quali livelli possono usare o usano attualmente la funzionalità rappresentata da altri livelli. Per gestire controllo a livello di architettura nel codice, mostrare le dipendenze desiderate nel diagramma, quindi convalidare il codice in base al diagramma.

[Video: convalidare le dipendenze dell'architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)

## <a name="create-a-dependency-diagram"></a><a name="CreateDiagram"></a>Creazione di un diagramma delle dipendenze

Prima di creare un diagramma delle dipendenze, assicurarsi che la soluzione disponga di un progetto di modello.

> [!IMPORTANT]
> Non aggiungere, trascinare o copiare un diagramma delle dipendenze esistente da un progetto di modello a un altro progetto di modello o a un'altra posizione nella soluzione. In questo modo i riferimenti del diagramma originale verranno mantenuti, anche se si modifica il diagramma. In caso contrario, il funzionamento della convalida dei livelli non sarà corretto e potrebbero verificarsi altri problemi, quali la mancanza di elementi o altri errori quando si tenta di aprire il diagramma.
>
> Aggiungere invece un nuovo diagramma delle dipendenze al progetto di modello. copiare gli elementi dal diagramma di origine al nuovo diagramma Salvare il progetto di modello e il nuovo diagramma delle dipendenze.

### <a name="add-a-new-dependency-diagram-to-a-modeling-project"></a>Aggiungere un nuovo diagramma delle dipendenze a un progetto di modello

> [!NOTE]
> I diagrammi di dipendenza per i progetti .NET Core sono supportati a partire da Visual Studio 2019 versione 16,2.

1. Scegliere **nuovo diagramma dipendenze**dal menu **architettura** .

2. In **modelli**scegliere **diagramma dipendenze**.

3. Assegnare un nome al diagramma.

4. In **Aggiungi a progetto di modello**individuare e selezionare un progetto di modello esistente nella soluzione.

     -oppure-

     Scegliere **Crea un nuovo progetto di modello** per aggiungere un nuovo progetto di modello alla soluzione.

    > [!NOTE]
    > Il diagramma delle dipendenze deve esistere all'interno di un progetto di modello. È tuttavia possibile collegarlo a elementi in qualsiasi punto della soluzione.

5. Assicurarsi di salvare il progetto di modello e il diagramma delle dipendenze.

## <a name="drag-and-drop-or-copy-and-paste-from-a-code-map"></a>Trascinamento della selezione, copia e incolla, da una mappa codice

1. Generare una mappa codice per la soluzione usando il menu **architettura** .

2. Si consiglia di applicare un filtro della mappa codici per rimuovere le cartelle della soluzione e "asset di test" Se si desidera applicare solo le dipendenze nel codice del prodotto.

3. Nella mappa codice generata rimuovere il nodo "External" oppure espanderlo per visualizzare gli assembly esterni, a seconda che si desideri applicare le dipendenze dello spazio dei nomi ed eliminare gli assembly non richiesti dalla mappa del codice.

4. Creare un nuovo diagramma delle dipendenze per la soluzione usando il menu **architettura**

5. Selezionare tutti i nodi nella mappa del codice (usare _CTRL_  +  _A_oppure usare la selezione della striscia di gomma premendo il tasto _MAIUSC_ prima di fare clic, trascinare e rilasciare.

6. Trascinare o copiare e incollare gli elementi selezionati nel nuovo diagramma di convalida delle dipendenze.

7. Viene visualizzata l'architettura dell'app corrente. Decidere che cosa si vuole che l'architettura sia e modificare di conseguenza il diagramma delle dipendenze.

![Diagramma delle dipendenze generato da una mappa codici](media/dependency-validation-01.png)

## <a name="create-layers-from-artifacts"></a><a name="CreateLayers"></a>Creare livelli da artefatti
 È possibile creare livelli da elementi presenti in una soluzione di Visual Studio, ad esempio progetti, file di codice, spazi dei nomi, classi e metodi. In questo modo vengono creati automaticamente collegamenti tra livelli ed elementi, che vengono inclusi nel processo di convalida dei livelli.

 È inoltre possibile collegare livelli a elementi che non supportano la convalida, ad esempio documenti Word o presentazioni PowerPoint, in modo da associare un livello con specifiche o piani. È anche possibile collegare livelli a file di progetti condivisi tra più applicazioni, ma il processo di convalida non includerà tali livelli, che vengano visualizzati con nomi generici come "Livello 1" e "Livello 2".

 Per verificare se un elemento collegato supporta la convalida, aprire **Esplora livello** ed esaminare la proprietà **convalida supportata** dell'elemento. Vedere [gestione dei collegamenti agli elementi](#Managing).

|**To**|**Attenersi alla seguente procedura**|
|-|-|
|Creare un livello per un solo elemento|<ol><li>Trascinare l'elemento nel diagramma delle dipendenze da queste origini:<br /><br /> <ul><li>**Esplora soluzioni**<br /><br />         Ad esempio, è possibile trascinare file o progetti.</li><li>Mappe codice<br /><br />         Vedere eseguire il [mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md) e [usare le mappe codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Visualizzazione classi** o **Visualizzatore oggetti**</li></ul><br />     Nel diagramma viene visualizzato un livello collegato all'elemento.</li><li>Rinominare il livello per riflettere le responsabilità del codice o degli artefatti associati.</li></ol> **Importante:**  Il trascinamento dei file binari nel diagramma delle dipendenze non aggiunge automaticamente i riferimenti al progetto di modello. ma è necessario aggiungere manualmente i file binari desiderati per convalidare il progetto di modello. **Per aggiungere file binari al progetto di modellazione** <ol><li>In **Esplora soluzioni**aprire il menu di scelta rapida per il progetto di modello, quindi scegliere **Aggiungi elemento esistente**.</li><li>Nella finestra di dialogo **Aggiungi elemento esistente** individuare i file binari, selezionarli, quindi scegliere **OK**.     I file binari verranno visualizzati nel progetto di modellazione.</li><li>In **Esplora soluzioni**scegliere un file binario aggiunto, quindi premere **F4** per aprire la finestra **proprietà** .</li><li>Per ogni file binario, impostare la proprietà **azione di compilazione** su **convalida**.</li></ol>|
|Creare un solo livello per tutti gli artefatti selezionati|Trascinare contemporaneamente tutti gli elementi nel diagramma delle dipendenze.<br /><br /> Nel diagramma viene visualizzato un livello collegato a tutti gli elementi.|
|Creare un livello per ogni elemento selezionato|Premere e tenere premuto **MAIUSC** mentre si trascinano tutti gli elementi nel diagramma delle dipendenze nello stesso momento. **Nota:**  Se si usa il tasto **MAIUSC** per selezionare un intervallo di elementi, rilasciare il tasto dopo avere selezionato gli elementi. Premerlo e tenerlo premuto nuovamente quando si trascinano gli elementi nel diagramma. <br /><br /> Per ogni elemento nel diagramma viene visualizzato un livello collegato a ciascun elemento.|
|Aggiungere un artefatto a un livello|Trascinare l'elemento sul livello.|
|Creare un nuovo livello non collegato|Nella **casella degli strumenti**espandere la sezione **diagramma delle dipendenze** , quindi trascinare un **livello** nel diagramma delle dipendenze.<br /><br /> Per aggiungere più livelli, fare doppio clic sullo strumento. Al termine, scegliere lo strumento **puntatore** o premere **ESC** .<br /><br /> - oppure -<br /><br /> Aprire il menu di scelta rapida per il diagramma delle dipendenze, scegliere **Aggiungi**, quindi scegliere **livello**.|
|Creare livelli annidati|Trascinare un livello esistente su un altro livello.<br /><br /> - oppure -<br /><br /> Aprire il menu di scelta rapida per un livello, scegliere **Aggiungi**, quindi scegliere **livello**.|
|Creare un nuovo livello contenente due o più livelli esistenti|Selezionare i livelli, aprire il menu di scelta rapida per la selezione, quindi scegliere **gruppo**.|
|Modificare il colore di un livello|Impostarne la proprietà **color** sul colore desiderato.|
|Specificare che gli elementi associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi nella proprietà **Forbidden Namespaces** del livello. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli elementi associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi nella proprietà delle **dipendenze dello spazio dei nomi non consentito** del livello. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi nella proprietà **obbligatoria Namespaces** del livello. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|

 Il numero raffigurato sul livello indica il numero di elementi a esso collegati. Tuttavia, nell'interpretazione di tale numero, considerare quanto segue:

- Se un livello è collegato a un elemento contenente altri elementi, ma non è collegato direttamente ad altri elementi, il numero include solo l'elemento collegato. Tuttavia, gli altri elementi vengono inclusi per l'analisi durante la convalida dei livelli.

     Ad esempio, se un livello è collegato a un solo spazio dei nomi, il numero degli elementi collegati sarà 1, anche se lo spazio dei nomi contiene classi. Se il livello è collegato anche a ciascuna classe dello spazio dei nomi, il numero includerà le classi collegate.

- Se un livello contiene altri livelli collegati a elementi, anche il livello contenitore sarà collegato a tali elementi nonostante il numero raffigurato sul livello contenitore non includa quegli elementi.

## <a name="manage-links-between-layers-and-artifacts"></a><a name="Managing"></a>Gestire i collegamenti tra livelli ed elementi

1. Nel diagramma delle dipendenze aprire il menu di scelta rapida per il livello, quindi scegliere **Visualizza collegamenti**.

     **Esplora livello** Mostra i collegamenti dell'elemento per il livello selezionato.

2. Usare le seguenti attività per gestire tali collegamenti:

|**To**|**In Esplora livello**|
|-|-|
|Eliminare il collegamento tra il livello e un elemento|Aprire il menu di scelta rapida per il collegamento artefatto, quindi scegliere **Elimina**.|
|Spostare il collegamento da un livello a un altro|Trascinare il collegamento dell'elemento in un livello esistente del diagramma.<br /><br /> - oppure -<br /><br /> 1. Aprire il menu di scelta rapida per il collegamento dell'artefatto, quindi scegliere **taglia**.<br />2. nel diagramma delle dipendenze aprire il menu di scelta rapida per il livello, quindi scegliere **Incolla**.|
|Copiare il collegamento da un livello a un altro|1. Aprire il menu di scelta rapida per il collegamento artefatto, quindi scegliere **copia**.<br />2. nel diagramma delle dipendenze aprire il menu di scelta rapida per il livello, quindi scegliere **Incolla**.|
|Creare un nuovo livello da un collegamento dell'elemento esistente|Trascinare il collegamento dell'artefatto in un'area vuota del diagramma.|
|Verificare che un elemento collegato supporti la convalida rispetto al diagramma delle dipendenze.|Esaminare la colonna **Supports Validation** per il collegamento dell'artefatto.|

## <a name="reverse-engineer-existing-dependencies"></a><a name="Discovering"></a>Decodificare le dipendenze esistenti
 È presente una dipendenza quando un elemento associato a un livello dispone di un riferimento a un elemento associato a un altro livello. Ad esempio, una classe di un livello dichiara una variabile che dispone di una classe in un altro livello. È possibile decompilare dipendenze esistenti per elementi collegati a livelli nel diagramma.

> [!NOTE]
> Non è possibile decompilare dipendenze per determinati tipi di elementi. Ad esempio, non è possibile decompilare dipendenze da e verso un livello collegato a un file di testo. Per verificare quali elementi presentano dipendenze che è possibile decompilare, aprire il menu di scelta rapida per uno o più livelli, quindi scegliere **Visualizza collegamenti**. In **Esplora livello**esaminare la colonna **supporta la convalida** . Le dipendenze non verranno decodificate per gli artefatti per i quali la colonna Visualizza **false**.

- Selezionare uno o più livelli, aprire il menu di scelta rapida per un livello selezionato, quindi scegliere **Genera dipendenze**.

  In genere vengono visualizzate alcune dipendenze che non dovrebbero esistere. È possibile modificare queste dipendenze per allinearle con la progettazione desiderata.

## <a name="edit-layers-and-dependencies-to-show-the-intended-design"></a><a name="EditDependencies"></a>Modificare i livelli e le dipendenze per visualizzare la progettazione desiderata
 Per descrivere le modifiche che si intende apportare al sistema o all'architettura desiderata, modificare il diagramma delle dipendenze:

|**To**|**Eseguire questi passaggi**|
|-|-|
|Modificare o limitare la direzione di una dipendenza|Impostarne la proprietà **Direction** .|
|Creare nuove dipendenze|Usare gli **strumenti di dipendenza e dipendenza** **bidirezionale** .<br /><br /> Per disegnare più dipendenze, fare doppio clic sullo strumento. Al termine, scegliere lo strumento **puntatore** o premere **ESC** .|
|Specificare che gli elementi associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi nella proprietà delle **dipendenze dello spazio dei nomi non consentito** del livello. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli elementi associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi nella proprietà **Forbidden Namespaces** del livello. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi nella proprietà **obbligatoria Namespaces** del livello. Utilizzare un punto e virgola (**;**) per separare gli spazi dei nomi.|

## <a name="change-how-elements-appear-on-the-diagram"></a><a name="EditLayout"></a>Modificare la modalità di visualizzazione degli elementi nel diagramma
 È possibile modificare la dimensione, la forma, il colore e la posizione dei livelli o il colore delle dipendenze modificandone le proprietà.

## <a name="discover-patterns-and-dependencies-on-a-code-map"></a><a name="Codemaps"></a>Individuare modelli e dipendenze in una mappa codici
 Durante la creazione di diagrammi di dipendenza, è anche possibile creare **mappe codice**. Questi diagrammi consentono di individuare i motivi e le dipendenze durante l'esplorazione del codice. Usare Esplora soluzioni, Visualizzazione classi o Visualizzatore oggetti per esplorare assembly, spazi dei nomi e classi, che spesso corrispondono ai livelli esistenti. Per altre informazioni sulle mappe codice, vedere:

- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)

- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)

- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="see-also"></a>Vedere anche

- [Supporto dell'edizione per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#edition-support-for-architecture-and-modeling-tools)
- [Video: convalidare le dipendenze dell'architettura in tempo reale](https://sec.ch9.ms/sessions/69613110-c334-4f25-bb36-08e5a93456b5/170ValidateArchitectureDependenciesWithVisualStudio.mp4)
- [Diagrammi delle dipendenze: riferimenti](../modeling/layer-diagrams-reference.md)
- [Diagrammi delle dipendenze: linee guida](../modeling/layer-diagrams-guidelines.md)
- [Convalidare il codice con i diagrammi delle dipendenze](../modeling/validate-code-with-layer-diagrams.md)
- [Visualizzare il codice](../modeling/visualize-code.md)
