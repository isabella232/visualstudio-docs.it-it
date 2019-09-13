---
title: Mappe codice
ms.date: 05/16/2018
ms.topic: conceptual
f1_keywords:
- vs.progression.codemap
- vs.progression.standardgraphsdialog
helpviewer_keywords:
- DGML
- graph documents
- code visualization [Visual Studio]
- dependencies, visualizing
- dependency graphs
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5ecc8ae714dfb35281029a9d6e240a148e7c9511
ms.sourcegitcommit: b60a00ac3165364ee0e53f7f6faef8e9fe59ec4a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/11/2019
ms.locfileid: "70913350"
---
# <a name="map-dependencies-with-code-maps"></a>Eseguire il mapping delle dipendenze con le mappe codice

È possibile visualizzare le dipendenze nel codice creando una mappa codice. Le mappe codici consentono di visualizzare il modo in cui il codice si integra senza leggere file e righe di codice.

![Visualizzare le dipendenze con le mappe codice in Visual Studio](../modeling/media/codemapsmainintro.png)

Per creare e modificare le mappe del codice, è necessario Visual Studio Enterprise Edition. Nelle edizioni community e Professional di Visual Studio è possibile aprire i diagrammi generati in Enterprise Edition, ma non modificarli.

> [!NOTE]
> Prima di condividere le mappe create in Visual Studio Enterprise con altri utenti che usano Visual Studio Professional, assicurarsi che tutti gli elementi della mappa, ad esempio elementi nascosti, gruppi espansi e collegamenti tra gruppi, siano visibili.

È possibile eseguire il mapping delle dipendenze per il codice nei seguenti linguaggi:

- Visual C# o Visual Basic in una soluzione o in assembly (con*estensione dll* o *exe*)

- C o C++ codice nativo o gestito in progetti C++ visivi, file di intestazione ( *. h* o `#include`) o file binari

- Progetti X++ e assembly creati da moduli .NET per Microsoft Dynamics AX

> [!NOTE]
> Per i progetti diversi C# da o Visual Basic, sono disponibili meno opzioni per l'avvio di una mappa del codice o l'aggiunta di elementi a una mappa codice esistente. Ad esempio, non è possibile fare clic con il pulsante destro del mouse su un oggetto nell'editor di testo di un progetto C++ e aggiungerlo a una mappa codice. È tuttavia possibile trascinare e rilasciare singoli elementi di codice o file da **Esplora soluzioni**, **Visualizzazione classi**e **Visualizzatore oggetti**.

## <a name="install-code-map-and-live-dependency-validation"></a>Installare la mappa codice e la convalida delle dipendenze attive

Per creare una mappa del codice in Visual Studio, installare prima di tutto la **mappa codice** e i componenti di **convalida delle dipendenze in tempo reale** :

1. Aprire **programma di installazione di Visual Studio**. È possibile aprirlo dal menu Start di Windows o in Visual Studio scegliendo **strumenti** > **Ottieni strumenti e funzionalità**.

1. Selezionare la scheda **Singoli componenti**.

1. Scorrere verso il basso fino alla sezione **strumenti del codice** e selezionare **mappa del codice** e **convalida delle dipendenze in tempo reale**.

   ![Mappa del codice e componenti di convalida delle dipendenze in tempo reale in Programma di installazione di Visual Studio](media/modeling-components.png)

1. Selezionare **Modifica**.

   Viene avviata l'installazione dei componenti **mappa del codice** e **convalida delle dipendenze attive** . Potrebbe essere richiesto di chiudere Visual Studio.

## <a name="add-a-code-map"></a>Aggiungere una mappa codice

È possibile creare una mappa codice vuota e trascinare gli elementi su di essa, inclusi i riferimenti ad assembly, i file e le cartelle, oppure è possibile generare una mappa codice per tutta o parte della soluzione.

Per aggiungere una mappa codice vuota:

1. In **Esplora soluzioni**aprire il menu di scelta rapida per il nodo della soluzione di primo livello. Scegliere **Aggiungi** > **nuovo elemento**.

2. Nella finestra di dialogo **Aggiungi nuovo elemento** , in **installato**, scegliere la categoria **generale** .

3. Scegliere il modello **documento grafico diretto (con estensione dgml)** , quindi selezionare **Aggiungi**.

   > [!TIP]
   > Questo modello potrebbe non essere visualizzato in ordine alfabetico, quindi scorrere fino alla fine dell'elenco dei modelli se non lo si visualizza.

   Una mappa vuota viene visualizzata nella cartella **elementi di soluzione** della soluzione.

Analogamente, è possibile creare**un nuovo file**della mappa del codice senza aggiungerlo alla soluzione selezionando **architettura** > **nuova mappa codice** o **file** > **nuovo** > file.

## <a name="generate-a-code-map-for-your-solution"></a>Generare una mappa codice per la soluzione

Per visualizzare tutte le dipendenze nella soluzione:

1. Sulla barra dei menu scegliere **architettura** > **Genera mappa codici per la soluzione**. Se il codice non è stato modificato dall'ultima volta in cui è stato compilato, è possibile selezionare l' **architettura** > **Genera mappa codice per la soluzione senza compilazione** .

   ![Comando di generazione mappa del codice](../modeling/media/codemapsarchitecturemenu.png)

   Viene generata una mappa che Mostra gli assembly di primo livello e i relativi collegamenti aggregati. A una maggiore ampiezza del collegamento aggregato corrisponde un maggior numero di dipendenze che rappresenta.

2. Usare il pulsante **Legenda** sulla barra degli strumenti del codice per visualizzare o nascondere l'elenco di icone del tipo di progetto (ad esempio Test, Web e Progetto per telefono), gli elementi di codice (ad esempio Classi, Metodi e Proprietà) e i tipi di relazione (ad esempio Eredita da, Implementa e Chiamate).

   ![Grafico dipendenze di primo livello di assembly](../modeling/media/dependencygraph_toplevelassemblies.png)

   Questa soluzione di esempio contiene cartelle della soluzione (**Test** e **Componenti**), progetti di test, progetti Web e assembly. Per impostazione predefinita, tutte le relazioni del contenitore vengono visualizzate come *gruppi*che è possibile espandere e comprimere. Il gruppo **Esterni** contiene qualsiasi elemento esterno alla soluzione, incluse le dipendenze della piattaforma. Gli assembly esterni mostrano solo gli elementi usati. Per impostazione predefinita, i tipi di base del sistema sono nascosti sulla mappa per evitare confusione.

3. Per eseguire il drill-down nella mappa, espandere i gruppi che rappresentano progetti e assembly. Per espandere tutti gli elementi premere **CTRL+A** per selezionare tutti i nodi e quindi scegliere **Gruppo**, **Espandi** dal menu di scelta rapida.

   ![Espansione di tutti i gruppi in una mappa codici](../modeling/media/codemapsexpandallgroups.png)

4. Tuttavia, questa operazione potrebbe non essere utile per una soluzione di grandi dimensioni. Infatti, per soluzioni complesse, i limiti di memoria potrebbero impedire di espandere tutti i gruppi. In alternativa, per visualizzare gli elementi all'interno di un singolo nodo, espanderlo. Spostare il puntatore del mouse sopra il nodo, quindi scegliere il pulsante con la freccia di espansione (freccia giù) quando viene visualizzato.

   ![Espansione di un nodo in una mappa codici](../modeling/media/dependencygraph_containment.png)

   In alternativa, usare la tastiera selezionando l'elemento e premendo il tasto più ( **+** ). Per esplorare i livelli più profondi di codice, effettuare la stessa operazione per gli spazi dei nomi, i tipi e i membri.

   > [!TIP]
   > Per ulteriori informazioni sull'utilizzo di mappe del codice con il mouse, la tastiera e il tocco, vedere [Browse and rearrange Code Maps](../modeling/browse-and-rearrange-code-maps.md).

5. Per semplificare la mappa e concentrarsi sulle singole parti, scegliere **Filtri** nella barra degli strumenti della mappa codice e selezionare solo i tipi di nodi e di collegamenti desiderati. Ad esempio, è possibile nascondere tutti i contenitori di Cartella soluzione e Assembly.

   ![Semplificare la mappa filtrando i contenitori](../modeling/media/codemapsfilterfoldersassemblies.png)

   È anche possibile semplificare la mappa nascondendo o rimuovendo i singoli gruppi ed elementi dalla mappa, senza modificare il codice della soluzione sottostante.

6. Per visualizzare le relazioni tra elementi, selezionarle nella mappa. I colori dei collegamenti indicano i tipi di relazione, come mostrato nel riquadro **Legenda** .

   ![Visualizzare le dipendenze nelle soluzioni](../modeling/media/codemapsmainintro.png)

   In questo esempio, i collegamenti viola sono chiamate, i collegamenti punteggiati sono riferimenti e i collegamenti azzurro rappresentano l'accesso al campo. I collegamenti verdi possono essere ereditati o possono essere *collegamenti aggregati* che indicano più di un tipo di relazione (o *categoria*).

   > [!TIP]
   > Se viene visualizzato un collegamento verde, non necessariamente esiste solo una relazione di ereditarietà. Potrebbero essere presenti anche chiamate al metodo, nascoste dalla relazione di ereditarietà. Per visualizzare tipi specifici di collegamenti, usare le caselle di controllo nel riquadro **filtri** per nascondere i tipi a cui non si è interessati.

7. Per altre informazioni su un elemento o un collegamento, spostare il puntatore su di esso finché non viene visualizzata una descrizione comando. In questo modo vengono mostrati i dettagli di un elemento di codice o delle categorie rappresentate da un collegamento.

   ![Mostra le categorie di una relazione](../modeling/media/codemapsshowlinkcatgories.png)

8. Per esaminare gli elementi e le dipendenze rappresentate da un collegamento di aggregazione, prima selezionare il collegamento, quindi aprire il relativo menu di scelta rapida. Scegliere **Mostra collegamenti partecipanti** (o **Mostra collegamenti partecipanti sulla nuova mappa codice**). I gruppi vengono espansi a entrambe le estremità del collegamento e vengono mostrati solo gli elementi e le dipendenze che partecipano al collegamento.

9. Per concentrarsi su parti specifiche della mappa, è possibile continuare a rimuovere gli elementi a cui non si è interessati. Ad esempio, per analizzare la visualizzazione delle classi e dei membri, è sufficiente filtrare tutti i nodi dello spazio dei nomi nel riquadro **Filtri** .

   ![Drill-down dei gruppi a livello di classe e membro](../modeling/media/dependencygraph_expandedselectedgroups_2012.png)

10. Un altro modo per concentrarsi sulla mappa di soluzione complessa consiste nel generare una nuova mappa contenente gli elementi selezionati da una mappa esistente. Tenere premuto **CTRL** mentre si selezionano gli elementi su cui si vuole concentrarsi, aprire il menu di scelta rapida e scegliere **nuovo grafico dalla selezione**.

    ![Mostra gli elementi selezionati in una nuova mappa codici](../modeling/media/codemapsshowonnewmap.png)

11. Il contesto contenitore viene trasferito alla nuova mappa. Nascondere le cartelle della soluzione e tutti gli altri contenitori che non si vuole visualizzare tramite il riquadro **filtri** .

    ![Filtrare i contenitori per semplificare la visualizzazione](../modeling/media/codemapsexpandnewgroups.png)

12. Espandere i gruppi e selezionare gli elementi della mappa per visualizzare le relazioni.

    ![Selezionare gli elementi per visualizzare le relazioni](../modeling/media/codemapsviewnewrelationships.png)

Vedere anche:

- [Cercare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)
- [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
- Individuare potenziali problemi nel codice eseguendo [un analizzatore](../modeling/find-potential-problems-using-code-map-analyzers.md)

## <a name="view-specific-dependencies-in-a-code-map"></a>Visualizzare dipendenze specifiche in una mappa codice

Si supponga di dover eseguire una revisione del codice in alcuni file con modifiche in sospeso. Per visualizzare le dipendenze in queste modifiche, è possibile creare una mappa codice da tali file.

   ![Mostra dipendenze specifiche su una mappa codici](../modeling/media/codemapsspecificdependenciesintro.png)

1. In **Esplora soluzioni**selezionare i progetti, i riferimenti agli assembly, le cartelle, i file, i tipi o i membri di cui si desidera eseguire il mapping.

   ![Selezionare gli elementi da mappare](../modeling/media/codemapsselectinsolutionexplorer.png)

1. Sulla barra degli strumenti **Esplora soluzioni** scegliere **Mostra in mappa** ![codici crea nuovo grafico dal pulsante](../modeling/media/createnewgraphfromselectedbutton.gif)nodi selezionati. In alternativa, aprire il menu di scelta rapida per uno o un gruppo di elementi e scegliere **Mostra in mappa codici**.

   È anche possibile trascinare elementi da **Esplora soluzioni**, **Visualizzazione classi**o **Visualizzatore oggetti**in una mappa codice [nuova](#add-a-code-map) o esistente. Per includere la gerarchia padre per gli elementi, tenere premuto il tasto **CTRL** mentre si trascinano gli elementi oppure usare il pulsante **Includi padri** sulla barra degli strumenti della mappa codice per specificare l'azione predefinita. È anche possibile trascinare i file di assembly dall'esterno di Visual Studio, ad esempio da **Esplora risorse**.

   > [!NOTE]
   > Quando si aggiungono elementi da un progetto condiviso tra più app, ad esempio Windows Phone o Microsoft Store, tali elementi vengono visualizzati nella mappa con il progetto di app attualmente attivo. Se si cambia il contesto passando a un altro progetto di applicazione e si aggiungono altri elementi dal progetto condiviso, tali elementi vengono visualizzati con il nuovo progetto di applicazione attivo. Le operazioni eseguite con un elemento nella mappa si applicano solo agli elementi che condividono lo stesso contesto.

3. La mappa visualizza gli elementi selezionati all'interno degli assembly in cui sono contenuti.

   ![Elementi selezionati visualizzati come gruppi sulla mappa](../modeling/media/codemapsshowitemsfromsolnexplorer.png)

4. Per esplorare gli elementi, espanderli. Spostare il puntatore del mouse sopra un elemento, quindi scegliere il pulsante con la freccia di espansione (freccia Giù) quando viene visualizzato.

   ![Espandere un nodo in una mappa codice](../modeling/media/dependencygraph_containment.png)

   Per espandere tutti gli elementi, selezionarli **usando Ctrl**+**A**, quindi aprire il menu di scelta rapida per la mappa e scegliere**Espandi** **gruppo** > . Tuttavia, questa opzione non è disponibile se l'espansione di tutti i gruppi crea una mappa inutilizzabile o problemi di memoria.

5. Continuare a espandere gli elementi a cui si è interessati, fino al livello di classe e membro, se necessario.

   ![Espandere i gruppi a livello di classe e membro](../modeling/media/codemapsexpandtoclassandmember.png)

   Per visualizzare i membri presenti nel codice ma che non vengono visualizzati sulla mappa, fare clic sull'icona](../modeling/media/dependencygraph_deletednodesicon.png) **Recupera** nuovamente ![i figli icona Riprendi figli nell'angolo in alto a sinistra di un gruppo.

6. Per visualizzare più elementi correlati a quelli sulla mappa, selezionarne uno e scegliere **Mostra correlati** nella barra degli strumenti della mappa codice, quindi selezionare il tipo di elementi correlati da aggiungere alla mappa. In alternativa, selezionare uno o più elementi, aprire il menu di scelta rapida, quindi scegliere l'opzione **Mostra** per il tipo di elementi correlati da aggiungere alla mappa. Ad esempio:

    Per un **assembly**scegliere:

    |||
    |-|-|
    |**Mostra assembly a cui fa riferimento**|Aggiungere gli assembly a cui fa riferimento questo assembly. Gli assembly esterni vengono visualizzati nel gruppo **Esterni** .|
    |**Mostra assembly che fanno riferimento a**|Aggiungere gli assembly della soluzione che fanno riferimento a questo assembly.|

    Per uno **spazio dei nomi**scegliere **Mostra assembly contenitore**, se non è visibile.

    Per una **classe** o un' **interfaccia**scegliere:

    |||
    |-|-|
    |**Mostra tipi base**|Per una classe, aggiungere la classe base e le interfacce implementate.<br /><br /> Per un'interfaccia, aggiungere le interfacce di base.|
    |**Mostra tipi derivati**|Per una classe, aggiungere le classi derivate.<br /><br /> Per un'interfaccia, aggiungere le interfacce derivate e le classi o gli struct implementati.|
    |**Mostra tipi a cui fa riferimento**|Aggiungere tutte le classi e i membri usati.|
    |**Mostra tipi che fanno riferimento a**|Aggiungere tutte le classi e membri che usano la classe.|
    |**Mostra spazio dei nomi contenitore**|Aggiungere lo spazio dei nomi del padre.|
    |**Mostra spazio dei nomi e assembly contenitore**|Aggiungere la gerarchia del contenitore padre.|
    |**Mostra tutti i tipi di base**|Aggiungere la gerarchia di interfacce o di classi base in modo ricorsivo.|
    |**Mostra tutti i tipi derivati**|Per una classe, aggiungere tutte le classi derivate in modo ricorsivo.<br /><br /> Per un'interfaccia, aggiungere tutte le interfacce derivate e implementare classi o struct in modo ricorsivo.|

     Per un **metodo**scegliere:

    |||
    |-|-|
    |**Mostra metodi chiamati**|Aggiungere metodi chiamati dal metodo specifico.|
    |**Mostra campi a cui fa riferimento**|Aggiungere i campi cui questo metodo fa riferimento.|
    |**Mostra tipo contenitore**|Aggiungere il tipo padre.|
    |**Mostra tipo, spazio dei nomi e assembly contenitore**|Aggiungere la gerarchia del contenitore padre.|
    |**Mostra metodi sottoposti a override**|Per un metodo che esegue l'override di altri metodi o implementa un metodo di interfaccia, aggiungere tutti i metodi astratti o virtuali nelle classi base sottoposte a override e, se disponibile, il metodo di interfaccia implementato.|

     Per un **campo** o una **proprietà**scegliere:

    |||
    |-|-|
    |**Mostra tipo contenitore**|Aggiungere il tipo padre.|
    |**Mostra tipo, spazio dei nomi e assembly contenitore**|Aggiungere la gerarchia del contenitore padre.|

    ![Mostra i metodi chiamati da questo membro](../modeling/media/codemapsshowrelatedmethods.png)

7. La mappa visualizza le relazioni. In questo esempio la mappa mostra i metodi chiamati dal `Find` metodo e la relativa posizione nella soluzione o esternamente.

   ![Mostra dipendenze specifiche su una mappa codici](../modeling/media/codemapsspecificdependenciesintro.png)

8. Per semplificare la mappa e concentrarsi sulle singole parti, scegliere **Filtri** nella barra degli strumenti della mappa codice e selezionare solo i tipi di nodi e di collegamenti desiderati. Ad esempio, disattivare la visualizzazione di Cartelle soluzione, Assembly e Spazi dei nomi.

   ![Usare il riquadro Filtro per semplificare la visualizzazione](../modeling/media/almcodemapfilterpane.png)

## <a name="see-also"></a>Vedere anche

- [Video: Comprendere la progettazione dal codice con le mappe codici di Visual Studio 2015](https://channel9.msdn.com/Events/Visual-Studio/Connect-event-2015/502)
- [Usare le mappe del codice per eseguire il debug delle applicazioni](../modeling/use-code-maps-to-debug-your-applications.md)
- [Eseguire il mapping dei metodi nello stack di chiamate durante il debug](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md)
- [Trovare problemi potenziali usando gli analizzatore delle mappe del codice](../modeling/find-potential-problems-using-code-map-analyzers.md)
- [Cercare e ridisporre le mappe del codice](../modeling/browse-and-rearrange-code-maps.md)
- [Customize code maps by editing the DGML files](../modeling/customize-code-maps-by-editing-the-dgml-files.md)
