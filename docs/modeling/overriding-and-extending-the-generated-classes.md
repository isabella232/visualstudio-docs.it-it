---
title: Override ed estensione delle classi generate
description: Informazioni su come la definizione DSL è una piattaforma in cui è possibile creare un potente set di strumenti basati su un linguaggio specifico di dominio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 4217f4f5ebc15ce32e138419f10cc412a40692e7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034266"
---
# <a name="override-and-extend-the-generated-classes"></a>Eseguire l'override ed estendere le classi generate

La definizione DSL è una piattaforma in cui è possibile creare un potente set di strumenti basati su un linguaggio specifico di dominio. È possibile eseguire molte estensioni e adattamenti eseguendo l'override ed estendendo le classi generate dalla definizione DSL. Queste classi includono non solo le classi di dominio definite in modo esplicito nel diagramma di definizione DSL, ma anche altre classi che definiscono la casella degli strumenti, lo strumento di esplorazione, la serializzazione e così via.

## <a name="extensibility-mechanisms"></a>Meccanismi di estendibilità

Sono disponibili diversi meccanismi che consentono di estendere il codice generato.

### <a name="override-methods-in-a-partial-class"></a>Eseguire l'override dei metodi in una classe parziale

Le definizioni di classe parziali consentono di definire una classe in più di una posizione. In questo modo è possibile separare il codice generato dal codice scritto manualmente. Nel codice scritto manualmente è possibile eseguire l'override delle classi ereditate dal codice generato.

Ad esempio, se nella definizione DSL si definisce una classe di dominio denominata , è possibile scrivere codice personalizzato che aggiunge `Book` metodi di override:

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
> Per eseguire l'override dei metodi in una classe generata, scrivere sempre il codice in un file separato dai file generati. In genere, il file è contenuto in una cartella denominata CustomCode. Se si apportano modifiche al codice generato, queste andranno perse quando si rigenera il codice dalla definizione DSL.

Per individuare i metodi di cui è possibile eseguire **l'override,** digitare override nella classe , seguito da uno spazio. La descrizione comando di IntelliSense indica quali metodi possono essere sottoposti a override.

### <a name="double-derived-classes"></a>Double-Derived classi

La maggior parte dei metodi nelle classi generate viene ereditata da un set fisso di classi negli spazi dei nomi Modeling. Tuttavia, alcuni metodi sono definiti nel codice generato. In genere, ciò significa che non è possibile eseguirne l'override. Non è possibile eseguire l'override in una classe parziale dei metodi definiti in un'altra definizione parziale della stessa classe.

Tuttavia, è possibile eseguire l'override di questi metodi impostando il flag **Generates Double Derived** per la classe di dominio. In questo modo vengono generate due classi, una è una classe di base astratta dell'altra. Tutte le definizioni di metodo e proprietà si trova nella classe di base e solo il costruttore si trova nella classe derivata.

Ad esempio, nell'esempio Library.dsl la proprietà della classe di dominio è `CirculationBook` `Generates``Double Derived` impostata su `true` . Il codice generato per tale classe di dominio contiene due classi:

- `CirculationBookBase`, che è un oggetto astratto e che contiene tutti i metodi e le proprietà.

- `CirculationBook`, derivato da `CirculationBookBase` . È vuoto, ad eccezione dei relativi costruttori.

Per eseguire l'override di qualsiasi metodo, creare una definizione parziale della classe derivata, ad esempio `CirculationBook` . È possibile eseguire l'override sia dei metodi generati che dei metodi ereditati dal framework di modellazione.

È possibile usare questo metodo con tutti i tipi di elemento, inclusi elementi del modello, relazioni, forme, diagrammi e connettori. È anche possibile eseguire l'override dei metodi di altre classi generate. Alcune classi generate, ad esempio ToolboxHelper, sono sempre derivate da due classi.

### <a name="custom-constructors"></a>Costruttori personalizzati

Non è possibile eseguire l'override di un costruttore. Anche nelle classi derivate doppie, il costruttore deve essere nella classe derivata.

Se si vuole fornire un costruttore personalizzato, è possibile eseguire questa operazione impostando per la classe `Has Custom Constructor` di dominio nella definizione DSL. Quando si fa **clic su Trasforma tutti i** modelli , il codice generato non includerà un costruttore per tale classe. Includerà una chiamata al costruttore mancante. In questo modo viene generato un report degli errori quando si compila la soluzione. Fare doppio clic sulla segnalazione errori per visualizzare un commento nel codice generato che spiega cosa fornire.

Scrivere una definizione di classe parziale in un file separato dai file generati e fornire il costruttore .

### <a name="flagged-extension-points"></a>Punti di estensione contrassegnati

Un punto di estensione contrassegnato è una posizione nella definizione DSL in cui è possibile impostare una proprietà o una casella di controllo per indicare che si fornirà un metodo personalizzato. I costruttori personalizzati sono un esempio. Altri esempi includono l'impostazione della proprietà di un dominio su Calculated o Custom Archiviazione l'impostazione del `Kind` flag **Is Custom** in un generatore di connessioni.

In ogni caso, quando si imposta il flag e si rigenera il codice, si verifica un errore di compilazione. Fare doppio clic sull'errore per visualizzare un commento che spiega cosa è necessario fornire.

### <a name="rules"></a>Regole

Il gestore delle transazioni consente di definire regole che vengono eseguite prima della fine di una transazione in cui si è verificato un evento designato, ad esempio una modifica in una proprietà. Le regole vengono in genere usate per mantenere il sincronismo tra elementi diversi nell'archivio. Ad esempio, le regole vengono usate per assicurarsi che nel diagramma sia visualizzato lo stato corrente del modello.

Le regole vengono definite per ogni classe, in modo che non sia necessario avere codice che registra la regola per ogni oggetto. Per altre informazioni, vedere [Regole propagare le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Archiviare eventi

L'archivio di modellazione fornisce un meccanismo di eventi che è possibile usare per restare in ascolto di tipi specifici di modifiche nell'archivio, tra cui aggiunta ed eliminazione di elementi, modifiche ai valori delle proprietà e così via. I gestori eventi vengono chiamati dopo la chiusura della transazione in cui sono state apportate le modifiche. In genere, questi eventi vengono usati per aggiornare le risorse all'esterno dell'archivio.

### <a name="net-events"></a>Eventi .NET

È possibile sottoscrivere alcuni eventi nelle forme. Ad esempio, è possibile restare in ascolto dei clic del mouse su una forma. È necessario scrivere codice che sottoscrive l'evento per ogni oggetto. Questo codice può essere scritto in un override di InitializeInstanceResources().

Alcuni eventi vengono generati in ShapeField, che vengono usati per disegnare elementi Decorator in una forma. Per un esempio, vedere [Procedura: Intercettare un clic su una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

Questi eventi in genere non si verificano all'interno di una transazione. È consigliabile creare una transazione se si desidera apportare modifiche nell'archivio.
