---
title: Override ed estensione delle classi generate
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8d3c90d955ba412a75005ab47627c1901df57891
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55936980"
---
# <a name="override-and-extend-the-generated-classes"></a>Override ed estensione delle classi generate

La definizione DSL è una piattaforma in cui è possibile compilare un set avanzato di strumenti basati su un linguaggio specifico di dominio. Possono accadere molte estensioni e gli adattamenti da override ed estensione delle classi generate dalla definizione DSL. Queste classi includono non solo le classi di dominio che sia stata definita in modo esplicito nel diagramma di definizione DSL, ma anche altre classi che definiscono la casella degli strumenti, Esplora, serializzazione e così via.

## <a name="extensibility-mechanisms"></a>Meccanismi di estendibilità

Vengono forniti diversi meccanismi che consentono di estendere il codice generato.

### <a name="override-methods-in-a-partial-class"></a>Eseguire l'override in una classe parziale

Definizioni di classe parziali consentono una classe di definire più di un'unica posizione. In questo modo è possibile separare il codice generato dal codice scritto dall'utente. Nel codice scritto manualmente, è possibile eseguire l'override di classi ereditate dal codice generato.

Ad esempio, se nella definizione DSL è definire una classe di dominio denominata `Book`, è possibile scrivere codice personalizzato che aggiunge i metodi di override:

```csharp
public partial class Book
{
   protected override void OnDeleting()
   {
      MessageBox.Show("Deleting book " + this.Title);
      base.OnDeleting();
   }
}
```

> [!NOTE]
> Per eseguire l'override di metodi in una classe generata, scrivono sempre il codice in un file separato dal file generati. In genere, il file è contenuto in una cartella denominata Customcoded. Se si apportano modifiche al codice generato, andranno persi quando si rigenera il codice dalla definizione DSL.

Per scoprire quali metodi è possibile eseguire l'override, digitare **eseguire l'override** nella classe, seguito da uno spazio. La descrizione comando IntelliSense indicherà quali metodi possono essere ignorati.

### <a name="double-derived-classes"></a>Classi di doppia derivazione

La maggior parte dei metodi nelle classi generate vengono ereditata da un set fisso delle classi negli spazi dei nomi di modellazione. Tuttavia, alcuni metodi sono definiti nel codice generato. In genere, ciò significa che è possibile eseguire l'override. è possibile eseguire l'override in una classe parziale i metodi definiti in un'altra definizione parziale della stessa classe.

Tuttavia, è possibile eseguire l'override di questi metodi impostando il **genera una derivata doppia** flag per la classe di dominio. Questo causa due classi da generare, uno da una classe base astratta di altro. Tutte le definizioni di metodo e proprietà sono nella classe di base e solo il costruttore è nella classe derivata.

Ad esempio, nell'esempio Library.dsl, il `CirculationBook` classe di dominio ha la `Generates``Double Derived` impostata su `true`. Il codice generato per tale classe di dominio contiene due classi:

-   `CirculationBookBase`, che è una classe astratta e che contiene tutte le proprietà e metodi.

-   `CirculationBook`, che deriva da `CirculationBookBase`. È vuoto, eccetto propri costruttori.

Per eseguire l'override di qualsiasi metodo, si crea una definizione parziale della classe derivata, ad esempio `CirculationBook`. È possibile eseguire l'override di entrambi i metodi generati e i metodi ereditati dal framework di modellazione.

È possibile utilizzare questo metodo con tutti i tipi di elemento, inclusi i connettori, relazioni, forme, diagrammi e gli elementi del modello. È anche possibile eseguire l'override di metodi di altre classi generate. Alcune classi generate, ad esempio il ToolboxHelper sono sempre doppia derivazione.

### <a name="custom-constructors"></a>Costruttori personalizzati

È possibile eseguire l'override di un costruttore. Anche in classi di doppia derivazione, deve essere il costruttore nella classe derivata.

Se si desidera fornire un costruttore personalizzato, è possibile farlo impostando `Has Custom Constructor` per la classe di dominio nella definizione DSL. Quando fa clic su **Trasforma tutti i modelli**, il codice generato non include un costruttore per la classe. Includerà una chiamata al costruttore manca. In questo modo un report degli errori quando si compila la soluzione. Fare doppio clic sul report degli errori per visualizzare un commento nel codice generato che spiega cosa è necessario fornire.

Scrivere una definizione di classe parziale in un file separato dal file generati e fornire il costruttore.

### <a name="flagged-extension-points"></a>Punti di estensione con flag

Un punto di estensione con flag è una posizione nella definizione DSL in cui è possibile impostare una proprietà o una casella di controllo per indicare che verrà fornito un metodo personalizzato. I costruttori personalizzati sono un esempio. Altri esempi includono l'impostazione di `Kind` della proprietà del dominio Calculated o archiviazione personalizzata o impostazione il **personalizzata è** flag in un generatore di connessioni.

In ogni caso, quando si imposta il flag e rigenerare il codice, verrà generato un errore di compilazione. Fare doppio clic per visualizzare un commento che spiega cosa è necessario specificare l'errore.

### <a name="rules"></a>Regole

Il gestore delle transazioni consente di definire regole che eseguono prima della fine di una transazione in cui designato verificato un evento, ad esempio una modifica in una proprietà. Le regole vengono in genere utilizzate per mantenere synchronism tra diversi elementi nell'archivio. Ad esempio, le regole consentono di assicurarsi che il diagramma viene visualizzato lo stato corrente del modello.

Le regole vengono definite per ogni classe, in modo che non è che il codice che registra la regola per ogni oggetto. Per altre informazioni, vedere [le regole propagano le modifiche all'interno di the Model](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Eventi di Store

L'archivio di modellazione fornisce un meccanismo di eventi che è possibile usare per l'ascolto per specifici tipi di modifiche nell'archivio, tra cui aggiunta ed eliminazione di elementi, le modifiche ai valori delle proprietà e così via. I gestori eventi vengono chiamati dopo la chiusura della transazione in cui sono state apportate le modifiche. In genere, questi eventi vengono usati per aggiornare le risorse all'esterno dell'archivio.

### <a name="net-events"></a>Eventi .NET

È possibile sottoscrivere alcuni eventi sulle forme. Ad esempio, è possibile restare in ascolto per clic del mouse su una forma. È necessario scrivere codice che sottoscrive l'evento per ogni oggetto. Questo codice può essere scritto in un override di InitializeInstanceResources().

Alcuni eventi vengono generati su ShapeFields, che consentono di disegnare gli elementi Decorator su una forma. Per un esempio, vedere [Procedura: Intercettare un clic su una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

In genere non si verificano tali eventi in una transazione. È necessario creare una transazione se si desidera apportare modifiche nell'archivio.