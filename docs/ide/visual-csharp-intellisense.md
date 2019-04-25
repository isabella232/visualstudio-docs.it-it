---
title: IntelliSense per C#
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- C#, IntelliSense
- IntelliSense [C#]
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: ef4f8974f448ad9e2e81d4f1ba98aa02ed9da354
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62581950"
---
# <a name="c-intellisense"></a>IntelliSense per C#

IntelliSense per C# è disponibile durante la scrittura del codice nell'editor e durante il debug nella finestra di comando [Modalità immediata](../ide/reference/immediate-window.md).

## <a name="completion-lists"></a>Elenchi di completamento

Gli elenchi di completamento di IntelliSense in C# contengono token di Elenca membri, Completa parola e altri ancora. Forniscono funzionalità di accesso rapido a:

- Membri di un tipo o spazio dei nomi

- Nomi di variabili, comandi e funzioni

- Frammenti di codice

- Parole chiave del linguaggio

- Metodi di estensione

L'elenco di completamento in C# può escludere i token irrilevanti e preselezionare quelli pertinenti al contesto. Per altre informazioni, vedere [Elenchi di completamento filtrati](#filtered-completion-lists).

### <a name="code-snippets-in-completion-lists"></a>Frammenti di codice negli elenchi di completamento

In C#, l'elenco di completamento include frammenti di codice che consentono di inserire facilmente corpi predefiniti di codice nel programma. I frammenti di codice vengono visualizzati nell'elenco di completamento come [testo del collegamento](../ide/code-snippets-schema-reference.md#shortcut-element) del frammento di codice. Per altre informazioni sui frammenti di codice disponibili per impostazione predefinita in C#, vedere [Frammenti di codice C#](../ide/visual-csharp-code-snippets.md).

### <a name="language-keywords-in-completion-lists"></a>Parole chiave del linguaggio negli elenchi di completamento

In C#, l'elenco di completamento include anche le parole chiave del linguaggio. Per altre informazioni sulle parole chiave del linguaggio C#, vedere [Parole chiave di C#](/dotnet/csharp/language-reference/keywords/index).

### <a name="extension-methods-in-completion-lists"></a>Metodi di estensione negli elenchi di completamento

In C# l'elenco di completamento include i metodi estensione che rientrano nell'ambito.

> [!NOTE]
> Nell'elenco di completamento non vengono visualizzati tutti i metodi di estensione degli oggetti <xref:System.String>.

I metodi di estensione usano un'icona diversa rispetto ai metodi di istanza. Per una guida di riferimento all'elenco di icone, vedere [Icone di Visualizzazione classi e Visualizzatore oggetti](../ide/class-view-and-object-browser-icons.md). Se un metodo di istanza e un metodo di estensione con lo stesso nome sono entrambi inclusi in un ambito, nell'elenco di completamento viene visualizzata l'icona del metodo di estensione.

### <a name="filtered-completion-lists"></a>Elenchi di completamento filtrati

I membri non necessari vengono rimossi dall'elenco di completamento IntelliSense usando dei filtri. In C# vengono filtrati gli elenchi di completamento disponibili per le voci riportate di seguito:

- **Interfacce e classi di base**: Vengono rimosse le voci dagli elenchi di completamento IntelliSense per interfacce e classi base, sia negli elenchi di interfacce e di dichiarazioni di classe base sia negli elenchi di vincoli. Le enumerazioni, ad esempio, non vengono visualizzate nell'elenco di completamento delle classi base perché non possono essere usate per tali classi. L'elenco di completamento delle classi base contiene solo interfacce e spazi dei nomi. Se si seleziona una voce nell'elenco e si digita una virgola, IntelliSense rimuove le classi di base dall'elenco di completamento perché C# non supporta l'ereditarietà multipla. Lo stesso comportamento si verifica anche per le clausole di vincoli.

- **Attributi**: Quando si applica un attributo a un tipo, l'elenco di completamento viene filtrato in modo da contenere solo quei tipi che discendono dagli spazi dei nomi contenenti tali tipi, ad esempio <xref:System.Attribute>.

- **Clausole catch**

- **Inizializzatori di oggetti**: Solo i membri che possono essere inizializzati verranno visualizzati nell'elenco di completamento.

- **Parola chiave new**: Quando si digita `new` e poi si preme la **Barra spaziatrice**, viene visualizzato un elenco di completamento. In base al contesto del codice, viene selezionata automaticamente una voce nell'elenco. Per le dichiarazioni e per le istruzioni return nei metodi, ad esempio, vengono selezionate automaticamente delle voci nell'elenco di completamento.

- **Parola chiave enum**: Quando si preme la **Barra spaziatrice** dopo il segno di uguale per un'assegnazione enum, viene visualizzato un elenco di completamento. In base al contesto del codice, viene selezionata automaticamente una voce nell'elenco. Dopo aver digitato la parola chiave return e quando si crea una dichiarazione, ad esempio, le voci nell'elenco di completamento vengono selezionate automaticamente.

- **Operatori as e is**: Quando si preme la **Barra spaziatrice** dopo aver digitato la parola chiave `as` o `is`, viene visualizzato automaticamente un elenco di completamento.

- **Eventi**: Quando si digita la parola chiave `event` l'elenco di completamento contiene solo tipi delegati.

- Il **parametro help** consente di ordinare automaticamente il primo overload di metodo corrispondente ai parametri immessi. Se sono disponibili più overload di metodi, è possibile usare le frecce verso l'alto e verso il basso per selezionare il successivo overload possibile in elenco.

### <a name="most-recently-used-members"></a>Membri utilizzati più di recente

IntelliSense memorizza i membri recentemente selezionati nella casella popup [Elenca membri](../ide/using-intellisense.md) per il completamento del nome oggetto automatico. Al successivo utilizzo di **Elenco membri**, i membri usati di recente vengono visualizzati nella parte superiore. La cronologia dei membri usati più di recente viene cancellata tra ogni sessione di Visual Studio.

### <a name="override"></a>override

Quando si digita [override](/dotnet/csharp/language-reference/keywords/override) e si preme la **BARRA SPAZIATRICE**, IntelliSense visualizza in una casella dell'elenco popup tutti i membri validi della classe di base di cui è possibile eseguire l'override. Se si digita il tipo restituito del metodo dopo `override`, IntelliSense mostra solo i metodi che restituiscono lo stesso tipo. Se non vengono trovate corrispondenze, IntelliSense visualizza tutti i membri della classe di base.

### <a name="ai-enhanced-intellisense"></a>IntelliSense migliorato per intelligenza artificiale

È possibile installare un'[estensione IntelliCode](/visualstudio/intellicode/intellicode-visual-studio) sperimentale per Visual Studio che fornisce elenchi di completamento di IntelliSense migliorati per intelligenza artificiale. Questa estensione prevede l'API più idonea da usare, invece di presentare semplicemente un elenco alfabetico di membri. Usa il contesto e i criteri del codice correnti per fornire l'elenco dinamico.

## <a name="automatic-code-generation"></a>Generazione automatica di codice

### <a name="add-using"></a>Aggiungi using

L'operazione **Aggiungi using** di IntelliSense aggiunge automaticamente la direttiva `using` richiesta al file di codice. Questa funzione consente di restare concentrati sul codice che si sta scrivendo anziché passare a un'altra parte del codice.

Per avviare l'operazione **Aggiungi using**, posizionare il cursore sul riferimento a un tipo che non può essere risolto. Ad esempio, quando si crea un'applicazione console e si aggiunge `XmlReader` al corpo del metodo `Main`, nella riga di codice appare una sottolineatura ondulata rossa per indicare che non è possibile risolvere il riferimento al tipo. È quindi possibile richiamare **Aggiungi using** con le **Azione rapide**. Le **Azioni rapide** sono visibili solo quando il cursore è posizionato sul tipo non associato.

![Immagine ampliata Aggiungi using, azione rapida](../ide/media/addusing-quickaction.png)

Fare clic sull'icona di lampadina di errore, quindi scegliere **using System.Xml;** per aggiungere automaticamente la direttiva using.

### <a name="remove-and-sort-usings"></a>Opzione Rimuovi e ordina using

L'opzione **Rimuovi e ordina using** consente di ordinare e rimuovere le dichiarazioni `using` e `extern` senza modificare il comportamento del codice sorgente. Nel tempo i file di origine possono diventare troppo grandi e difficili da leggere a causa di direttive `using` superflue e non organizzate. L'opzione **Rimuovi e ordina using** compatta il codice sorgente rimuovendo le direttive `using` inutilizzate e migliora la leggibilità mettendole in ordine. Dal menu **Modifica** scegliere **IntelliSense** e **Organizza using**.

### <a name="implement-interface"></a>Implementare l'interfaccia

IntelliSense offre un'opzione che consente di implementare un'[interfaccia](/dotnet/csharp/language-reference/keywords/interface) mentre si usa l'editor del codice. Per implementare correttamente un'interfaccia è in genere necessario creare una dichiarazione di metodo per ogni membro dell'interfaccia della classe. Usando IntelliSense, dopo aver digitato il nome di un'interfaccia in una dichiarazione di classe, viene visualizzata la lampadina delle **Azioni rapide**. La lampadina offre la possibilità di implementare automaticamente l'interfaccia, usando la denominazione esplicita o implicita. Se si usa la denominazione esplicita, le dichiarazioni dei metodi includono il nome dell'interfaccia. Se si usa la denominazione implicita, le dichiarazioni dei metodi non indicano l'interfaccia a cui appartengono. Un metodo di interfaccia con denominazione esplicita è accessibile solo tramite un'istanza di interfaccia e non tramite un'istanza di classe. Per altre informazioni, vedere [Implementazione esplicita dell'interfaccia](/dotnet/csharp/programming-guide/interfaces/explicit-interface-implementation).

Il comando Implementa interfaccia genera il numero minimo di stub di metodo necessario per soddisfare l'interfaccia. Se una classe di base implementa parti dell'interfaccia, tali stub non verranno rigenerati.

### <a name="implement-abstract-base-class"></a>Implementare una classe di base astratta

IntelliSense offre un'opzione che consente di implementare automaticamente i membri di una classe di base astratta mentre si usa l'editor del codice. Per implementare i membri di una classe base astratta è in genere necessario creare una nuova definizione di metodo per ciascun metodo della classe base astratta nella classe derivata. Usando IntelliSense, dopo aver digitato il nome di una classe di base astratta in una dichiarazione di classe, viene visualizzata la lampadina delle **Azioni rapide**. La lampadina offre la possibilità di implementare automaticamente i metodi della classe di base.

Gli stub di metodo generati con la funzionalità **Implementare una classe di base astratta** vengono modellati in base al frammento di codice definito nel file *MethodStub.snippet*. I frammenti di codice sono modificabili. Per altre informazioni, vedere [Procedura dettagliata: Creare un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md).

### <a name="generate-from-usage"></a>Generazione dall'utilizzo

La funzionalità di **generazione dall'utilizzo** consente di usare le classi e i membri prima di definirli. È possibile generare uno stub per qualsiasi classe, costruttore, metodo, proprietà, campo o enumerazione che si desidera utilizzare, ma che non è ancora stato definito. È possibile generare nuovi tipi e membri senza abbandonare la posizione corrente nel codice. Ciò riduce al minimo l'interruzione del flusso di lavoro.

Viene visualizzata una sottolineatura ondulata rossa sotto ogni identificatore non definito. Quando si posiziona il puntatore del mouse sull'identificatore, viene visualizzato un messaggio di errore in una descrizione comando. Per visualizzare le opzioni appropriate, è possibile utilizzare le procedure seguenti:

- Fare clic sull'identificatore non definito. Verrà visualizzata la lampadina di errore di **Azioni rapide** sotto l'identificatore. Fare clic sulla lampadina di errore.

- Fare clic sull'identificatore non definito e premere **CTRL**+**.** (**CTRL** + punto).

- Fare clic con il pulsante destro del mouse sull'identificatore non definito e quindi scegliere **Azioni rapide e refactoring**.

Le opzioni visualizzate possono includere quanto segue:

- **Genera proprietà**

- **Genera campo**

- **Genera metodo**

- **Genera classe**

- **Genera nuovo tipo** (per una classe, struct, interfaccia o enumerazione)

## <a name="generate-event-handlers"></a>Genera gestori eventi

Nell'editor del codice IntelliSense consente di agganciare i metodi (gestori di eventi) a campi evento.

Quando si digita l'operatore `+=` dopo un campo evento in un file con estensione *cs*, IntelliSense chiede di premere **TAB**. Questa operazione consente di inserire una nuova istanza di un delegato che punta al metodo che gestisce l'evento.

![Associazione automatica dei pulsanti](../ide/media/vxautohookup.gif)

Se si preme **TAB**, IntelliSense termina automaticamente l'istruzione e visualizza il riferimento al gestore dell'evento come testo selezionato nell'editor del codice. Per completare l'associazione automatica dell'evento, IntelliSense chiede di premere di nuovo **TAB** per creare uno stub vuoto per il gestore dell'evento.

![Gestore eventi di generazione](../ide/media/vxgenerateeventhandler.gif)

> [!NOTE]
> Se un nuovo delegato creato da IntelliSense fa riferimento a un gestore eventi esistente, IntelliSense comunica queste informazioni nella descrizione comando. È quindi possibile modificare questo riferimento. Il testo è già selezionato nell'editor del codice. In caso contrario, l'associazione automatica dell'evento è a questo punto completata.

Se si preme **TAB**, IntelliSense associa automaticamente un metodo con la firma corretta e posiziona il cursore nel corpo del gestore dell'evento.

> [!NOTE]
> Usare il comando **Posizione precedente** nel menu **Visualizza** (**CTRL**+**-**) per tornare all'istruzione di associazione dell'evento.

## <a name="see-also"></a>Vedere anche

- [Usare IntelliSense](../ide/using-intellisense.md)
- [IDE di Visual Studio](../get-started/visual-studio-ide.md)