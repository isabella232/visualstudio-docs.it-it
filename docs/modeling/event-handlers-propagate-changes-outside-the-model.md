---
title: I gestori eventi propagano le modifiche al di fuori del modello
description: In Visualization and Modeling SDK è possibile definire i gestori eventi dell'archivio per propagare le modifiche alle risorse esterne all'archivio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, programming domain models
- Domain-Specific Language, events
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 0e2cd3ac4771da6d5cc5beb925e717a49b25912d22cc72e66210e34f13f46512
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386095"
---
# <a name="event-handlers-propagate-changes-outside-the-model"></a>I gestori eventi propagano le modifiche al di fuori del modello

In Visualization and Modeling SDK è possibile definire i gestori eventi dell'archivio per propagare le modifiche alle risorse esterne all'archivio, ad esempio variabili, file, modelli in altri archivi o altre estensioni Visual Studio archiviazione. I gestori eventi dell'archivio vengono eseguiti dopo la fine della transazione in cui si è verificato l'evento di attivazione. Vengono anche eseguite in un'operazione di annullamento o ripristino. Pertanto, a differenza delle regole dell'archivio, gli eventi dell'archivio sono particolarmente utili per l'aggiornamento di valori esterni all'archivio. A differenza degli eventi .NET, i gestori eventi dell'archivio vengono registrati per restare in ascolto di una classe: non è necessario registrare un gestore separato per ogni istanza. Per altre informazioni su come scegliere tra diversi modi per gestire le modifiche, vedere [Risposta e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md).

La superficie grafica e altri controlli dell'interfaccia utente sono esempi di risorse esterne che possono essere gestite dagli eventi dell'archivio.

### <a name="to-define-a-store-event"></a>Per definire un evento di archivio

1. Scegliere il tipo di evento da monitorare. Per un elenco completo, esaminare le proprietà di <xref:Microsoft.VisualStudio.Modeling.EventManagerDirectory> . Ogni proprietà corrisponde a un tipo di evento. I tipi di evento usati più di frequente sono:

    - `ElementAdded` : attivato quando viene creato un elemento del modello, un collegamento di relazione, una forma o un connettore.

    - ElementPropertyChanged: attivato quando viene modificato il valore di una `Normal` proprietà di dominio. L'evento viene attivato solo se i valori nuovi e vecchi non sono uguali. L'evento non può essere applicato alle proprietà di archiviazione calcolate e personalizzate.

         Non può essere applicato alle proprietà del ruolo che corrispondono ai collegamenti di relazione. Usare invece per `ElementAdded` monitorare la relazione di dominio.

    - `ElementDeleted` : attivato dopo l'eliminazione di un elemento del modello, una relazione, una forma o un connettore. È comunque possibile accedere ai valori delle proprietà dell'elemento, ma non avrà relazioni con altri elementi.

2. Aggiungere una definizione di classe parziale _per YourDsl_**DocData** in un file di codice separato nel **progetto DslPackage.**

3. Scrivere il codice dell'evento come metodo, come nell'esempio seguente. Può essere `static` , a meno che non si voglia accedere a `DocData` .

4. Eseguire `OnDocumentLoaded()` l'override di per registrare il gestore. Se sono presenti più gestori, è possibile registrarli tutti nella stessa posizione.

La posizione del codice di registrazione non è critica. `DocView.LoadView()` è una posizione alternativa.

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

## <a name="use-events-to-make-undoable-adjustments-in-the-store"></a>Usare gli eventi per apportare modifiche annullabili nello Store

Gli eventi di archiviazione non vengono in genere usati per la propagazione delle modifiche all'interno dell'archivio, perché il gestore eventi viene eseguito dopo il commit della transazione. Si userebbe invece una regola dell'archivio. Per altre informazioni, vedere [Regole propagare le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

Tuttavia, è possibile usare un gestore eventi per apportare altri aggiornamenti all'archivio, se si vuole che l'utente sia in grado di annullare gli aggiornamenti aggiuntivi separatamente dall'evento originale. Si supponga, ad esempio, che i caratteri minuscoli siano la convenzione consueta per i titoli degli album. È possibile scrivere un gestore dell'evento store che corregge il titolo in lettere minuscole dopo che l'utente lo ha digitato in maiuscolo. L'utente potrebbe tuttavia usare il comando Annulla per annullare la correzione, ripristinando i caratteri maiuscoli. Un secondo annullamento rimuove la modifica dell'utente.

Al contrario, se è stata scritta una regola dell'archivio per eseguire la stessa operazione, la modifica dell'utente e la correzione si presenterebbero nella stessa transazione, in modo che l'utente non possa annullare la rettifica senza perdere la modifica originale.

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

- Usare `store.InUndoRedoOrRollback` per evitare di apportare modifiche agli elementi del modello in Annulla. Il gestore delle transazioni imposta di nuovo lo stato originale di tutti gli elementi nell'archivio.

- Usare `store.InSerializationTransaction` per evitare di apportare modifiche durante il caricamento del modello dal file.

- Le modifiche causeranno l'attivazione di altri eventi. Assicurarsi di evitare un ciclo infinito.

## <a name="store-event-types"></a>Archiviare i tipi di evento

Ogni tipo di evento corrisponde a una raccolta in Store.EventManagerDirectory. È possibile aggiungere o rimuovere gestori eventi in qualsiasi momento, ma è consueto aggiungerli quando il documento viene caricato.

|`EventManagerDirectory` Nome della proprietà|Eseguito quando|
|-|-|
|ElementAdded|Viene creata un'istanza di una classe di dominio, una relazione di dominio, una forma, un connettore o un diagramma.|
|ElementoDeleted|Un elemento del modello è stato rimosso dalla directory degli elementi dell'archivio e non è più l'origine o la destinazione di alcuna relazione. L'elemento non viene effettivamente eliminato dalla memoria, ma viene mantenuto in caso di annullamento futuro.|
|ElementEventsBegun|Richiamato alla fine di una transazione esterna.|
|ElementEventsEnded|Richiamato quando tutti gli altri eventi sono stati elaborati.|
|ElementoMoved|Un elemento del modello è stato spostato da una partizione dell'archivio a un'altra.<br /><br /> Questa operazione non è correlata alla posizione di una forma nel diagramma.|
|ElementPropertyChanged|Il valore di una proprietà di dominio è stato modificato. Questa operazione viene eseguita solo se i valori vecchi e nuovi non sono uguali.|
|RolePlayerChanged|Uno dei due ruoli (termina) di una relazione fa riferimento a un nuovo elemento.|
|RolePlayerOrderChanged|In un ruolo con molteplicità maggiore di 1, la sequenza di collegamenti è stata modificata.|
|TransactionBeginning||
|TransactionCommitted||
|TransactionRolledBack||

## <a name="see-also"></a>Vedi anche

- [Risposta alle modifiche e propagazione delle modifiche](../modeling/responding-to-and-propagating-changes.md)
- [Codice di esempio: Diagrammi di circuito](https://code.msdn.microsoft.com/Visualization-Modeling-SDK-763778e8)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
