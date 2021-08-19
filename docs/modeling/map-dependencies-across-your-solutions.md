---
title: Visualizzare le dipendenze con mappe codice
description: Informazioni su come le mappe codice consentono di vedere come si inserisce il codice senza leggere file e righe di codice.
ms.custom: SEO-VS-2020
ms.date: 05/16/2021
ms.topic: how-to
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: d4968cd181a05cdfabce5eb3ae772afe42423291
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047959"
---
# <a name="map-dependencies-with-code-maps"></a>Eseguire il mapping delle dipendenze con mappe codice

Questo articolo illustra come visualizzare le dipendenze nel codice con mappe codice.

## <a name="what-are-code-maps"></a>Che cosa sono le mappe codice?

In Visual Studio, le mappe codice consentono di vedere più rapidamente come si inserisce il codice del programma senza leggere file e righe di codice.  Con queste mappe è possibile visualizzare l'organizzazione e le relazioni nel codice, inclusa la struttura e le relative dipendenze, come aggiornarla e stimare il costo delle modifiche proposte.

![Visualizzare le dipendenze con mappe codice in Visual Studio](../modeling/media/codemapsmainintro.png)

È possibile eseguire il mapping delle dipendenze per il codice nei seguenti linguaggi:

- Visual C# o Visual Basic in una soluzione o in assembly (*.dll* *o.exe*)

- Codice C o C++ nativo o gestito in Visual C++, file di intestazione ( con estensione *h* `#include` o ) o file binari

- Progetti X++ e assembly creati da moduli .NET per Microsoft Dynamics AX

> [!NOTE]
> Per i progetti diversi da C# o Visual Basic, sono disponibili meno opzioni per l'avvio di una mappa codice o l'aggiunta di elementi a una mappa codice esistente. Ad esempio, non è possibile fare clic con il pulsante destro del mouse su un oggetto nell'editor di testo di un progetto C++ e aggiungerlo a una mappa codice. È tuttavia possibile trascinare e rilasciare singoli elementi di codice o file **da** Esplora soluzioni , **Visualizzazione classi** e **Visualizzatore oggetti**.

## <a name="prerequisites"></a>Prerequisiti

Per creare una mappa del codice in Visual Studio, installare prima i componenti Mappa codice e [ **Convalida dipendenze** in  tempo reale](install-architecture-tools.md)

Per creare e modificare mappe codice, è necessario **Visual Studio Enterprise edizione**. Tuttavia, nelle Visual Studio Community e Professional, è possibile aprire i diagrammi generati Enterprise edizione, ma non è possibile modificarli.

> [!NOTE]
> Prima di condividere le mappe create in Visual Studio Enterprise con altri utenti che usano Visual Studio Professional, assicurarsi che tutti gli elementi sulla mappa (ad esempio elementi nascosti, gruppi espansi e collegamenti tra gruppi) siano visibili.

## <a name="add-a-code-map"></a>Aggiungere una mappa del codice

È possibile creare una mappa codice vuota e trascinarvi elementi, inclusi riferimenti ad assembly, file e cartelle, oppure generare una mappa codice per tutta o parte della soluzione.

Per aggiungere una mappa codice vuota:

1. In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo della soluzione di primo livello. Scegliere **Aggiungi**  >  **nuovo elemento**.

2. Nella finestra **di dialogo Aggiungi nuovo elemento** in **Installato** scegliere la **categoria** Generale.

3. Scegliere il **modello Graph documento (.dgml) e** quindi selezionare **Aggiungi**.

   > [!TIP]
   > Questo modello potrebbe non essere visualizzato in ordine alfabetico, quindi scorrere verso il basso fino alla fine dell'elenco dei modelli se non viene visualizzato.

   Nella cartella Elementi di soluzione della soluzione viene visualizzata una **mappa** vuota.

Analogamente, è possibile creare un nuovo file di mappa codice senza aggiungerlo alla soluzione selezionando Architettura Nuova mappa codice  >   o **File**  >    >  **nuovo file**.

Altre informazioni:
- [Condividere mappe codice](share-code-maps.md)
- [Creare mappe codice per C++](code-maps-for-cpp.md)
- [Migliorare le prestazioni della mappa codice](code-maps-performance.md)

## <a name="generate-a-code-map-for-your-solution"></a>Generare una mappa del codice per la soluzione

Per visualizzare tutte le dipendenze nella soluzione:

1. Sulla barra dei menu scegliere **Architettura**  >  **Genera mappa codice per la soluzione**. Se il codice non è stato modificato dopo l'ultima compilazione, è possibile selezionare Architecture Generate Code Map for Solution Without Building (Architettura Genera mappa codice per soluzione   >  **senza compilazione).**

   ![Comando di generazione mappa del codice](../modeling/media/codemapsarchitecturemenu.png)

   Viene generata una mappa che mostra gli assembly di primo livello e i collegamenti aggregati tra di essi. A una maggiore ampiezza del collegamento aggregato corrisponde un maggior numero di dipendenze che rappresenta.

2. Usare il pulsante **Legenda** sulla barra degli strumenti del codice per visualizzare o nascondere l'elenco di icone del tipo di progetto (ad esempio Test, Web e Progetto per telefono), gli elementi di codice (ad esempio Classi, Metodi e Proprietà) e i tipi di relazione (ad esempio Eredita da, Implementa e Chiamate).

   ![Grafico dipendenze di primo livello di assembly](../modeling/media/dependencygraph_toplevelassemblies.png)

   Questa soluzione di esempio contiene cartelle della soluzione (**Test** e **Componenti**), progetti di test, progetti Web e assembly. Per impostazione predefinita, tutte le relazioni del contenitore vengono visualizzate come *gruppi* che è possibile espandere e comprimere. Il gruppo **Esterni** contiene qualsiasi elemento esterno alla soluzione, incluse le dipendenze della piattaforma. Gli assembly esterni mostrano solo gli elementi usati. Per impostazione predefinita, i tipi di base del sistema sono nascosti sulla mappa per evitare confusione.

3. Per eseguire il drill-down nella mappa, espandere i gruppi che rappresentano progetti e assembly. Per espandere tutti gli elementi premere **CTRL+A** per selezionare tutti i nodi e quindi scegliere **Gruppo**, **Espandi** dal menu di scelta rapida.

   ![Espansione di tutti i gruppi in una mappa codici](../modeling/media/codemapsexpandallgroups.png)

4. Tuttavia, questa operazione potrebbe non essere utile per una soluzione di grandi dimensioni. Infatti, per soluzioni complesse, i limiti di memoria potrebbero impedire di espandere tutti i gruppi. In alternativa, per visualizzare gli elementi all'interno di un singolo nodo, espanderlo. Spostare il puntatore del mouse sopra il nodo, quindi scegliere il pulsante con la freccia di espansione (freccia giù) quando viene visualizzato.

   ![Espansione di un nodo in una mappa codici](../modeling/media/dependencygraph_containment.png)

   Oppure usare la tastiera selezionando l'elemento e quindi premendo il tasto più ( **+** ). Per esplorare i livelli più profondi di codice, effettuare la stessa operazione per gli spazi dei nomi, i tipi e i membri.

   > [!TIP]
   > Per altre informazioni sull'uso delle mappe codice con il mouse, la tastiera e il tocco, vedere Esplorare e [ridisporre le mappe codice.](../modeling/browse-and-rearrange-code-maps.md)

5. Per semplificare la mappa e concentrarsi sulle singole parti, scegliere **Filtri** nella barra degli strumenti della mappa codice e selezionare solo i tipi di nodi e di collegamenti desiderati. Ad esempio, è possibile nascondere tutti i contenitori di Cartella soluzione e Assembly.

   ![Semplificare la mappa filtrando i contenitori](../modeling/media/codemapsfilterfoldersassemblies.png)

   È anche possibile semplificare la mappa nascondendo o rimuovendo i singoli gruppi ed elementi dalla mappa, senza modificare il codice della soluzione sottostante.

6. Per visualizzare le relazioni tra elementi, selezionarle nella mappa. I colori dei collegamenti indicano i tipi di relazione, come mostrato nel riquadro **Legenda** .

   ![Visualizzare le dipendenze nelle soluzioni](../modeling/media/codemapsmainintro.png)

   In questo esempio, i collegamenti viola sono chiamate, i collegamenti punteggiati sono riferimenti e i collegamenti azzurro rappresentano l'accesso al campo. I collegamenti verdi possono essere ereditati o possono essere *collegamenti aggregati* che indicano più di un tipo di relazione (o *categoria*).

   > [!TIP]
   > Se viene visualizzato un collegamento verde, non necessariamente esiste solo una relazione di ereditarietà. Potrebbero essere presenti anche chiamate al metodo, nascoste dalla relazione di ereditarietà. Per visualizzare tipi specifici di collegamenti,  usare le caselle di controllo nel riquadro Filtri per nascondere i tipi a cui non si è interessati.

7. Per altre informazioni su un elemento o un collegamento, spostare il puntatore su di esso finché non viene visualizzata una descrizione comando. In questo modo vengono mostrati i dettagli di un elemento di codice o delle categorie rappresentate da un collegamento.

   ![Mostra le categorie di una relazione](../modeling/media/codemapsshowlinkcatgories.png)

8. Per esaminare gli elementi e le dipendenze rappresentate da un collegamento di aggregazione, prima selezionare il collegamento, quindi aprire il relativo menu di scelta rapida. Scegliere **Mostra collegamenti partecipanti** (o **Mostra collegamenti partecipanti sulla nuova mappa codice**). I gruppi vengono espansi a entrambe le estremità del collegamento e vengono mostrati solo gli elementi e le dipendenze che partecipano al collegamento.

9. Per concentrarsi su parti specifiche della mappa, è possibile continuare a rimuovere gli elementi a cui non si è interessati. Ad esempio, per analizzare la visualizzazione delle classi e dei membri, è sufficiente filtrare tutti i nodi dello spazio dei nomi nel riquadro **Filtri** .

   ![Drill-down dei gruppi a livello di classe e membro](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Un altro modo per concentrarsi sulla mappa di soluzione complessa consiste nel generare una nuova mappa contenente gli elementi selezionati da una mappa esistente. Tenere **premuto CTRL** mentre si selezionano gli elementi su cui si vuole concentrarsi, aprire il menu di scelta rapida e scegliere Nuovo Graph da **Selezione**.

    ![Mostra gli elementi selezionati in una nuova mappa codici](../modeling/media/codemapsshowonnewmap.png)

11. Il contesto contenitore viene trasferito alla nuova mappa. Nascondere cartelle della soluzione e qualsiasi altro contenitore che non si vuole visualizzare usando il **riquadro** Filtri.

    ![Filtrare i contenitori per semplificare la visualizzazione](../modeling/media/codemapsexpandnewgroups.png)

12. Espandere i gruppi e selezionare gli elementi della mappa per visualizzare le relazioni.

    ![Selezionare gli elementi per visualizzare le relazioni](../modeling/media/codemapsviewnewrelationships.png)

Vedere anche:

- [Cercare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)
- [Personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Trovare potenziali problemi nel codice eseguendo [un analizzatore](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-dependencies"></a>Visualizzare le dipendenze

Si supponga di avere una revisione del codice da eseguire in alcuni file con modifiche in sospeso. Per visualizzare le dipendenze in queste modifiche, è possibile creare una mappa codice da tali file.

   ![Mostra dipendenze specifiche su una mappa codici](../modeling/media/codemapsspecificdependenciesintro.png)

1. In **Esplora soluzioni** selezionare i progetti, i riferimenti agli assembly, le cartelle, i file, i tipi o i membri di cui si vuole eseguire il mapping.

   ![Selezionare gli elementi da mappare](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Sulla barra **Esplora soluzioni** fare **clic** su Mostra nella mappa codice Crea Graph pulsante Da nodi ![ selezionati ](../modeling/media/createnewgraphfromselectedbutton.gif) . In caso contrario, aprire il menu di scelta rapida per uno o un gruppo di elementi e **scegliere Mostra nella mappa codice**.

   È anche possibile trascinare elementi **Esplora soluzioni**, **Visualizzazione classi** o **Visualizzatore** oggetti in una [mappa](#add-a-code-map) codice nuova o esistente. Per includere la gerarchia padre per gli elementi, tenere premuto **CTRL** mentre si trascinano gli elementi oppure usare il pulsante Includi elementi padre sulla barra degli strumenti della mappa codice per specificare l'azione predefinita.  È anche possibile trascinare i file di assembly dall'Visual Studio, ad esempio **da Windows Explorer.**

   > [!NOTE]
   > Quando si aggiungono elementi da un progetto condiviso tra più app, ad esempio Windows Phone o Microsoft Store, tali elementi vengono visualizzati sulla mappa con il progetto di app attualmente attivo. Se si cambia il contesto passando a un altro progetto di applicazione e si aggiungono altri elementi dal progetto condiviso, tali elementi vengono visualizzati con il nuovo progetto di applicazione attivo. Le operazioni eseguite con un elemento nella mappa si applicano solo agli elementi che condividono lo stesso contesto.

3. La mappa visualizza gli elementi selezionati all'interno degli assembly in cui sono contenuti.

   ![Elementi selezionati visualizzati come gruppi sulla mappa](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Per esplorare gli elementi, espanderli. Spostare il puntatore del mouse sopra un elemento, quindi scegliere il pulsante con la freccia di espansione (freccia Giù) quando viene visualizzato.

   ![Espandere un nodo in una mappa codice](../modeling/media/dependencygraph_containment.png)

   Per espandere tutti gli elementi, selezionarli premendo **CTRL** A, quindi aprire il + menu di scelta rapida per la mappa e scegliere Group Expand **(Espandi**  >  **gruppo).** Tuttavia, questa opzione non è disponibile se l'espansione di tutti i gruppi crea una mappa inutilizzabile o problemi di memoria.

5. Continuare ad espandere gli elementi a cui si è interessati, fino al livello di classe e membro, se necessario.

   ![Espandere i gruppi a livello di classe e membro](../modeling/media/codemapsexpandtoclassandmember.png)

   Per visualizzare i membri presenti nel codice ma non visualizzati sulla mappa, fare clic sull'icona Refetch Children (Elementi figlio **refetch) Icona Refetch Children** (Elementi figlio refetch) nell'angolo superiore sinistro ![ di un ](../modeling/media/dependencygraph_deletednodesicon.png) gruppo.

6. Per visualizzare più elementi correlati a quelli sulla mappa, selezionarne uno e scegliere **Mostra correlati** nella barra degli strumenti della mappa codice, quindi selezionare il tipo di elementi correlati da aggiungere alla mappa. In alternativa, selezionare uno o più elementi, aprire  il menu di scelta rapida e quindi scegliere l'opzione Mostra per il tipo di elementi correlati da aggiungere alla mappa. Esempio:

    Per un **assembly** scegliere:

    |Opzione|Descrizione|
    |-|-|
    |**Mostra assembly a cui fa riferimento**|Aggiungere gli assembly a cui fa riferimento questo assembly. Gli assembly esterni vengono visualizzati nel gruppo **Esterni** .|
    |**Mostra assembly che fanno riferimento a**|Aggiungere gli assembly della soluzione che fanno riferimento a questo assembly.|

    Per uno **spazio dei nomi** scegliere **Mostra assembly contenitore**, se non è visibile.

    Per una **classe** o un' **interfaccia** scegliere:

    |Opzione|Descrizione|
    |-|-|
    |**Mostra tipi base**|Per una classe, aggiungere la classe base e le interfacce implementate.<br /><br /> Per un'interfaccia, aggiungere le interfacce di base.|
    |**Mostra tipi derivati**|Per una classe, aggiungere le classi derivate.<br /><br /> Per un'interfaccia, aggiungere le interfacce derivate e le classi o gli struct implementati.|
    |**Mostra tipi a cui fa riferimento**|Aggiungere tutte le classi e i membri usati.|
    |**Mostra tipi che fanno riferimento a**|Aggiungere tutte le classi e membri che usano la classe.|
    |**Mostra spazio dei nomi contenitore**|Aggiungere lo spazio dei nomi del padre.|
    |**Mostra spazio dei nomi e assembly contenitore**|Aggiungere la gerarchia del contenitore padre.|
    |**Mostra tutti i tipi di base**|Aggiungere la gerarchia di interfacce o di classi base in modo ricorsivo.|
    |**Mostra tutti i tipi derivati**|Per una classe, aggiungere tutte le classi derivate in modo ricorsivo.<br /><br /> Per un'interfaccia, aggiungere tutte le interfacce derivate e implementare classi o struct in modo ricorsivo.|

     Per un **metodo** scegliere:

    |Opzione|Descrizione|
    |-|-|
    |**Mostra metodi chiamati**|Aggiungere metodi chiamati dal metodo specifico.|
    |**Mostra campi a cui fa riferimento**|Aggiungere i campi cui questo metodo fa riferimento.|
    |**Mostra tipo contenitore**|Aggiungere il tipo padre.|
    |**Mostra tipo, spazio dei nomi e assembly contenitore**|Aggiungere la gerarchia del contenitore padre.|
    |**Mostra metodi sottoposti a override**|Per un metodo che esegue l'override di altri metodi o implementa un metodo di interfaccia, aggiungere tutti i metodi astratti o virtuali nelle classi base sottoposte a override e, se disponibile, il metodo di interfaccia implementato.|

     Per un **campo** o una **proprietà** scegliere:

    |Opzione|Descrizione|
    |-|-|
    |**Mostra tipo contenitore**|Aggiungere il tipo padre.|
    |**Mostra tipo, spazio dei nomi e assembly contenitore**|Aggiungere la gerarchia del contenitore padre.|

    ![Mostra i metodi chiamati da questo membro](../modeling/media/codemapsshowrelatedmethods.png)

7. La mappa visualizza le relazioni. In questo esempio la mappa mostra i metodi chiamati dal metodo e `Find` la relativa posizione nella soluzione o esternamente.

   ![Mostra dipendenze specifiche su una mappa codici](../modeling/media/codemapsspecificdependenciesintro.png)

8. Per semplificare la mappa e concentrarsi sulle singole parti, scegliere **Filtri** nella barra degli strumenti della mappa codice e selezionare solo i tipi di nodi e di collegamenti desiderati. Ad esempio, disattivare la visualizzazione di Cartelle soluzione, Assembly e Spazi dei nomi.

   ![Usare il riquadro Filtro per semplificare la visualizzazione](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Vedi anche

- [Condividere mappe codice](share-code-maps.md)
- [Creare mappe codice per C++](code-maps-for-cpp.md)
- [Migliorare le prestazioni della mappa codice](code-maps-performance.md)
- [Video: Comprendere la progettazione dal codice con le mappe Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Video: Comprendere la progettazione dal codice con le mappe Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Mappare i metodi sullo stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Cercare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)
- [Personalizzare le mappe codice modificando i file DGML](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
