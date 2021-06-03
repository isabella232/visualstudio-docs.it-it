---
title: IntelliSense per C#
description: Informazioni su alcune funzionalità di IntelliSense che è possibile usare durante la codifica del progetto C#.
ms.custom: SEO-VS-2020
ms.date: 06/01/2021
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: mikadumont
ms.author: midumont
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 3156b1236a130478d83fe82c8fa462a1144a8e6a
ms.sourcegitcommit: f50bbdb15c4f9fca0fa245ca765183c378960cc5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2021
ms.locfileid: "111351955"
---
# <a name="c-intellisense"></a>IntelliSense per C#

IntelliSense C# è disponibile quando si codifica nell'editor e durante il debug nella finestra [di comando in](../ide/reference/immediate-window.md) modalità immediata.

## <a name="completion-lists"></a>Elenchi di completamento

Gli elenchi di completamento di IntelliSense in C# contengono token di Elenca membri, Completa parola e altri ancora. Forniscono funzionalità di accesso rapido a:

- Membri di un tipo o spazio dei nomi

- Nomi di variabili, comandi e funzioni

- Frammenti di codice

- Parole chiave del linguaggio

- Metodi di estensione

L'elenco di completamento in C# può escludere i token irrilevanti e preselezionare quelli pertinenti al contesto. Per altre informazioni, vedere [Elenchi di completamento filtrati.](#filtered-completion-lists)

### <a name="code-snippets-in-completion-lists"></a>Frammenti di codice negli elenchi di completamento

In C#, l'elenco di completamento include frammenti di codice che consentono di inserire facilmente corpi predefiniti di codice nel programma. I frammenti di codice vengono visualizzati nell'elenco di completamento come [testo del collegamento](../ide/code-snippets-schema-reference.md#shortcut-element) del frammento di codice. Per altre informazioni sui frammenti di codice disponibili in C# per impostazione predefinita, vedere Frammenti [di codice C#.](../ide/visual-csharp-code-snippets.md)

### <a name="language-keywords-in-completion-lists"></a>Parole chiave del linguaggio negli elenchi di completamento

In C#, l'elenco di completamento include anche le parole chiave del linguaggio. Per altre informazioni sulle parole chiave del linguaggio C#, vedere Parole [chiave C#.](/dotnet/csharp/language-reference/keywords/index)

### <a name="extension-methods-in-completion-lists"></a>Metodi di estensione negli elenchi di completamento

In C# l'elenco di completamento include i metodi estensione che rientrano nell'ambito.

> [!NOTE]
> Nell'elenco di completamento non vengono visualizzati tutti i metodi di estensione degli oggetti <xref:System.String>.

I metodi di estensione usano un'icona diversa rispetto ai metodi di istanza. Per una guida di riferimento all'elenco di icone, vedere [Icone di Visualizzazione classi e Visualizzatore oggetti](../ide/class-view-and-object-browser-icons.md). Se un metodo di istanza e un metodo di estensione con lo stesso nome sono entrambi inclusi in un ambito, nell'elenco di completamento viene visualizzata l'icona del metodo di estensione.

### <a name="filtered-completion-lists"></a>Elenchi di completamento filtrati

I membri non necessari vengono rimossi dall'elenco di completamento IntelliSense usando dei filtri. In C# vengono filtrati gli elenchi di completamento disponibili per le voci riportate di seguito:

- **Interfacce e classi di base**: IntelliSense rimuove automaticamente le voci dagli elenchi di completamento per interfacce e classi base, sia negli elenchi di interfacce e di dichiarazioni di classe base sia negli elenchi di vincoli. Le enumerazioni, ad esempio, non vengono visualizzate nell'elenco di completamento delle classi base perché non possono essere usate per tali classi. L'elenco di completamento delle classi base contiene solo interfacce e spazi dei nomi. Se si seleziona una voce nell'elenco e si digita una virgola, IntelliSense rimuove le classi di base dall'elenco di completamento perché C# non supporta l'ereditarietà multipla. Lo stesso comportamento si verifica anche per le clausole di vincoli.

- **Attributi**: quando si applica un attributo a un tipo, l'elenco di completamento viene filtrato in modo da contenere solo i tipi che discendono dagli spazi dei nomi contenenti tali tipi, ad esempio <xref:System.Attribute>.

- **Clausole catch**

- **Inizializzatori di oggetto**: solo i membri che possono essere inizializzati verranno visualizzati nell'elenco di completamento.

- **Nuova parola chiave**: quando si digita `new` e si preme la **BARRA SPAZIATRICE**, viene visualizzato un elenco di completamento. In base al contesto del codice, viene selezionata automaticamente una voce nell'elenco. Per le dichiarazioni e per le istruzioni return nei metodi, ad esempio, vengono selezionate automaticamente delle voci nell'elenco di completamento.

- **Parola chiave di enumerazione**: quando si preme la **BARRA SPAZIATRICE** dopo il segno di uguale per un'assegnazione di enumerazione, viene visualizzato un elenco di completamento. In base al contesto del codice, viene selezionata automaticamente una voce nell'elenco. Dopo aver digitato la parola chiave return e quando si crea una dichiarazione, ad esempio, le voci nell'elenco di completamento vengono selezionate automaticamente.

- **Operatori as e is**: quando si preme la **BARRA SPAZIATRICE** dopo aver digitato la parola chiave `as` o `is` viene visualizzato automaticamente un elenco di completamento filtrato.

- **Eventi**: quando si digita la parola chiave `event` l'elenco di completamento contiene solo tipi delegati.

- Il **parametro help** consente di ordinare automaticamente il primo overload di metodo corrispondente ai parametri immessi. Se sono disponibili più overload di metodi, è possibile usare le frecce verso l'alto e verso il basso per selezionare il successivo overload possibile in elenco.

### <a name="most-recently-used-members"></a>Membri utilizzati più di recente

IntelliSense memorizza i membri recentemente selezionati nella casella popup [Elenca membri](../ide/using-intellisense.md) per il completamento del nome oggetto automatico. Al successivo utilizzo di **Elenco membri,** nella parte superiore vengono visualizzati i membri usati più di recente. La cronologia dei membri usati più di recente viene cancellata tra ogni sessione di Visual Studio.

### <a name="override"></a>override

Quando si digita [override](/dotnet/csharp/language-reference/keywords/override) e si preme la **BARRA SPAZIATRICE**, IntelliSense visualizza in una casella dell'elenco popup tutti i membri validi della classe di base di cui è possibile eseguire l'override. Se si digita il tipo restituito del metodo dopo `override`, IntelliSense mostra solo i metodi che restituiscono lo stesso tipo. Se non vengono trovate corrispondenze, IntelliSense visualizza tutti i membri della classe di base.

### <a name="ai-enhanced-intellisense"></a>IntelliSense migliorato per intelligenza artificiale

[Visual Studio IntelliCode](/visualstudio/intellicode/intellicode-visual-studio) include elenchi di completamento di IntelliSense migliorati per intelligenza artificiale. IntelliCode prevede l'API più idonea da usare, invece di presentare semplicemente un elenco alfabetico di membri. Usa il contesto e i criteri del codice correnti per fornire l'elenco dinamico.

## <a name="automatic-code-generation"></a>Generazione automatica di codice

### <a name="add-using"></a>Aggiungi using

L'operazione **Aggiungi using** di IntelliSense aggiunge automaticamente la direttiva `using` richiesta al file di codice. Questa funzione consente di restare concentrati sul codice che si sta scrivendo anziché passare a un'altra parte del codice.

Per avviare **l'operazione Aggiungi using,** posizionare il cursore su un riferimento al tipo che non può essere risolto. Ad esempio, quando si crea un'applicazione console e si aggiunge `XmlReader` al corpo del metodo `Main`, nella riga di codice appare una sottolineatura ondulata rossa per indicare che non è possibile risolvere il riferimento al tipo. È quindi possibile richiamare **Aggiungi using** con le **Azione rapide**. Le **Azioni rapide** sono visibili solo quando il cursore è posizionato sul tipo non associato.

![Immagine ampliata Aggiungi using, azione rapida](../ide/media/addusing-quickaction.png)

Fare clic sull'icona di lampadina di errore, quindi scegliere **using System.Xml;** per aggiungere automaticamente la direttiva using.

### <a name="add-missing-using-directives-on-paste"></a>Aggiungi direttive using mancanti dopo operazione Incolla

IntelliSense può aggiungere automaticamente direttive mancanti al codice `using` quando si incolla un tipo nel file di codice. Questa funzionalità consente di risparmiare tempo automatizzando l'attività di aggiunta di direttive using mancanti quando si incolla un tipo in un file. Abilitare questa funzionalità in **Strumenti**  >  **Opzioni**  >  **Editor di testo**  >  **C#** o **Avanzate**  >   di base e selezionare Aggiungi direttive using mancanti in Incolla .

### <a name="remove-and-sort-usings"></a>Opzione Rimuovi e ordina using

L'opzione **Rimuovi e ordina using** consente di ordinare e rimuovere le dichiarazioni `using` e `extern` senza modificare il comportamento del codice sorgente. Nel tempo i file di origine possono diventare troppo grandi e difficili da leggere a causa di direttive `using` superflue e non organizzate. L'opzione **Rimuovi e ordina using** compatta il codice sorgente rimuovendo le direttive `using` inutilizzate e migliora la leggibilità mettendole in ordine. Dal menu **Modifica** scegliere **IntelliSense** e **Organizza using**.

### <a name="implement-interface"></a>Implementare l'interfaccia

IntelliSense offre un'opzione che consente di implementare [un'interfaccia](/dotnet/csharp/language-reference/keywords/interface) mentre si lavora nell'editor di codice. Per implementare correttamente un'interfaccia è in genere necessario creare una dichiarazione di metodo per ogni membro dell'interfaccia della classe. Usando IntelliSense, dopo aver digitato il nome di un'interfaccia in una dichiarazione di classe, viene visualizzata la lampadina delle **Azioni rapide**. La lampadina offre la possibilità di implementare automaticamente l'interfaccia, usando la denominazione esplicita o implicita. Se si usa la denominazione esplicita, le dichiarazioni dei metodi includono il nome dell'interfaccia. Se si usa la denominazione implicita, le dichiarazioni dei metodi non indicano l'interfaccia a cui appartengono. Un metodo di interfaccia con denominazione esplicita è accessibile solo tramite un'istanza di interfaccia e non tramite un'istanza di classe. Per altre informazioni, vedere Implementazione esplicita [dell'interfaccia](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Il comando Implementa interfaccia genera il numero minimo di stub di metodo necessario per soddisfare l'interfaccia. Se una classe di base implementa parti dell'interfaccia, tali stub non verranno rigenerati.

### <a name="implement-abstract-base-class"></a>Implementare una classe di base astratta

IntelliSense offre un'opzione che consente di implementare automaticamente i membri di una classe di base astratta mentre si usa l'editor del codice. Per implementare i membri di una classe base astratta è in genere necessario creare una nuova definizione di metodo per ciascun metodo della classe base astratta nella classe derivata. Usando IntelliSense, dopo aver digitato il nome di una classe di base astratta in una dichiarazione di classe, viene visualizzata la lampadina delle **Azioni rapide**. La lampadina offre la possibilità di implementare automaticamente i metodi della classe di base.

Gli stub dei metodi generati dalla funzionalità Implementa classe **di base** astratta sono modellati dal frammento di codice definito nel file *MethodStub.snippet.* I frammenti di codice sono modificabili. Per altre informazioni, vedere [Procedura dettagliata: Creazione di un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generazione dall'utilizzo

La funzionalità di **generazione dall'utilizzo** consente di usare le classi e i membri prima di definirli. È possibile generare uno stub per qualsiasi classe, costruttore, metodo, proprietà, campo o enumerazione che si desidera utilizzare, ma che non è ancora stato definito. È possibile generare nuovi tipi e membri senza abbandonare la posizione corrente nel codice. Ciò riduce al minimo l'interruzione del flusso di lavoro.

Viene visualizzata una sottolineatura ondulata rossa sotto ogni identificatore non definito. Quando si posiziona il puntatore del mouse sull'identificatore, viene visualizzato un messaggio di errore in una descrizione comando. Per visualizzare le opzioni appropriate, è possibile utilizzare le procedure seguenti:

- Fare clic sull'identificatore non definito. Verrà visualizzata la lampadina di errore di **Azioni rapide** sotto l'identificatore. Fare clic sulla lampadina di errore.

- Fare clic sull'identificatore non definito e quindi premere + **CTRL.** (**CTRL** + punto).

- Fare clic con il pulsante destro del mouse sull'identificatore non definito e quindi scegliere **Azioni rapide e refactoring**.

Le opzioni visualizzate possono includere quanto segue:

- **Genera proprietà**

- **Genera campo**

- **Generare un metodo**

- **Genera classe**

- **Genera nuovo tipo** (per una classe, struct, interfaccia o enumerazione)

## <a name="generate-event-handlers"></a>Genera gestori eventi

Nell'editor del codice IntelliSense consente di agganciare i metodi (gestori di eventi) a campi evento.

Quando si digita l'operatore dopo un campo evento in un file con estensione `+=` *cs,* IntelliSense richiede di premere **TAB.** Questa operazione consente di inserire una nuova istanza di un delegato che punta al metodo che gestisce l'evento.

![Associazione automatica dei pulsanti](../ide/media/vxautohookup.gif)

Se si preme **TAB,** IntelliSense completa automaticamente l'istruzione e visualizza il riferimento al gestore eventi come testo selezionato nell'editor di codice. Per completare l'associazione automatica degli eventi, IntelliSense richiede di premere di nuovo **TAB** per creare uno stub vuoto per il gestore eventi.

![Gestore eventi di generazione](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> Se un nuovo delegato creato da IntelliSense fa riferimento a un gestore eventi esistente, IntelliSense comunica queste informazioni nella descrizione comando. È quindi possibile modificare questo riferimento. Il testo è già selezionato nell'editor del codice. In caso contrario, l'associazione automatica dell'evento è a questo punto completata.

Se si preme **TAB,** IntelliSense esegue lo stub di un metodo con la firma corretta e inserisce il cursore nel corpo del gestore eventi.

> [!NOTE]
> Usare il **comando Indietro** nel menu **Visualizza** (**CTRL**) per + **-** tornare all'istruzione di collegamento all'evento.

## <a name="see-also"></a>Vedi anche

- [Usare IntelliSense](../ide/using-intellisense.md)
- [IDE di Visual Studio](../get-started/visual-studio-ide.md)
