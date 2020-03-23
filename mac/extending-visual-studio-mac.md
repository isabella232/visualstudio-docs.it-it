---
title: Estensione di Visual Studio per Mac
description: Le funzioni e funzionalità di Visual Studio per Mac possono essere estese con moduli chiamati pacchetti di estensione. La prima parte di questa guida permette di creare un semplice pacchetto di estensione per Visual Studio per Mac per inserire la data e l'ora in un documento. La seconda parte della guida presenta le nozioni di base relative al sistema dei pacchetti di estensione e alcune delle principali API che costituiscono la base di Visual Studio per Mac.
author: heiligerdankgesang
ms.author: dominicn
ms.date: 12/20/2019
ms.technology: vs-ide-sdk
ms.assetid: D5245AB0-8404-426B-B538-F49125E672B2
ms.openlocfilehash: 30826f68be1ef2f29940c8f9c95b2b79435e0a2a
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "75852042"
---
# <a name="extending-visual-studio-for-mac"></a>Estensione di Visual Studio per Mac

Visual Studio per Mac è costituito da un set di moduli chiamati *pacchetti di estensione*. È possibile usare i pacchetti di estensione per introdurre nuove funzionalità in Visual Studio per Mac, come il supporto per un linguaggio aggiuntivo o un nuovo modello di progetto.

I pacchetti di estensione vengono compilati dai punti di *estensione* di altri pacchetti di estensione. I punti di estensione sono segnaposto per aree che possono essere espanse, ad esempio un menu o l'elenco dei comandi dell'IDE. Un pacchetto di estensione può essere compilato da un punto di estensione registrando un nodo di dati strutturati chiamato estensione, ad esempio una nuova voce di menu o un nuovo comando. Ogni punto di estensione accetta tipi specifici di estensioni, come *Command*, *Pad* o *FileTemplate*. Un modulo che contiene punti di estensione viene definito un *host di componenti aggiuntivi*, in quanto può essere esteso da altri pacchetti di estensione.

Per personalizzare Visual Studio per Mac, è possibile creare un pacchetto di estensione compilato da punti di estensione contenuti in host di componenti aggiuntivi all'interno di librerie preesistenti in Visual Studio per Mac, come mostrato nel diagramma seguente:

![Architettura dei componenti aggiuntivi](media/extending-visual-studio-mac-addin1.png)

Perché un pacchetto di estensione possa essere compilato da Visual Studio per Mac, deve includere estensioni compilate da punti di estensione preesistenti all'interno dell'IDE di Visual Studio per Mac. Quando un pacchetto di estensione si basa su un punto di estensione definito in un host del componente aggiuntivo, si dice che abbia una _dipendenza_ da tale pacchetto di estensione.

Il vantaggio di questa progettazione modulare è il fatto che Visual Studio per Mac è estendibile, ovvero sono disponibili molti punti di estensione su cui è possibile basare i pacchetti di estensione personalizzati. Alcuni esempi degli attuali pacchetti di estensione includono il supporto per C# ed F#, strumenti debugger e modelli di progetto.

> [!NOTE]
> in presenza di un progetto Addin Maker creato prima di Addin Maker 1.2, è necessario eseguire la migrazione del progetto come descritto nei passaggi [qui](https://mhut.ch/addinmaker/1.2).

<!---The [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) topic explains how to build an extension package that uses a *Command* to insert the date and time into an open text document.--->

Questa sezione esamina i diversi file generati da Addin Maker e i dati richiesti da un'estensione di comando.

## <a name="attribute-files"></a>File di attributo

I pacchetti di estensione archiviano i metadati su nome, versione, dipendenze e altre informazioni in attributi C#. Addin Maker crea due file, `AddinInfo.cs` e `AssemblyInfo.cs`, per archiviare e organizzare queste informazioni. I pacchetti di estensione devono avere un ID univoco e uno spazio dei nomi specificati nel * `Addin` relativo attributo:*

```csharp
[assembly:Addin (
   "DateInserter",
   Namespace = "DateInserter",
   Version = "1.0"
)]
```

I pacchetti di estensione devono anche dichiarare dipendenze dai pacchetti di estensione proprietari dei punti di estensione a cui sono collegati, ai quali viene automaticamente fatto riferimento in fase di compilazione.

È inoltre possibile aggiungere altri riferimenti tramite il nodo dei riferimenti del componente aggiuntivo nel riquadro della soluzione per il progetto, come mostrato nell'immagine seguente:

![Screenshot dell'inserimento della data](media/extending-visual-studio-mac-addin13.png)

Vengono anche aggiunti gli attributi `assembly:AddinDependency` corrispondenti in fase di compilazione. Una volta aggiunti i metadati e le dichiarazioni di dipendenza, è possibile concentrarsi sui blocchi predefiniti essenziali del pacchetto di estensione.

## <a name="extensions-and-extension-points"></a>Estensioni e punti di estensione

Un punto di estensione è un segnaposto che definisce una struttura dei dati (tipo), mentre un'estensione definisce i dati conformi a una struttura specificata da un determinato punto di estensione. I punti di estensione specificano il tipo di estensione che accettano nella rispettiva dichiarazione. Le estensioni vengono dichiarate tramite nomi di tipo o percorsi di estensione. Per una spiegazione più approfondita di come creare il punto di estensione necessario, vedere le [informazioni di riferimento sui punti di estensione](https://github.com/mono/mono-addins/wiki/Extension-Points).

L'architettura delle estensioni e dei punti di estensione mantiene rapido e modulare lo sviluppo di Visual Studio per Mac.

<!--Since there are a large number of extension types, this article focuses on the ones used in the extension package that was built in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md).-->

### <a name="command-extensions"></a>Estensioni comando

<!--[Walkthrough](~/extending-visual-studio-mac-walkthrough.md) uses a Command Extension - an extension that points to methods that are called every time it is executed. -->

Le estensioni comando sono estensioni che puntano a metodi chiamati ogni volta che vengono eseguiti.

Le estensioni comando vengono definite aggiungendo voci al punto di estensione `/MonoDevelop/Ide/Commands`. L'estensione è stata definita in `Manifest.addin.xml` con il codice seguente:

 ```xml
<Extension path="/MonoDevelop/Ide/Commands/Edit">
  <Command id="DateInserter.DateInserterCommands.InsertDate"
            _label="Insert Date"
            _description="Insert the current date"
            defaultHandler="DateInserter.InsertDateHandler" />
</Extension>
```

Il nodo di estensione contiene un attributo path che specifica il punto di estensione a cui si collega, in questo caso `/MonoDevelop/Ide/Commands/Edit`. Inoltre, funge da nodo padre per il comando. Il nodo del comando include gli attributi seguenti:

* `id` - Specifica l'identificatore per questo comando. Gli identificatori dei comandi devono essere dichiarati come membri di enumerazione e vengono usati per connettere Commands a CommandItems.
* `_label` - Il testo da visualizzare nei menu.
* `_description` - Il testo da visualizzare come descrizione comando per i pulsanti della barra degli strumenti.
* `defaultHandler` - Specifica la classe `CommandHandler` che attiva il comando.

<!--To invoke the command from the Edit Menu, the walkthrough creates a CommandItem extension that plugs into the `/MonoDevelop/Ide/MainMenu/Edit` extension point:-->

Nel frammento di codice seguente è illustrata un'estensione CommandItem che si collega al punto di estensione `/MonoDevelop/Ide/MainMenu/Edit`:

```xml
<Extension path="/MonoDevelop/Ide/MainMenu/Edit">
  <CommandItem id="DateInserter.DateInserterCommands.InsertDate" />
</Extension>
```

Un'estensione CommandItem inserisce un comando specificato nel relativo attributo `id` in un menu. CommandItem estende il punto di estensione `/MonoDevelop/Ide/MainMenu/Edit`, che fa apparire l'etichetta del comando nel **menu Modifica**. Osservare come l'ID in CommandItem corrisponda all'ID del nodo del comando, `InsertDate`. Se si rimuove CommandItem, l'opzione **Inserisci data** non sarà più disponibile nel menu Modifica.

### <a name="command-handlers"></a>Gestori di comandi

`InsertDateHandler` è un'estensione della classe `CommandHandler`. Questo oggetto esegue l'override di due metodi, `Update` e `Run`. Sul metodo `Update` viene eseguita una query ogni volta che un comando viene visualizzato in un menu o eseguito tramite tasti di scelta rapida. Modificando l'oggetto info, è possibile disabilitare il comando o renderlo invisibile, immettere comandi di matrice e altro ancora. Questo metodo `Update` disabilita il comando se non può trovare un oggetto *Document* attivo con un oggetto *TextEditor* per inserire informazioni di testo:

```csharp
protected override void Update (CommandInfo info)
{
    info.Enabled = IdeApp.Workbench.ActiveDocument?.Editor != null;
}
```

Quando è presente logica speciale per abilitare o nascondere il comando, è sufficiente eseguire l'override del metodo `Update`. Il metodo `Run` viene eseguito ogni volta che un utente esegue un comando, in questo caso quando un utente sceglie il comando dal menu Modifica. Questo metodo inserisce la data e l'ora nel punto di inserimento all'interno dell'editor di testo:

```csharp
protected override void Run ()
{
  var editor = IdeApp.Workbench.ActiveDocument.Editor;
  var date = DateTime.Now.ToString ();
  editor.InsertAtCaret (date);
}
```

Dichiarare il tipo di comando come membro di enumerazione in `DateInserterCommands`:

```csharp
public enum DateInserterCommands
{
  InsertDate,
}
```

Il comando e CommandItem sono ora collegati: CommandItem chiama il comando quando CommandItem viene selezionato nel **menu Modifica**.

## <a name="ide-apis"></a>API dell'IDE

<!--The extension package detailed in the [Walkthrough](~/extending-visual-studio-mac-walkthrough.md) deals with the Text Editor in Visual Studio for Mac, but this is only one of many possible areas for customization. -->

Per informazioni sull'ambito delle aree disponibili per lo sviluppo, vedere le [informazioni di riferimento sull'albero delle estensioni](https://www.monodevelop.com/developers/articles/extension-tree-reference/) e la [panoramica delle API](https://www.monodevelop.com/developers/articles/api-overview/). Quando si compilano pacchetti di estensione avanzati, fare riferimento agli [articoli per sviluppatori](https://www.monodevelop.com/developers/articles/). Ecco un elenco parziale delle aree per la personalizzazione:

* Riquadri
* Schemi di tasti di scelta rapida
* Criteri
* Formattatori di codice
* Formati di file di progetto
* Pannelli delle preferenze
* Pannelli delle opzioni
* Protocolli del debugger
* Visualizzatori del debugger
* Layout dell'area di lavoro
* Nodi dell'albero del riquadro della soluzione
* Margini dell'editor standard
* Motori di unit test
* Generatori di codice
* Frammenti di codice
* Framework di destinazione
* Runtime di destinazione
* Back-end VCS
* Refactoring
* Gestori di esecuzione
* Evidenziazione della sintassi

## <a name="extending-the-new-editor"></a>Estensione del nuovo editor

Visual Studio per Mac [introduce l'interfaccia utente del nuovo editor di testo Cocoa](https://docs.microsoft.com/visualstudio/releasenotes/vs2019-mac-relnotes#RTW) basato sugli stessi livelli di editor di Visual Studio in Windows.

La condivisione dell'editor di testo tra Visual Studio e Visual Studio per Mac offre numerosi vantaggi, tra cui la possibilità di adattare a Visual Studio per Mac codice destinato all'editor di Visual Studio.

> [!NOTE]
> Al momento, il nuovo editor supporta solo file C#. Verranno presi in considerazione altri linguaggi e formati di file nell'editor legacy, in cui sono tuttavia implementate alcune delle API dell'editor di Visual Studio descritte di seguito.

### <a name="visual-studio-editor-overview"></a>Panoramica dell'editor di Visual Studio

![Architettura dell'editor di Visual Studio](media/vs-editor-architecture.png)

Prima di affrontare i dettagli dell'estensione per Visual Studio per Mac, è utile fornire alcune informazioni sull'editor condiviso. Di seguito sono elencate alcune risorse che possono facilitare questo approfondimento:

* [Managed Extensibility Framework](/dotnet/framework/mef/index)
* [MEF nell'editor](/visualstudio/extensibility/managed-extensibility-framework-in-the-editor)
* [Componenti e funzionalità dell'editor](/visualstudio/extensibility/inside-the-editor)
* [Punti di estensione dei servizi di linguaggio e dell'editor](/visualstudio/extensibility/language-service-and-editor-extension-points)
* [Video introduttivo dell'architettura dell'editor](https://www.youtube.com/watch?v=PkYVztKjO9A)

Con queste risorse in mano, i concetti principali che [`ITextBuffer`](/dotnet/api/microsoft.visualstudio.text.itextbuffer) è [`ITextView`](/dotnet/api/microsoft.visualstudio.text.editor.itextview)necessario avere familiarità con sono un e un :

* Un `ITextBuffer` è una rappresentazione in memoria di testo che può essere modificato nel corso del tempo. La proprietà `CurrentSnapshot` di `ITextBuffer` restituisce una rappresentazione *immutabile* del contenuto corrente del buffer, un'istanza di `ITextSnapshot`. Quando viene apportata una modifica nel buffer, la proprietà CurrentSnapshot viene aggiornata alla versione più recente. Gli analizzatori potranno esaminare lo snapshot di testo in qualsiasi thread, ma il contenuto non potrà essere in alcun modo modificato.

* Un `ITextView` è la rappresentazione nell'interfaccia utente come viene eseguito il rendering di `ITextBuffer` sullo schermo del controllo editor. Contiene un riferimento al buffer di testo, nonché a `Caret`, `Selection` e ad altri concetti correlati all'interfaccia utente.

Per un [`MonoDevelop.Ide.Gui.Document`](http://source.monodevelop.com/#MonoDevelop.Ide/MonoDevelop.Ide.Gui/Document.cs,4e960d4735f089b5)determinato oggetto , `ITextBuffer` è `ITextView` `Document.GetContent<ITextBuffer>()` possibile `Document.GetContent<ITextView>()` recuperare rispettivamente l'oggetto sottostante associato e in via e.

## <a name="additional-information"></a>Informazioni aggiuntive

> [!NOTE]
> Microsoft sta attualmente lavorando al miglioramento degli scenari di estendibilità per Visual Studio per Mac. Se si stanno creando estensioni e sono necessarie altre informazioni o maggiore supporto oppure si vuole fornire commenti e suggerimenti, compilare il modulo [Visual Studio for Mac Extension Authoring](https://forms.office.com/Pages/ResponsePage.aspx?id=v4j5cvGGr0GRqy180BHbR3YufGX_azhFl7MkrQO9i9JUNVMyMklVVlAzQVdURDg2NjQxTFRBVTJURC4u) (Creazione di estensioni per Visual Studio per Mac).

## <a name="see-also"></a>Vedere anche

- [Sviluppare estensioni di Visual Studio (in Windows)](/visualstudio/extensibility/starting-to-develop-visual-studio-extensions)
