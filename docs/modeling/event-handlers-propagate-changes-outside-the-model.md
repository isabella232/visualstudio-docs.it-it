---
title: I gestori eventi propagano le modifiche al di fuori del modello
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cd02491b42e9e6a5d677eca35ccde2aa559352c4
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096881"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>I gestori eventi propagano le modifiche al di fuori del modello

In Visualization and Modeling SDK, è possibile definire gestori eventi dell'archivio per propagare le modifiche alle risorse all'esterno dell'archivio, ad esempio di variabile non di archivio, file, i modelli in altri archivi o altre estensioni di Visual Studio. I gestori eventi Store vengono eseguiti dopo la fine della transazione in cui si è verificato un evento di attivazione. Vengono anche eseguite in un'operazione di annullamento o ripristino. Pertanto, a differenza di archivio regole, gli eventi di archiviazione sono particolarmente utili per l'aggiornamento dei valori che non rientrano nell'archivio. A differenza degli eventi di .NET, archivio i gestori eventi registrati per l'ascolto di una classe: non è necessario registrare un gestore separato per ogni istanza. Per altre informazioni su come scegliere tra diversi modi per gestire le modifiche, vedere [procedura: rispondere a e la propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).

L'area grafica e altri controlli dell'interfaccia utente sono esempi di risorse esterne che possono essere gestiti dagli eventi dell'archivio.

### <a name="to-define-a-store-event"></a>Per definire un evento di archiviazione

1. Scegliere il tipo di evento che si vuole monitorare. Per un elenco completo, esaminare le proprietà di <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory>. Ogni proprietà corrisponde a un tipo di evento. I più usati sono tipi di evento:

    - `ElementAdded` -attivato quando un elemento del modello, viene creato il collegamento di relazione, forma o connettore.

    - ElementPropertyChanged - attivato quando il valore di un `Normal` della proprietà di dominio viene modificata. L'evento viene generato solo se i valori nuovi e precedenti non sono uguali. L'evento non può essere applicato alle proprietà di archiviazione calcolate e personalizzate.

         Non può essere applicato alle proprietà del ruolo che corrispondono ai collegamenti di relazione. Usare invece `ElementAdded` per monitorare la relazione di dominio.

    - `ElementDeleted` -attivato dopo un elemento del modello, relazione, forma o connettore è stato eliminato. È comunque possibile accedere i valori delle proprietà dell'elemento, ma lo sarà non presentano relazioni tra gli altri elementi.

2. Aggiungere una definizione di classe parziale per _Dslutente_**DocData** in un file di codice separato nella **DslPackage** progetto.

3. Scrivere il codice dell'evento come un metodo, come nell'esempio seguente. Può essere `static`, a meno che non si desidera accedere `DocData`.

4. Eseguire l'override `OnDocumentLoaded()` per registrare il gestore. Se si dispone di più di un gestore, è possibile registrarli tutti nella stessa posizione.

Il percorso del codice di registrazione non critico. `DocView.LoadView()` è un percorso alternativo.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using Microsoft.VisualStudio.Modeling;

namespace Company.MusicLib
{
  partial class MusicLibDocData
  {
    // Register store events here or in DocView.LoadView().
    protected override void OnDocumentLoaded()
    {
      base.OnDocumentLoaded(); // Don't forget this.

      #region Store event handler registration.
      Store store = this.Store;
      EventManagerDirectory emd = store.EventManagerDirectory;
      DomainRelationshipInfo linkInfo = store.DomainDataDirectory
          .FindDomainRelationship(typeof(ArtistAppearsInAlbum));
      emd.ElementAdded.Add(linkInfo,
          new EventHandler<ElementAddedEventArgs>(AddLink));
      emd.ElementDeleted.Add(linkInfo,
          new EventHandler<ElementDeletedEventArgs>(RemoveLink));

      #endregion Store event handlers.
    }

    private void AddLink(object sender, ElementAddedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Add(link.Artist.Name, link.Album.Title);
    }
    private void RemoveLink(object sender, ElementDeletedEventArgs e)
    {
      ArtistAppearsInAlbum link = e.ModelElement as ArtistAppearsInAlbum;
      if (link != null)
            ExternalDatabase.Delete(link.Artist.Name, link.Album.Title);
    }
  }
}
```

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Usare gli eventi per apportare modifiche annullabili di Store

Eventi Store non vengono usati in genere per la propagazione delle modifiche all'interno dell'archivio, in quanto il gestore eventi viene eseguito dopo che viene eseguito il commit della transazione. Utilizzare invece una regola di archivio. Per altre informazioni, vedere [le regole propagano le modifiche all'interno di the Model](../modeling/rules-propagate-changes-within-the-model.md).

Tuttavia, è possibile utilizzare un gestore eventi per eseguire gli aggiornamenti aggiuntivi nello store, se si desidera che l'utente sia in grado di annullare gli aggiornamenti aggiuntivi separatamente dall'evento originale. Si supponga, ad esempio, di caratteri minuscoli convenzione abituale per i titoli di album. È possibile scrivere un gestore eventi dell'archivio che corregge il titolo in lettere minuscole dopo che l'utente ha digitato in lettere maiuscole. Ma l'utente potrebbe usare il comando di annullamento per annullare la correzione, ripristino i caratteri maiuscoli. Una seconda operazione di annullamento annullerebbe la modifica dell'utente.

Al contrario, se si scrivesse una regola di archivio per eseguire la stessa operazione, la modifica dell'utente e la correzione, sarebbe nella stessa transazione, in modo che l'utente non è riuscito ad annullare la regolazione senza perdere le modifiche originali.

```csharp
partial class MusicLibDocView
{
    // Register store events here or in DocData.OnDocumentLoaded().
    protected override void LoadView()
    {
      /* Register store event handler for Album Title property. */
      // Get reflection data for property:
      DomainPropertyInfo propertyInfo =
        this.DocData.Store.DomainDataDirectory
        .FindDomainProperty(Album.TitleDomainPropertyId);
      // Add to property handler list:
      this.DocData.Store.EventManagerDirectory
        .ElementPropertyChanged.Add(propertyInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));

      /*
      // Alternatively, you can set one handler for
      // all properties of a class.
      // Your handler has to determine which property changed.
      DomainClassInfo classInfo = this.Store.DomainDataDirectory
           .FindDomainClass(typeof(Album));
      this.Store.EventManagerDirectory
          .ElementPropertyChanged.Add(classInfo,
        new EventHandler<ElementPropertyChangedEventArgs>
             (AlbumTitleAdjuster));
       */
      return base.LoadView();
    }

// Undoable adjustment after a property is changed.
// Method can be static since no local access.
private static void AlbumTitleAdjuster(object sender,
         ElementPropertyChangedEventArgs e)
{
  Album album = e.ModelElement as Album;
  Store store = album.Store;

  // We mustn't update the store in an Undo:
  if (store.InUndoRedoOrRollback
      || store.InSerializationTransaction)
      return;

  if (e.DomainProperty.Id == Album.TitleDomainPropertyId)
  {
    string newValue = (string)e.NewValue;
    string lowerCase = newValue.ToLowerInvariant();
    if (!newValue.Equals(lowerCase))
    {
      using (Transaction t = store.TransactionManager
            .BeginTransaction("adjust album title"))
      {
        album.Title = lowerCase;
        t.Commit();
      } // Beware! This could trigger the event again.
    }
  }
  // else other properties of this class.
}
```

Se si scrive un evento che aggiorna l'archivio:

- Usare `store.InUndoRedoOrRollback` per evitare di apportare modifiche agli elementi del modello di annullamento. Il gestore delle transazioni imposterà tutti gli elementi nell'archivio di tornare allo stato originale.

- Usare `store.InSerializationTransaction` per evitare di apportare modifiche mentre il modello viene caricato dal file.

- Le modifiche causerà un'ulteriore eventi venga attivato. Assicurarsi di evitare un ciclo infinito.

## <a name="store-event-types"></a>Store i tipi di evento

Ogni tipo di evento corrisponde a una raccolta in Store.EventManagerDirectory. È possibile aggiungere o rimuovere i gestori eventi in qualsiasi momento, ma è normale per aggiungerle quando il documento viene caricato.

|`EventManagerDirectory` Nome della proprietà|Eseguito quando|
|-|-|
|ElementAdded|Viene creata un'istanza di una classe di dominio, relazione di dominio, forma, connettore o diagramma.|
|ElementDeleted|Un elemento del modello è stato rimosso dalla directory dell'elemento dell'archivio e non è più l'origine o la destinazione di una relazione. L'elemento non viene effettivamente eliminato dalla memoria, ma verrà mantenuto in caso di una futura operazione di annullamento.|
|ElementEventsBegun|Richiamato al termine di una transazione esterna.|
|ElementEventsEnded|Richiamato quando sono stati elaborati tutti gli altri eventi.|
|ElementMoved|Un elemento del modello è stato spostato da un archivio di partizione a altra.<br /><br /> Ciò non è correlata alla posizione di una forma nel diagramma.|
|ElementPropertyChanged|Il valore della proprietà del dominio è stato modificato. Questa operazione viene eseguita solo se i valori vecchi e nuovi sono diversi.|
|RolePlayerChanged|Uno dei due ruoli (estremità) di una relazione fa riferimento a un nuovo elemento.|
|RolePlayerOrderChanged|In un ruolo con molteplicità maggiore di 1, la sequenza di collegamenti è stata modificata.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Vedere anche

- [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)
- [Codice di esempio: Elettrici](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]