---
title: I gestori eventi propagano le modifiche al di fuori del modello
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 76234eea6c689459728e0da876b6a9cce7c290a5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "76114597"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>I gestori eventi propagano le modifiche al di fuori del modello

Nell'SDK di visualizzazione e modellazione è possibile definire i gestori eventi di archiviazione per propagare le modifiche alle risorse esterne all'archivio, ad esempio le variabili non di archivio, i file, i modelli in altri archivi o altre estensioni di Visual Studio. I gestori eventi dell'archivio vengono eseguiti dopo la fine della transazione in cui si è verificato l'evento di attivazione. Vengono inoltre eseguite in un'operazione di annullamento o ripetizione. Pertanto, a differenza delle regole di archiviazione, gli eventi di archiviazione sono particolarmente utili per aggiornare i valori che non rientrano nell'archivio. Diversamente dagli eventi .NET, i gestori eventi di archiviazione sono registrati per l'ascolto di una classe: non è necessario registrare un gestore separato per ogni istanza. Per ulteriori informazioni su come scegliere tra diversi modi per gestire le modifiche, vedere [risposta alle modifiche e propagazione delle](../modeling/responding-to-and-propagating-changes.md)modifiche.

La superficie grafica e altri controlli dell'interfaccia utente sono esempi di risorse esterne che possono essere gestite dagli eventi di archiviazione.

### <a name="to-define-a-store-event"></a>Per definire un evento di archivio

1. Scegliere il tipo di evento che si desidera monitorare. Per un elenco completo, esaminare le proprietà di <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> . Ogni proprietà corrisponde a un tipo di evento. I tipi di evento usati più di frequente sono:

    - `ElementAdded` -attivato quando viene creato un elemento del modello, un collegamento alla relazione, una forma o un connettore.

    - ElementPropertyChanged: attivato quando viene modificato il valore di una `Normal` proprietà di dominio. L'evento viene attivato solo se i valori nuovi e precedenti non sono uguali. Non è possibile applicare l'evento alle proprietà di archiviazione calcolate e personalizzate.

         Non può essere applicato alle proprietà del ruolo che corrispondono ai collegamenti delle relazioni. Usare invece `ElementAdded` per monitorare la relazione di dominio.

    - `ElementDeleted` -attivato dopo l'eliminazione di un elemento del modello, una relazione, una forma o un connettore. È comunque possibile accedere ai valori delle proprietà dell'elemento, ma non avrà alcuna relazione con altri elementi.

2. Aggiungere una definizione di classe parziale per _dslutente_**DocData** in un file di codice separato nel progetto **DslPackage** .

3. Scrivere il codice dell'evento come metodo, come nell'esempio seguente. Può essere `static` , a meno che non si desideri accedere a `DocData` .

4. Eseguire l'override `OnDocumentLoaded()` di per registrare il gestore. Se è presente più di un gestore, è possibile registrarli tutti nella stessa posizione.

Il percorso del codice di registrazione non è critico. `DocView.LoadView()` è un percorso alternativo.

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

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Usare gli eventi per apportare modifiche annullabili nell'archivio

Gli eventi di archiviazione non vengono in genere usati per la propagazione delle modifiche all'interno dell'archivio, perché il gestore eventi viene eseguito dopo il commit della transazione. Usare invece una regola di archiviazione. Per ulteriori informazioni, vedere la pagina relativa alla [propagazione delle modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

Tuttavia, è possibile usare un gestore eventi per eseguire ulteriori aggiornamenti all'archivio se si vuole che l'utente sia in grado di annullare gli aggiornamenti aggiuntivi separatamente dall'evento originale. Si supponga, ad esempio, che i caratteri minuscoli siano la convenzione usuale per i titoli degli album. È possibile scrivere un gestore eventi di archiviazione che corregge il titolo in lettere minuscole dopo che l'utente lo ha digitato in lettere maiuscole. Tuttavia, l'utente può usare il comando Annulla per annullare la correzione, ripristinando i caratteri maiuscoli. Una seconda operazione di annullamento comporta la rimozione della modifica dell'utente.

Al contrario, se è stata scritta una regola di archiviazione per eseguire la stessa operazione, la modifica dell'utente e la correzione si verificheranno nella stessa transazione, in modo che l'utente non possa annullare la regolazione senza perdere la modifica originale.

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

- Utilizzare `store.InUndoRedoOrRollback` per evitare di apportare modifiche agli elementi del modello in Undo. Il gestore delle transazioni imposterà tutti gli elementi dell'archivio sullo stato originale.

- Utilizzare `store.InSerializationTransaction` per evitare di apportare modifiche durante il caricamento del modello da un file.

- Le modifiche provocheranno l'attivazione di altri eventi. Assicurarsi di evitare un ciclo infinito.

## <a name="store-event-types"></a>Tipi di eventi di archiviazione

Ogni tipo di evento corrisponde a una raccolta in Store. EventManagerDirectory. È possibile aggiungere o rimuovere i gestori eventi in qualsiasi momento, ma è normale aggiungerli quando il documento viene caricato.

|`EventManagerDirectory` Nome proprietà|Eseguito quando|
|-|-|
|ElementAdded|Viene creata un'istanza di una classe di dominio, una relazione di dominio, una forma, un connettore o un diagramma.|
|ElementDeleted|Un elemento del modello è stato rimosso dalla directory degli elementi dell'archivio e non è più l'origine o la destinazione di una relazione. L'elemento non viene effettivamente eliminato dalla memoria, ma viene mantenuto in caso di un'operazione di annullamento futura.|
|ElementEventsBegun|Richiamato alla fine di una transazione esterna.|
|ElementEventsEnded|Richiamato quando tutti gli altri eventi sono stati elaborati.|
|ElementMoved|Un elemento del modello è stato spostato da una partizione di archivio a un'altra.<br /><br /> Non è correlato alla posizione di una forma nel diagramma.|
|ElementPropertyChanged|Il valore di una proprietà di dominio è stato modificato. Questa operazione viene eseguita solo se i valori vecchi e nuovi sono diversi.|
|RolePlayerChanged|Uno dei due ruoli (termina) di una relazione fa riferimento a un nuovo elemento.|
|RolePlayerOrderChanged|In un ruolo con molteplicità maggiore di 1, la sequenza dei collegamenti è cambiata.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Vedere anche

- [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)
- [Codice di esempio: diagrammi di circuito](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
