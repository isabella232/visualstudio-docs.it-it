---
title: Override ed estensione delle classi generate | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language, providing overridable classes
ms.assetid: 30baa60d-a8ea-4611-96c1-8fcc3317cf21
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 16a09a5b0f5e534d310092036b8e7eb1d4c344d9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668481"
---
# <a name="overriding-and-extending-the-generated-classes"></a>Override ed estensione delle classi generate
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La definizione DSL è una piattaforma in cui è possibile creare un potente set di strumenti basati su un linguaggio specifico di dominio. Molte estensioni e adattamenti possono essere apportate eseguendo l'override e l'estensione delle classi generate dalla definizione DSL. Queste classi includono non solo le classi di dominio definite in modo esplicito nel diagramma di definizione DSL, ma anche altre classi che definiscono la casella degli strumenti, la finestra di esplorazione, la serializzazione e così via.

## <a name="extensibility-mechanisms"></a>Meccanismi di estendibilità
 Sono disponibili diversi meccanismi che consentono di estendere il codice generato.

### <a name="overriding-methods-in-a-partial-class"></a>Override di metodi in una classe parziale
 Le definizioni di classe parziali consentono di definire una classe in più di una posizione. In questo modo è possibile separare il codice generato dal codice scritto personalmente. Nel codice scritto manualmente è possibile eseguire l'override delle classi ereditate dal codice generato.

 Se, ad esempio, nella definizione DSL si definisce una classe di dominio denominata `Book`, è possibile scrivere codice personalizzato per aggiungere metodi di override:

 `public partial class Book`

 `{`

 `protected override void OnDeleting()`

 `{`

 `MessageBox.Show("Deleting book " + this.Title);`

 `base.OnDeleting();`

 `} }`

> [!NOTE]
> Per eseguire l'override dei metodi in una classe generata, scrivere sempre il codice in un file separato dai file generati. In genere, il file è contenuto in una cartella denominata CustomCoded. Se si apportano modifiche al codice generato, andranno perse quando si rigenera il codice dalla definizione DSL.

 Per individuare i metodi di cui è possibile eseguire l'override, digitare **override** nella classe, seguito da uno spazio. La descrizione comando IntelliSense indica i metodi di cui è possibile eseguire l'override.

### <a name="double-derived-classes"></a>Classi derivate doppie
 La maggior parte dei metodi nelle classi generate viene ereditata da un set fisso di classi negli spazi dei nomi di modellazione. Tuttavia, alcuni metodi sono definiti nel codice generato. In genere, ciò significa che non è possibile eseguirne l'override; non è possibile eseguire l'override di in una classe parziale i metodi definiti in un'altra definizione parziale della stessa classe.

 Tuttavia, è possibile eseguire l'override di questi metodi impostando il flag **generato doppio derivato** per la classe di dominio. In questo modo vengono generate due classi, una che è una classe di base astratta dell'altra. Tutte le definizioni di metodo e proprietà si trovano nella classe di base e solo il costruttore si trova nella classe derivata.

 Ad esempio, nella libreria di esempio. DSL, per la classe di dominio `CirculationBook` la proprietà `Generates``Double Derived` è impostata su `true`. Il codice generato per la classe di dominio contiene due classi:

- `CirculationBookBase`, che è un oggetto astratto e che contiene tutti i metodi e le proprietà.

- `CirculationBook`, derivato da `CirculationBookBase`. È vuota, tranne che per i relativi costruttori.

  Per eseguire l'override di qualsiasi metodo, si crea una definizione parziale della classe derivata, ad esempio `CirculationBook`. È possibile eseguire l'override sia dei metodi generati che dei metodi ereditati dal framework di modellazione.

  È possibile utilizzare questo metodo con tutti i tipi di elemento, tra cui elementi del modello, relazioni, forme, diagrammi e connettori. È anche possibile eseguire l'override dei metodi di altre classi generate. Alcune classi generate, ad esempio ToolboxHelper, sono sempre derivate da Double.

### <a name="custom-constructors"></a>Costruttori personalizzati
 Non è possibile eseguire l'override di un costruttore. Anche nelle classi derivate da doppio, il costruttore deve trovarsi nella classe derivata.

 Se si desidera fornire un costruttore personalizzato, è possibile eseguire questa operazione impostando `Has Custom Constructor` per la classe di dominio nella definizione DSL. Quando si fa clic su **trasforma tutti i modelli**, il codice generato non includerà un costruttore per tale classe. Verrà inclusa una chiamata al costruttore mancante. Questo genera una segnalazione di errore quando si compila la soluzione. Fare doppio clic sulla segnalazione errori per visualizzare un commento nel codice generato che spiega cosa è necessario fornire.

 Scrivere una definizione di classe parziale in un file separato dai file generati e fornire il costruttore.

### <a name="flagged-extension-points"></a>Punti di estensione contrassegnati
 Un punto di estensione contrassegnato è una posizione nella definizione DSL in cui è possibile impostare una proprietà o una casella di controllo per indicare che si fornirà un metodo personalizzato. I costruttori personalizzati sono un esempio. Altri esempi includono l'impostazione del `Kind` di una proprietà di dominio su un archivio calcolato o personalizzato oppure l'impostazione del flag **is Custom** in un generatore di connessioni.

 In ogni caso, quando si imposta il flag e si rigenera il codice, viene generato un errore di compilazione. Fare doppio clic sull'errore per visualizzare un commento che spiega cosa è necessario fornire.

### <a name="rules"></a>Regole
 Il gestore delle transazioni consente di definire regole che vengono eseguite prima della fine di una transazione in cui si è verificato un evento designato, ad esempio una modifica in una proprietà. Le regole vengono in genere usate per gestire la sincronizzazione tra elementi diversi nell'archivio. Ad esempio, le regole vengono utilizzate per assicurarsi che nel diagramma venga visualizzato lo stato corrente del modello.

 Le regole vengono definite in base alle singole classi, quindi non è necessario disporre di codice che registri la regola per ogni oggetto. Per ulteriori informazioni, vedere la pagina relativa alla [propagazione delle modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).

### <a name="store-events"></a>Archivia eventi
 L'archivio di modellazione fornisce un meccanismo per gli eventi che è possibile usare per restare in attesa di tipi specifici di modifiche nell'archivio, tra cui l'aggiunta e l'eliminazione di elementi, modifiche ai valori delle proprietà e così via. I gestori eventi vengono chiamati dopo la chiusura della transazione in cui sono state apportate le modifiche. In genere, questi eventi vengono usati per aggiornare le risorse all'esterno dell'archivio.

### <a name="net-events"></a>Eventi .NET
 È possibile sottoscrivere alcuni eventi in forme. Ad esempio, è possibile attendere i clic del mouse su una forma. È necessario scrivere codice che sottoscrive l'evento per ogni oggetto. Questo codice può essere scritto in un override di InitializeInstanceResources ().

 Alcuni eventi vengono generati in ShapeFields, che vengono utilizzati per disegnare elementi Decorator in una forma. Per un esempio, vedere [procedura: intercettare un clic su una forma o un elemento Decorator](../modeling/how-to-intercept-a-click-on-a-shape-or-decorator.md).

 Questi eventi in genere non si verificano all'interno di una transazione. Se si desidera apportare modifiche nell'archivio, è necessario creare una transazione.
