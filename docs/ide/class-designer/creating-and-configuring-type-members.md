---
title: Creazione e configurazione di membri di tipi (Progettazione classi)
description: Informazioni su come aggiungere membri ai tipi in un diagramma classi e configurare tali membri nella finestra Dettagli classe.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdetails.method
- vs.classdetails.property
- vs.classdetails.parameter
- vs.classdetails.event
- vs.classdetails.field
helpviewer_keywords:
- Class Designer [Visual Studio], member creation
- type members, modifying in Class Designer
- parameters [ASP.NET Web Services], adding to methods
- type members, configuring
- type members
- members
- type members, creating
- members, creating
- Class Designer [Visual Studio], type members
- read-only information, displaying
- members, configuring
- methods [Visual Studio], adding parameters
- Class Details window
- Class Details window, member creation
ms.assetid: 42af8738-3738-4ca7-82ff-edf573a68f96
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 793b4262e457301f79f625156194573d63664e9a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122056485"
---
# <a name="create-and-configure-type-members-in-class-designer"></a>Creare e configurare membri di tipi in Progettazione classi

È possibile aggiungere questi membri ai tipi in un diagramma classi e configurarli nella finestra **Dettagli classe**:

|**Tipo**|**Membri che può contenere**|
|--------------| - |
|Classe|metodo, proprietà (per C# e Visual Basic), campo, evento (per C# e Visual Basic), costruttore (metodo), distruttore (metodo), costante|
|Enumerazione|member|
|Interfaccia|metodo, proprietà, evento (per C# e Visual Basic)|
|Classe astratta|metodo, proprietà (per C# e Visual Basic), campo, evento (per C# e Visual Basic), costruttore (metodo), distruttore (metodo), costante|
|Struttura (struct in C#)|metodo, proprietà (per C# e Visual Basic), campo, evento (per C# e Visual Basic), costruttore (metodo), costante|
|Delegato|parameter|
|Modulo (solo VB)|metodo, proprietà, campo, evento, costruttore, costante|

> [!NOTE]
> Rendere più concisa la dichiarazione di proprietà se le funzioni di accesso get e set della proprietà non necessitano di logica aggiuntiva mediante proprietà implementate automaticamente (solo C#). Per visualizzare la firma completa, scegliere **Modifica il formato membri**, **Visualizza firma completa** dal menu  > **Diagramma classi**. Per altre informazioni sulle proprietà implementate automaticamente, vedere [Proprietà implementate automaticamente](/dotnet/csharp/programming-guide/classes-and-structs/auto-implemented-properties).

## <a name="common-tasks"></a>Attività comuni

|Attività|Contenuto di supporto|
|----------| - |
|**Introduzione:** prima di creare e configurare membri di tipo, è necessario aprire la finestra **Dettagli classe**.|- [Aprire la finestra Dettagli classe](creating-and-configuring-type-members.md#open-the-class-details-window)<br />- [Note sull'utilizzo di Dettagli classe](creating-and-configuring-type-members.md#class-details-usage-notes)<br />- [Visualizzazione di informazioni di sola lettura](creating-and-configuring-type-members.md#display-of-read-only-information)<br />- [Scelte rapide da tastiera e mouse nel diagramma classi e nella finestra Dettagli classe](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md)|
|**Creare e modificare membri di tipi:** è possibile creare nuovi membri, modificare i membri e aggiungere parametri a un metodo tramite la finestra **Dettagli classe**.|- [Creare membri](creating-and-configuring-type-members.md#create-members)<br />- [Modificare i membri dei tipi](creating-and-configuring-type-members.md#modify-type-members)<br />- [Aggiungere parametri ai metodi](creating-and-configuring-type-members.md#add-parameters-to-methods)|

## <a name="open-the-class-details-window"></a>Aprire la finestra Dettagli classe

Per impostazione predefinita, la finestra **Dettagli classe** viene visualizzata automaticamente quando si apre un nuovo diagramma classi. Vedere [Procedura: Aggiungere diagrammi classi ai progetti](how-to-add-class-diagrams-to-projects.md). È anche possibile aprire la finestra **Dettagli classe** nei modi seguenti:

- Fare clic con il pulsante destro del mouse su qualsiasi classe nel diagramma per visualizzare un menu di scelta rapida e quindi scegliere **Dettagli classe**.

- Selezionare **Visualizza**  >  **altri Windows** dettagli  >  **classe** dalla barra dei menu.

## <a name="create-members"></a>Creare membri

Per creare un membro, è possibile utilizzare uno dei seguenti strumenti:

- **Progettazione classi**

- Barra degli strumenti della finestra **Dettagli classe**

- Finestra **Dettagli classe**

> [!NOTE]
> È inoltre possibile creare costruttori e distruttori attenendosi alle procedure descritte in questa sezione. Tenere presente che costruttori e distruttori sono tipi speciali di metodi e, in quanto tali, vengono visualizzatili nel raggruppamento **Metodi** nelle forme del diagramma classi e nella sezione **Metodi** della griglia della finestra **Dettagli classe**.

> [!NOTE]
> L'unica entità che è possibile aggiungere a un delegato è il parametro. Si noti che la procedura "Per creare un membro usando la barra degli strumenti della finestra **Dettagli classe**" non è valida per questa operazione.

### <a name="create-a-member-using-class-designer"></a>Creare un membro usando Progettazione classi

1. Fare clic con il pulsante destro del mouse sul tipo a cui si vuole aggiungere un membro, scegliere **Aggiungi** e scegliere il tipo di membro da aggiungere.

     Verrà creata una nuova firma del membro, che verrà aggiunta al tipo. Il nome predefinito assegnato può essere modificato in **Progettazione classi**, nella finestra **Dettagli classe** oppure nella finestra **Proprietà**.

2. Se lo si desidera, specificare altri dettagli sul membro, ad esempio il tipo.

### <a name="create-a-member-using-the-class-details-window-toolbar"></a>Creare un membro usando la barra degli strumenti della finestra Dettagli classe

1. Sulla superficie del diagramma selezionare il tipo a cui aggiungere un membro.

     Il tipo otterrà lo stato attivo e i relativi contenuti verranno visualizzati nella finestra **Dettagli classe**.

2. Nella barra **degli strumenti della finestra** Dettagli classe fare clic sull'icona in alto e selezionare **Nuovo \<member>** nell'elenco a discesa.

     Il cursore si sposta nel campo **Nome** in una riga per il tipo di membro che si vuole aggiungere. Se, ad esempio, è stata selezionata l'opzione **Nuova proprietà**, il cursore si sposta in una nuova riga nella sezione **Proprietà** della finestra **Dettagli classe**.

3. Digitare il nome del membro da creare e premere Invio oppure spostare lo stato attivo in altro modo, ad esempio premendo Tab.

     Verrà creata una nuova firma del membro, che verrà aggiunta al tipo. A questo punto il membro esiste nel codice e viene visualizzato in **Progettazione classi**, nella finestra **Dettagli classe** e nella finestra Proprietà.

4. Se lo si desidera, specificare altri dettagli sul membro, ad esempio il tipo.

### <a name="create-a-member-using-the-class-details-window"></a>Creare un membro usando la finestra Dettagli classe

1. Sulla superficie del diagramma selezionare il tipo a cui aggiungere un membro.

     Il tipo otterrà lo stato attivo e i relativi contenuti verranno visualizzati nella finestra **Dettagli classe**.

2. Nella sezione **contenente il** tipo di membro da aggiungere della finestra Dettagli classe fare clic su **\<add member>** . Ad esempio, se si vuole aggiungere un campo, fare clic su **\<add field>** .

3. Digitare il nome del membro da creare e premere Invio.

     Verrà creata una nuova firma del membro, che verrà aggiunta al tipo. A questo punto il membro esiste nel codice e viene visualizzato in **Progettazione classi**, nella finestra **Dettagli classe** e nella finestra Proprietà.

4. Se lo si desidera, specificare altri dettagli sul membro, ad esempio il tipo.

    > [!NOTE]
    > per creare i membri è anche possibile usare i tasti di scelta rapida. Per altre informazioni, vedere [Scelte rapide da tastiera e con il mouse nel diagramma classi e nella finestra Dettagli classe](keyboard-and-mouse-shortcuts-in-the-class-diagram-and-class-details-window.md).

## <a name="modify-type-members"></a>Modificare i membri dei tipi

Utilizzando Progettazione classi è possibile modificare i membri dei tipi visualizzati nel diagramma. È possibile modificare i membri di qualsiasi tipo visualizzato in un diagramma classi che non sia di sola lettura. È possibile modificare i membri dei tipi usando la modifica sul posto nell'area di progettazione, la finestra Proprietà e la finestra **Dettagli classe**.

Tutti i membri visualizzati nella finestra **Dettagli classe** rappresentano i membri dei tipi presenti nel diagramma classi. Sono disponibili quattro tipi di membri: metodi, proprietà, campi ed eventi.

Tutte le righe dei membri sono contraddistinte da intestazioni che raggruppano i membri in base al tipo. Tutte le proprietà vengono ad esempio visualizzate sotto l'intestazione **Proprietà**, che possono essere compresse o espanse come un nodo nella griglia.

Ciascuna riga di membri visualizza i seguenti elementi:

- **Icona del membro**

     Ciascun tipo di membro è rappresentato dalla rispettiva icona. Posizionare il cursore del mouse sull'icona del membro per visualizzarne la firma. Fare clic sull'icona del membro o sullo spazio vuoto a sinistra per selezionare la riga.

- **Nome membro**

     Nella colonna **Nome** della riga di un membro è visualizzato il nome del membro. Questo nome viene visualizzato anche nella proprietà **Nome** nella finestra Proprietà. È possibile utilizzare questa cella per modificare il nome di qualsiasi membro con autorizzazioni di lettura-scrittura.

     Se la colonna **Nome** è troppo stretta per visualizzare l'intero nome, è possibile posizionare il cursore del mouse sul nome del membro per visualizzarlo.

- **Tipo di membro**

     Nella cella **Tipo di membro** viene usata la tecnologia Intellisense, che consente di scegliere da un elenco di tutti i tipi disponibili nel progetto corrente o nei progetti a cui viene fatto riferimento.

- **Modificatore del membro**

     È possibile modificare il modificatore di visibilità di un membro in `Public` (`public`), `Private` (`private`), `Friend` (`internal`) `Protected` (`protected`), `Protected Friend` (`protected internal`) o `Default`.

- **\<add member>**

     L'ultima riga nella **finestra Dettagli** classe contiene il testo **\<add member>** nella **cella** Nome. Facendo clic su questa cella, è possibile creare un nuovo membro. Per altre informazioni, vedere [Creare membri](creating-and-configuring-type-members.md#create-members).

- **Proprietà dei membri nella finestra Proprietà**

     Nella finestra **Dettagli classe** viene visualizzato un sottoinsieme delle proprietà dei membri riportate nella finestra Proprietà. La modifica di una proprietà in un percorso aggiorna il valore della proprietà a livello globale. Ciò include la visualizzazione del valore nell'altro percorso.

- **Summary**

     Nella cella **Riepilogo** è contenuto un riepilogo delle informazioni relative al membro. Fare clic sui puntini di sospensione nella cella **Riepilogo** per visualizzare o modificare le informazioni relative a **Riepilogo**, **Tipo restituito** e **Note** per il membro.

- **Nascondi**

     Se la casella di controllo **Nascondi** è selezionata, il membro non verrà visualizzato nel tipo.

### <a name="to-modify-a-type-member"></a>Per modificare un membro di un tipo

1. Selezionare un tipo utilizzando Progettazione classi.

2. Se la finestra **Dettagli classe** non è visualizzata, fare clic sul pulsante della finestra **Dettagli classe** nella barra degli strumenti di Progettazione classi.

3. Modificare i valori nei campi della griglia della finestra **Dettagli classe**. Dopo ogni modifica premere INVIO oppure spostare lo stato attivo dal campo modificato, ad esempio premendo TAB. Il codice verrà immediatamente aggiornato in base alle modifiche apportate.

    > [!NOTE]
    > Se si desidera modificare solo il nome di un membro, è possibile farlo mediante la modifica sul posto.

## <a name="add-parameters-to-methods"></a>Aggiungere parametri a metodi

Usare la finestra **Dettagli classe** per aggiungere parametri ai metodi. I parametri possono essere configurati per essere obbligatori o facoltativi. Se si specifica un valore per la proprietà **Valore predefinito facoltativo** di un parametro, la finestra di progettazione genererà il codice come parametro facoltativo.

Le righe dei parametri contengono i seguenti elementi:

- **Nome**

     La colonna **Nome** di una riga di parametri visualizza il nome del parametro. Questo nome viene visualizzato anche nella proprietà **Nome** nella finestra Proprietà. È possibile utilizzare questa cella per cambiare il nome di qualsiasi parametro con autorizzazioni di lettura-scrittura.

     Se la colonna **Nome** è troppo stretta per visualizzare l'intero nome, è possibile posizionare il cursore del mouse sul nome del parametro per visualizzarlo.

- **Tipo**

     Nella cella **Tipo parametro** viene usata la tecnologia IntelliSense, che consente di scegliere da un elenco di tutti i tipi disponibili nel progetto corrente o nei progetti a cui viene fatto riferimento.

- **Modificatore**

     La cella **Modificatore** di una riga di parametro accetta e visualizza il nuovo modificatore del parametro. Per immettere un nuovo modificatore di parametro, nell'elenco a discesa selezionare **Nessuno**, **ref**, **out** o **params** in C# e **ByVal**, **ByRef** o **ParamArray** in VB.

- **Summary**

     La cella **Riepilogo** di una riga di parametro consente di immettere i commenti di codice visualizzati in IntelliSense quando si immette il parametro nell'editor di codice.

- **\<add parameter>**

     Nell'ultima riga di parametri di un membro la cella **Nome** contiene la stringa **<aggiungi parametro\>**. Fare clic in questa cella per creare un nuovo parametro. Per altre informazioni, vedere [Per aggiungere un parametro a un metodo](creating-and-configuring-type-members.md#add-parameters-to-methods).

Nella **finestra Proprietà** vengono visualizzate le  stesse proprietà dei parametri visualizzate nella finestra Dettagli classe: **Nome** **,** Tipo , **Modificatore**, **Riepilogo**, nonché la proprietà **Valore predefinito** facoltativo. Se una proprietà viene cambiata in una posizione, il relativo valore verrà aggiornato a livello globale, anche nell'altra posizione.

> [!NOTE]
> Per aggiungere un parametro a un delegato, vedere [Creare membri](creating-and-configuring-type-members.md#create-members).

> [!NOTE]
> Anche se è un metodo, un distruttore non può avere parametri.

### <a name="to-add-a-parameter-to-a-method"></a>Per aggiungere un parametro a un metodo

1. Sulla superficie del diagramma fare clic sul tipo contenente il metodo a cui si desidera aggiungere un parametro.

     Il tipo otterrà lo stato attivo e il relativo contenuto verrà visualizzato nella finestra **Dettagli classe**.

2. Nella finestra **Dettagli classe** espandere la riga del metodo a cui si vuole aggiungere un parametro.

     Viene visualizzata una riga di parametro rientrata contenente solo una coppia di parentesi e le parole **\<add parameter> .**

3. Fare **\<add parameter>** clic su , digitare il nome del nuovo parametro e premere **INVIO.**

     Il nuovo parametro verrà aggiunto al metodo e al codice del metodo. Verrà visualizzato nelle finestre **Dettagli classe** e Proprietà.

4. Se lo si desidera, specificare altri dettagli relativi al parametro, ad esempio il tipo.

### <a name="to-add-an-optional-parameter-to-a-method"></a>Per aggiungere un parametro facoltativo a un metodo

1. Sulla superficie del diagramma fare clic sul tipo contenente il metodo a cui si desidera aggiungere un parametro facoltativo.

     Il tipo otterrà lo stato attivo e il relativo contenuto verrà visualizzato nella finestra **Dettagli classe**.

2. Nella finestra **Dettagli classe** espandere la riga del metodo a cui si vuole aggiungere un parametro facoltativo.

     Viene visualizzata una riga di parametro rientrata contenente solo una coppia di parentesi e le parole **\<add parameter> .**

3. Fare **\<add parameter>** clic su , digitare il nome del nuovo parametro e premere **INVIO.**

     Il nuovo parametro verrà aggiunto al metodo e al codice del metodo. Verrà visualizzato nelle finestre **Dettagli classe** e Proprietà.

4. Nella finestra Proprietà digitare un valore per la proprietà **Valore predefinito facoltativo**. L'impostazione della proprietà Valore predefinito facoltativo di un parametro lo rende facoltativo.

    > [!NOTE]
    > I parametri facoltativi devono essere gli ultimi parametri presenti nell'elenco di parametri.

## <a name="class-details-usage-notes"></a>Note sull'uso di Dettagli classe

Leggere i suggerimenti riportati di seguito relativi all'uso della finestra **Dettagli classe**.

### <a name="editable-and-non-editable-cells"></a>Celle modificabili e non modificabili

Tutte le celle della finestra **Dettagli classe** sono modificabili, con alcune eccezioni:

- L'intero tipo è di sola lettura se, ad esempio, si trova in un assembly a cui viene fatto riferimento. Se si seleziona la forma in Progettazione classi, i relativi dettagli vengono visualizzati in sola lettura nella finestra **Dettagli classe**.

- Per gli indicizzatori, il nome è di sola lettura mentre gli altri elementi (tipo, modificatore, riepilogo) sono modificabili.

- Per tutti i generics sono presenti parametri di sola lettura nella finestra **Dettagli classe**. Per cambiare tali parametri, è necessario modificare il relativo codice sorgente.

- Il nome del parametro di tipo definito su un tipo generico è di sola lettura.

- Se il codice di un tipo è interrotto (non analizzabile), il contenuto del tipo viene visualizzato in sola lettura nella finestra **Dettagli classe**.

### <a name="the-class-details-window-and-source-code"></a>Finestra Dettagli classe e codice sorgente

- Per visualizzare il codice sorgente, fare clic con il pulsante destro del mouse su una forma nella finestra **Dettagli classe** (o in Progettazione classi) e scegliere Visualizza codice. Il file del codice sorgente verrà aperto e il cursore verrà posizionato sull'elemento selezionato.

- La visualizzazione di informazioni sulla firma in Progettazione classi e nella finestra **Dettagli classe** verrà immediatamente aggiornata in base alla modifica del codice sorgente. Se la finestra **Dettagli classe** è chiusa, le nuove informazioni saranno visibili alla successiva apertura.

- Se il codice di un tipo è interrotto (non analizzabile), il contenuto del tipo viene visualizzato in sola lettura nella finestra **Dettagli classe**.

### <a name="clipboard-functionality-in-the-class-details-window"></a>Funzionalità Appunti nella finestra Dettagli classe

È possibile copiare o tagliare campi o righe dalla finestra **Dettagli classe** e incollarli in un altro tipo. Le righe possono essere tagliate solo se non sono di sola lettura. Quando una riga viene incollata, la finestra **Dettagli classe** assegna un nuovo nome (derivato dal nome della riga copiata) per evitare conflitti.

## <a name="display-of-read-only-information"></a>Visualizzare le informazioni di sola lettura

In Progettazione classi e nella finestra **Dettagli classe** è possibile visualizzare i tipi (e i membri dei tipi) per i seguenti elementi:

- un progetto contenente un diagramma classi;

- un progetto a cui viene fatto riferimento da un progetto contenente un diagramma classi;

- un assembly a cui viene fatto riferimento da un progetto contenente un diagramma classi.

Negli ultimi due casi, l'entità a cui viene fatto riferimento (un tipo o un membro) è in sola lettura nel diagramma classi che la rappresenta.

Un intero progetto o parti di esso, ad esempio singoli file, possono essere in sola lettura. Nella maggior parte dei casi un progetto o uno dei relativi file è in sola lettura quando è incluso nel controllo del codice sorgente (e non estratto), esiste in un assembly esterno oppure il sistema operativo considera i file in sola lettura.

**Controllo del codice sorgente**

Poiché un diagramma classi viene salvato come file in un progetto, è necessario estrarre il progetto per salvare tutte le modifiche apportate in Progettazione classi o nella finestra **Dettagli classe**.

**Progetti di sola lettura**

Il progetto può essere in sola lettura per un motivo diverso dal controllo del codice sorgente. Se si chiude il progetto verrà visualizzata una finestra di dialogo in cui viene chiesto se si vuole sovrascrivere il file del progetto, ignorare le modifiche (non salvarle) o annullare l'operazione di chiusura. Se si sceglie di sovrascrivere, i file del progetto verranno sovrascritti e diventeranno di lettura-scrittura. Verrà inoltre aggiunto il nuovo file del diagramma classi.

**Tipi di sola lettura**

Se si prova a salvare un progetto contenente un tipo il cui file del codice sorgente è di sola lettura, verrà visualizzata la finestra di dialogo **Salvataggio file in sola lettura**, in cui sono disponibili le opzioni per salvare il file con un nuovo nome o in un nuovo percorso oppure per sovrascrivere il file di sola lettura. Se si sceglie di sovrascrivere il file, la nuova copia non sarà più in sola lettura.

Se un file di codice contiene un errore di sintassi, le forme che visualizzano il codice in quel file saranno temporaneamente in sola lettura finché l'errore di sintassi non viene corretto. Le forme in questo stato sono caratterizzate da testo di colore rosso e da un'icona rossa con una descrizione che indica un errore di analisi nel file del codice sorgente.

Un tipo a cui viene fatto riferimento (ad esempio un tipo .NET), che esiste all'interno di un altro nodo di progetto o di un nodo di assembly a cui viene fatto riferimento, viene indicato nell'area Progettazione classi come in sola lettura. Un tipo locale, che esiste nel progetto aperto, è in lettura-scrittura e la relativa forma viene indicata come tale nell'area di progettazione di Progettazione classi.

Gli indicizzatori sono in lettura/scrittura nel codice e nella finestra **Dettagli classe**, ma il nome dell'indicizzatore è in sola lettura.

I metodi parziali non possono essere modificati tramite Progettazione classi o la finestra **Dettagli classe**, ma devono essere modificati con l'editor del codice.

Il codice C++ nativo non può essere modificato tramite Progettazione classi o la finestra **Dettagli classe**, ma deve essere modificato con l'editor del codice.

## <a name="see-also"></a>Vedi anche

- [Visualizzazione dei tipi e delle relazioni](designing-and-viewing-classes-and-types.md)
- [Refactoring di classi e tipi](refactoring-classes-and-types.md)
