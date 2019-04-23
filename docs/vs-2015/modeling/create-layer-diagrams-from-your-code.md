---
title: Creare diagrammi livello dal codice | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- architecture, layer diagrams
- layer diagrams
- diagrams - modeling, layer
- constraints, architectural
ms.assetid: 58c3ea71-2dbc-4963-bf82-40f1924cf973
caps.latest.revision: 64
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: a3ff96a68d66c95d4f1302ba2f419c873e8f077d
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60050212"
---
# <a name="create-layer-diagrams-from-your-code"></a>Creare diagrammi livello dal codice
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per visualizzare l'architettura di alto livello, logica del sistema software, creare un *diagramma livello* in Visual Studio. Per verificare la conformità del codice alla progettazione, convalidare il codice con un diagramma livello. È possibile creare diagrammi livello per i progetti Visual C# .NET e Visual Basic. .NET. Per le versioni di Visual Studio che supportano questa funzionalità, vedere [supporto della versione per l'architettura e strumenti di modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport)  
  
 ![Creare un diagramma livello](../modeling/media/layerdiagramvisualizecode.png "LayerDiagramVisualizeCode")  
  
 Un diagramma livello consente di organizzare gli elementi di soluzione di Visual Studio in gruppi logici astratti, chiamati *livelli*. È possibile utilizzare i livelli per descrivere le attività principali che tali elementi eseguono oppure i componenti principali del sistema. Ogni livello può contenere altri livelli che descrivono attività più dettagliate. È inoltre possibile specificare il desiderate o esistenti *dipendenze* tra livelli. Tali dipendenze, rappresentate come frecce, mostrano quali livelli possono usare o usano attualmente la funzionalità rappresentata da altri livelli. Per gestire controllo a livello di architettura nel codice, mostrare le dipendenze desiderate nel diagramma, quindi convalidare il codice in base al diagramma.  
  
## <a name="CreateDiagram"></a> Creare un diagramma livello  
 Prima di creare un diagramma livello, verificare che alla soluzione sia associato un progetto di modellazione. Visualizzare [diagrammi e progetti di modellazione UML creare](../modeling/create-uml-modeling-projects-and-diagrams.md).  
  
> [!IMPORTANT]
>  Non aggiungere, trascinare o copiare alcun diagramma livello esistente da un progetto di modello a un altro né a un altro percorso nella soluzione. In questo modo i riferimenti del diagramma originale verranno mantenuti, anche se si modifica il diagramma. In caso contrario, il funzionamento della convalida dei livelli non sarà corretto e potrebbero verificarsi altri problemi, quali la mancanza di elementi o altri errori quando si tenta di aprire il diagramma.  
>   
>  È necessario aggiungere invece un nuovo diagramma livello al progetto di modellazione, copiare gli elementi dal diagramma di origine al nuovo diagramma e salvare sia il progetto di modello che il nuovo diagramma livello.  
  
#### <a name="to-add-a-new-layer-diagram-to-a-modeling-project"></a>Per aggiungere un nuovo diagramma livello a un progetto di modellazione  
  
1. Nel **Architecture** menu, scegliere **nuovo diagramma livello o UML**.  
  
2. Sotto **modelli**, scegliere **diagramma livello**.  
  
3. Assegnare un nome al diagramma.  
  
4. Nelle **Aggiungi a progetto di modello**, individuare e selezionare un progetto di modellazione esistente nella soluzione.  
  
     -oppure-  
  
     Scegli **creare un nuovo progetto di modellazione** per aggiungere un nuovo progetto di modellazione alla soluzione.  
  
    > [!NOTE]
    >  È necessario che il diagramma livello sia presente all'interno di un progetto di modellazione. È tuttavia possibile collegarlo a elementi in qualsiasi punto della soluzione.  
  
5. Assicurarsi di salvare il progetto di modello contenente il diagramma livello.  
  
## <a name="CreateLayers"></a> Creare livelli da artefatti  
 È possibile creare livelli da elementi presenti in una soluzione di Visual Studio, ad esempio progetti, file di codice, spazi dei nomi, classi e metodi. In questo modo vengono creati automaticamente collegamenti tra livelli ed elementi, che vengono inclusi nel processo di convalida dei livelli.  
  
 È inoltre possibile collegare livelli a elementi che non supportano la convalida, ad esempio documenti Word o presentazioni PowerPoint, in modo da associare un livello con specifiche o piani. È anche possibile collegare livelli a file di progetti condivisi tra più applicazioni, ma il processo di convalida non includerà tali livelli, che vengano visualizzati con nomi generici come "Livello 1" e "Livello 2".  
  
 Per vedere se un elemento collegato supporta la convalida, aprire **Esplora livello** ed esaminare le **supporta la convalida** proprietà dell'elemento. Visualizzare [gestione dei collegamenti agli elementi](#Managing).  
  
|**Per**|**Seguire questi passaggi**|  
|------------|----------------------------|  
|Creare un livello per un solo elemento|<ol><li>Trascinare l'elemento nel diagramma livello da queste origini:<br /><br /> <ul><li>**Esplora soluzioni**<br /><br />         Ad esempio, è possibile trascinare file o progetti.</li><li>Mappe codice<br /><br />         Visualizzare [mappare le dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md) e [usare le mappe codice per il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md).</li><li>**Visualizzazione classi** o **Visualizzatore oggetti**</li></ul><br />     Nel diagramma viene visualizzato un livello collegato all'elemento.</li><li>Rinominare il livello per riflettere le responsabilità del codice o degli artefatti associati.</li></ol> **Importante:**  Se si trascinano file binari sul diagramma livello, i riferimenti relativi non vengono aggiunti automaticamente al progetto di modellazione, ma è necessario aggiungere manualmente i file binari desiderati per convalidare il progetto di modello. **Per aggiungere i file binari al progetto di modellazione** <ol><li>Nelle **Esplora soluzioni**, aprire il menu di scelta rapida per il progetto di modellazione e quindi scegliere **Aggiungi elemento esistente**.</li><li>Nel **Aggiungi elemento esistente** della finestra di dialogo selezionare i file binari, selezionarli e quindi scegliere **OK**.     I file binari verranno visualizzati nel progetto di modellazione.</li><li>Nelle **Esplora soluzioni**, scegliere un file binario che aggiunto e quindi premere **F4** per aprire il **proprietà** finestra.</li><li>Per ogni file binario, impostare il **Build Action** proprietà **Validate**.</li></ol>|  
|Creare un solo livello per tutti gli artefatti selezionati|Trascinare contemporaneamente tutti gli elementi sul diagramma livello.<br /><br /> Nel diagramma viene visualizzato un livello collegato a tutti gli elementi.|  
|Creare un livello per ogni elemento selezionato|Premere e tenere premuto il **MAIUSC** mentre si trascinano contemporaneamente tutti gli elementi nel diagramma livello. **Nota:**  Se si usa la **MAIUSC** chiave per selezionare un intervallo di elementi, rilasciare il tasto dopo avere selezionato gli artefatti. Premerlo e tenerlo premuto nuovamente quando si trascinano gli elementi nel diagramma. <br /><br /> Per ogni elemento nel diagramma viene visualizzato un livello collegato a ciascun elemento.|  
|Aggiungere un elemento a un livello|Trascinare l'elemento sul livello.|  
|Creare un nuovo livello non collegato|Nel **casella degli strumenti**, espandere il **diagramma livello** sezione e quindi trascinare un' **livello** nel diagramma livello.<br /><br /> Per aggiungere più livelli, fare doppio clic sullo strumento. Al termine, scegliere il **puntatore** degli strumenti oppure premere la **ESC** chiave.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per il diagramma livello, scegliere **Add**, quindi scegliere **Layer**.|  
|Creare livelli annidati|Trascinare un livello esistente su un altro livello.<br /><br /> -oppure-<br /><br /> Aprire il menu di scelta rapida per un livello, scegliere **Add**, quindi scegliere **Layer**.|  
|Creare un nuovo livello contenente due o più livelli esistenti|Selezionare i livelli, aprire il menu di scelta rapida per la selezione e quindi scegliere **gruppo**.|  
|Modificare il colore di un livello|Impostare relativi **colore** proprietà sul colore desiderato.|  
|Specificare che gli elementi associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **Forbidden Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli elementi associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **dipendenze Namespace non è consentito** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi del livello **Required Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
  
 Il numero raffigurato sul livello indica il numero di elementi a esso collegati. Tuttavia, nell'interpretazione di tale numero, considerare quanto segue:  
  
- Se un livello è collegato a un elemento contenente altri elementi, ma non è collegato direttamente ad altri elementi, il numero include solo l'elemento collegato. Tuttavia, gli altri elementi vengono inclusi per l'analisi durante la convalida dei livelli.  
  
     Ad esempio, se un livello è collegato a un solo spazio dei nomi, il numero degli elementi collegati sarà 1, anche se lo spazio dei nomi contiene classi. Se il livello è collegato anche a ciascuna classe dello spazio dei nomi, il numero includerà le classi collegate.  
  
- Se un livello contiene altri livelli collegati a elementi, anche il livello contenitore sarà collegato a tali elementi nonostante il numero raffigurato sul livello contenitore non includa quegli elementi.  
  
## <a name="Managing"></a> Gestire collegamenti tra livelli e artefatti  
  
1. Nel diagramma livello, aprire il menu di scelta rapida per il livello e quindi scegliere **Visualizza collegamenti**.  
  
     **Esplora livello** vengono visualizzati i collegamenti dell'artefatto per il livello selezionato.  
  
2. Usare le seguenti attività per gestire tali collegamenti:  
  
|**Per**|**In Layer Explorer**|  
|------------|---------------------------|  
|Eliminare il collegamento tra il livello e un elemento|Aprire il menu di scelta rapida per il collegamento all'artefatto e quindi scegliere **Elimina**.|  
|Spostare il collegamento da un livello a un altro|Trascinare il collegamento dell'elemento in un livello esistente del diagramma.<br /><br /> -oppure-<br /><br /> 1.  Aprire il menu di scelta rapida per il collegamento all'artefatto e quindi scegliere **Taglia**.<br />2.  Nel diagramma livello, aprire il menu di scelta rapida per il livello e quindi scegliere **Incolla**.|  
|Copiare il collegamento da un livello a un altro|1.  Aprire il menu di scelta rapida per il collegamento all'artefatto e quindi scegliere **copia**.<br />2.  Nel diagramma livello, aprire il menu di scelta rapida per il livello e quindi scegliere **Incolla**.|  
|Creare un nuovo livello da un collegamento dell'elemento esistente|Trascinare il collegamento dell'artefatto in un'area vuota del diagramma.|  
|Verificare che un elemento collegato supporti la convalida in base al diagramma livello.|Esaminare i **supporta la convalida** colonna per il collegamento dell'artefatto.|  
  
## <a name="Discovering"></a> Decompilare dipendenze esistenti  
 È presente una dipendenza quando un elemento associato a un livello dispone di un riferimento a un elemento associato a un altro livello. Ad esempio, una classe di un livello dichiara una variabile che dispone di una classe in un altro livello. È possibile decompilare dipendenze esistenti per elementi collegati a livelli nel diagramma.  
  
> [!NOTE]
>  Non è possibile decompilare dipendenze per determinati tipi di elementi. Ad esempio, non è possibile decompilare dipendenze da e verso un livello collegato a un file di testo. Per vedere quali artefatti sono associate dipendenze che è possibile decompilare, aprire il menu di scelta rapida per uno o più livelli e quindi scegliere **Visualizza collegamenti**. Nelle **Esplora livello**, esaminare le **supporta la convalida** colonna. Le dipendenze non verranno decompilate per artefatti per cui questa colonna viene visualizzato **False**.  
  
- Selezionare uno o più livelli, aprire il menu di scelta rapida per un livello selezionato e quindi scegliere **genera dipendenze**.  
  
  In genere vengono visualizzate alcune dipendenze che non dovrebbero esistere. È possibile modificare queste dipendenze per allinearle con la progettazione desiderata.  
  
## <a name="EditDependencies"></a> Modificare livelli e dipendenze per visualizzare la progettazione desiderata  
 Per descrivere le modifiche da apportare al sistema o all'architettura desiderata, modificare il diagramma livello:  
  
|**Per**|**Eseguire questi passaggi**|  
|------------|-----------------------------|  
|Modificare o limitare la direzione di una dipendenza|Impostare relativi **direzione** proprietà.|  
|Creare nuove dipendenze|Usare la **Dependency** e **dipendenza bidirezionale** strumenti.<br /><br /> Per disegnare più dipendenze, fare doppio clic sullo strumento. Al termine, scegliere il **puntatore** degli strumenti oppure premere la **ESC** chiave.|  
|Specificare che gli elementi associati a un livello non possono dipendere dagli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **dipendenze Namespace non è consentito** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli elementi associati a un livello non devono appartenere agli spazi dei nomi specificati|Digitare gli spazi dei nomi del livello **Forbidden Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
|Specificare che gli artefatti associati a un livello non devono appartenere a uno degli spazi dei nomi specificati|Digitare lo spazio dei nomi del livello **Required Namespaces** proprietà. Usare un punto e virgola (**;**) per separare gli spazi dei nomi.|  
  
## <a name="EditLayout"></a> Modificare l'aspetto gli elementi del diagramma  
 È possibile modificare la dimensione, la forma, il colore e la posizione dei livelli o il colore delle dipendenze modificandone le proprietà.  
  
## <a name="Codemaps"></a> Individuare i motivi e le dipendenze in una mappa codici  
 Quando si creano i diagrammi livello, è possibile creare anche **mappe codici**. Questi diagrammi consentono di individuare i motivi e le dipendenze durante l'esplorazione del codice. Usare Esplora soluzioni, Visualizzazione classi o Visualizzatore oggetti per esplorare assembly, spazi dei nomi e classi, che spesso corrispondono ai livelli esistenti. Per altre informazioni sulle mappe codice, vedere:  
  
- [Eseguire il mapping delle dipendenze nelle soluzioni](../modeling/map-dependencies-across-your-solutions.md)  
  
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)  
  
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Video di Channel 9: Progettare e convalidare l'architettura utilizzando i diagrammi livello](http://go.microsoft.com/fwlink/?LinkID=252073)   
 [Diagrammi dei livelli: Riferimento](../modeling/layer-diagrams-reference.md)   
 [Diagrammi dei livelli: Linee guida](../modeling/layer-diagrams-guidelines.md)   
 [Convalidare il codice con diagrammi livello](../modeling/validate-code-with-layer-diagrams.md)   
 [Visualizzare il codice](../modeling/visualize-code.md)