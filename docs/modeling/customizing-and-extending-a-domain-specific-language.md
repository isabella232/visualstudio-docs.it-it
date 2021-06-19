---
title: Personalizzazione ed estensione di un linguaggio specifico di dominio
description: Informazioni su come Visual Studio SDK di modellazione e visualizzazione (VMSDK) offre diversi livelli in cui è possibile definire gli strumenti di modellazione.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 04180b1fc8930b58c2d78635c794c8a614db5ed5
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112389384"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Personalizzare ed estendere un linguaggio specifico di dominio

Visual Studio SDK di modellazione e visualizzazione (VMSDK) offre diversi livelli in cui è possibile definire gli strumenti di modellazione:

1. Definire un linguaggio specifico di dominio (DSL) usando il diagramma di definizione DSL. È possibile creare rapidamente un linguaggio DSL con una notazione diagrammatica, un modulo XML leggibile e gli strumenti di base necessari per generare codice e altri artefatti. Per altre informazioni, vedere [How to Define a Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

2. Ottimizzare il DSL usando funzionalità più avanzate della definizione DSL. Ad esempio, è possibile fare in modo che vengano visualizzati collegamenti aggiuntivi quando l'utente crea un elemento. Queste tecniche vengono ottenute principalmente nella definizione DSL e alcune richiedono alcune righe di codice programma.

3. Estendere gli strumenti di modellazione usando il codice programma. VMSDK è progettato in modo specifico per facilitare l'integrazione delle estensioni con il codice generato dalla definizione DSL. Per altre informazioni, vedere [Writing Code to Customize a Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
> Dopo aver aggiornato il file delle definizioni DSL, non dimenticare  di fare clic su Trasforma tutti i modelli sulla barra degli strumenti Esplora soluzioni prima di ricompilare la soluzione. 

## <a name="article-reference"></a>Informazioni di riferimento sull'articolo

|Per ottenere questo effetto|Fare riferimento a questo argomento|
|-|-|
|Consente all'utente di impostare le proprietà di colore e stile di una forma.|Fare clic con il pulsante destro del mouse sulla forma o sulla classe connettore, scegliere **Aggiungi** esposto e fare clic su un elemento.|
|Classi diverse dell'elemento del modello hanno un aspetto simile nel diagramma, condividendo proprietà quali altezza e larghezza iniziali, colore e descrizioni comando.|Usare l'ereditarietà tra forme o classi connettore. I mapping tra forme derivate e classi di dominio derivate ereditano i dettagli di mapping degli elementi padre.<br /><br /> In caso contrario, eseguire il mapping di classi di dominio diverse alla stessa classe di forma.|
|Una classe di elementi del modello viene visualizzata da contesti di forme diversi.|Eseguire il mapping di più classi di forma alla stessa classe di dominio. Quando si compila la soluzione, seguire la segnalazione errori e fornire il codice richiesto per decidere quale forma usare.|
|Il colore della forma o altre caratteristiche, ad esempio il tipo di carattere, indicano lo stato corrente.|Vedere [Aggiornamento di forme e connettori per riflettere il modello.](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)<br /><br /> Creare una regola che aggiorna le proprietà esposte. Vedere [Le regole propagano le modifiche all'interno del modello.](../modeling/rules-propagate-changes-within-the-model.md)<br /><br /> In caso contrario, usare OnAssociatedPropertyChanged() per aggiornare le funzionalità non esposte, ad esempio le frecce di collegamento o il tipo di carattere.|
|L'icona sulla forma cambia per indicare lo stato.|Impostare la visibilità del mapping dell'elemento Decorator nella finestra Dettagli DSL. Individuare diversi elementi Decorator immagine nella stessa posizione. Vedere [Aggiornamento di forme e connettori per riflettere il modello.](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md)<br /><br /> In caso contrario, eseguire l'override `ImageField.GetDisplayImage()` di . Vedere l'esempio in <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> .|
|Impostare un'immagine di sfondo su qualsiasi forma|Eseguire l'override di InitializeInstanceResources() per aggiungere un imageField ancorato.|
|Annidare forme a qualsiasi profondità|Configurare un albero di incorporamento ricorsivo. Definire BoundsRules per contenere le forme.|
|Collegare i connettori in corrispondenza di punti fissi sul limite di un elemento.|Definire gli elementi del terminale incorporati, rappresentati da porte di piccole dimensioni nel diagramma. Usare BoundsRules per correggere le porte sul posto. Vedere l'esempio circuit diagram in [Visualization and Modeling SDK](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).|
|Campo di testo visualizza un valore derivato da altri valori.|Eseguire il mapping dell'elemento Decorator di testo a una proprietà di dominio Calculated o Custom Storage. Per altre informazioni, vedere [Proprietà di archiviazione calcolate e personalizzate.](../modeling/calculated-and-custom-storage-properties.md)|
|Propagare le modifiche tra gli elementi del modello o tra forme|Vedere [Convalida in un Domain-Specific linguaggio.](../modeling/validation-in-a-domain-specific-language.md)|
|Propagare le modifiche alle risorse, ad esempio altre estensioni Visual Studio all'esterno dell'archivio.|Vedere [I gestori eventi propagano le modifiche all'esterno del modello.](../modeling/event-handlers-propagate-changes-outside-the-model.md)|
|Nella finestra Proprietà vengono visualizzate le proprietà di un elemento correlato.|Configurare l'inoltro delle proprietà. Vedere [Personalizzazione della finestra Proprietà.](../modeling/customizing-the-properties-window.md)|
|Categorie di proprietà|La finestra delle proprietà è suddivisa in sezioni denominate categorie. Impostare la **categoria** delle proprietà del dominio. Le proprietà con lo stesso nome di categoria verranno visualizzate nella stessa sezione. È anche possibile impostare la **categoria di** un ruolo relazione.|
|Controllare l'accesso utente alle proprietà del dominio|Impostare **Is Browsable** false per impedire che una proprietà di dominio venga visualizzata nel Finestra Proprietà in fase di esecuzione. È comunque possibile mapparlo agli elementi Decorator di testo.<br /><br /> **È di sola lettura dell'interfaccia** utente impedisce agli utenti di modificare una proprietà di dominio.<br /><br /> L'accesso del programma alla proprietà di dominio non è interessato.|
|Modificare il nome, l'icona e la visibilità dei nodi in Esplora modelli del DSL.|Vedere [Personalizzazione di Esplora modelli.](../modeling/customizing-the-model-explorer.md)|
|Abilitare copia, taglia e incolla|Impostare la **proprietà Abilita Copia** incolla del nodo **Editor** in Esplora DSL.|
|Copiare i collegamenti di riferimento e le relative destinazioni ogni volta che viene copiato un elemento. Ad esempio, copiare i commenti allegati a un elemento.|Impostare la **proprietà Propagates Copy** del ruolo di origine (rappresentata dalla riga su un lato della relazione di dominio nel diagramma di definizione DSL).<br /><br /> Scrivere codice per eseguire l'override di ProcessOnCopy per ottenere effetti più complessi.<br /><br /> Vedere [Personalizzazione del comportamento di copia.](../modeling/customizing-copy-behavior.md)|
|Elimina, ricollega o ricollega elementi correlati quando viene eliminato un elemento.|Impostare il **valore Propagates Delete** di un ruolo relazione. Per gli effetti più complessi, `ShouldVisitRelationship` eseguire l'override dei metodi e nella classe , definiti in `ShouldVisitRolePlayer` `MyDslDeleteClosure` **DomainModel.cs.**|
|Mantenere il layout e l'aspetto delle forme durante la copia e il trascinamento della selezione.|Aggiungere le forme e i connettori all'oggetto `ElementGroupPrototype` copiato. Il metodo più pratico per eseguire l'override è `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Vedere [Personalizzazione del comportamento di copia.](../modeling/customizing-copy-behavior.md)|
|Incollare le forme in una posizione prescelta, ad esempio la posizione del cursore attuale.|Eseguire `ClipboardCommandSet.ProcessOnCopy()` l'override di per usare la versione specifica del percorso `ElementOperations.Merge().` di Vedere [Personalizzazione del comportamento di copia.](../modeling/customizing-copy-behavior.md)|
|Creare collegamenti aggiuntivi durante l'operazione Incolla|Eseguire l'override di ClipboardCommandSet.ProcessOnPasteCommand()|
|Abilitare il trascinamento della selezione da questo diagramma, da altri DSL e da altri elementi di Windows|Vedere [Procedura: Aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Consente di trascinare una forma o uno strumento su una forma figlio, ad esempio una porta, come se fosse trascinata sull'elemento padre.|Definire una direttiva di unione degli elementi nella classe dell'oggetto di destinazione per inoltrare l'oggetto eliminato all'elemento padre. Vedere [Personalizzazione della creazione e dello spostamento di elementi.](../modeling/customizing-element-creation-and-movement.md)|
|Consente di trascinare una forma o uno strumento in una forma e di creare altri collegamenti o oggetti. Ad esempio, per consentire l'applicazione di un commento a un elemento a cui deve essere collegato.|Definire una direttiva di unione degli elementi nella classe di dominio di destinazione e definire i collegamenti da generare. In casi complessi è possibile aggiungere codice personalizzato. Vedere [Personalizzazione della creazione e dello spostamento di elementi.](../modeling/customizing-element-creation-and-movement.md)|
|Creare un gruppo di elementi con un solo strumento. Ad esempio, un componente con un set fisso di porte.|Eseguire l'override del metodo di inizializzazione della casella degli strumenti in ToolboxHelper.cs. Creare un prototipo EGP (Element Group Prototype) contenente gli elementi e i relativi collegamenti di relazione. Vedere [Personalizzazione degli strumenti e della casella degli strumenti.](../modeling/customizing-tools-and-the-toolbox.md)<br /><br /> Includere le forme principale e porta in EGP o definire BoundsRules per posizionare le forme delle porte quando viene creata un'istanza di EGP.|
|Usare uno strumento di connessione per creare un'istanza di diversi tipi di relazione.|Aggiungere direttive di connessione di collegamento (LCD) al generatore di connessioni richiamato dallo strumento. Le LCD determinano il tipo di relazione dai tipi dei due elementi. Per fare in modo che questo dipersi dagli stati degli elementi, è possibile aggiungere codice personalizzato. Vedere [Personalizzazione degli strumenti e della casella degli strumenti.](../modeling/customizing-tools-and-the-toolbox.md)|
|Sticky Tools: l'utente può fare doppio clic su qualsiasi strumento per creare molte forme o connettori in successione.|In Esplora DSL selezionare il `Editor` nodo . Nella finestra Finestra Proprietà impostare **Usa elementi della casella degli strumenti sticky**.|
|Definire i comandi di menu|Vedere [Procedura: Modificare un comando di menu standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Vincolare il modello con le regole di convalida|Vedere [Convalida in un Domain-Specific linguaggio](../modeling/validation-in-a-domain-specific-language.md)|
|Generare codice, file di configurazione o documenti da un DSL.|[Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Personalizzare la modalità di salvataggio dei modelli in un file.|Vedere [Personalizzazione dell'archiviazione file e serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Salvare i modelli in database o altri supporti.|Eseguire *l'override di YourLanguage* DocData<br /><br /> Vedere [Personalizzazione dell'archiviazione file e serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integrare più DSL in modo che funzionino come parte di un'applicazione.|Vedere [Integrazione di modelli con Visual Studio Modelbus.](../modeling/integrating-models-by-using-visual-studio-modelbus.md)|
|Consentire l'estensione del DSL da terze parti e controllare l'estensione.|[Estendere il DSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Condivisione di classi tra DSL utilizzando una libreria DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definizione di un criterio di blocco per creare segmenti di sola lettura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Vedi anche

- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Scrittura di codice per personalizzare un linguaggio Domain-Specific personalizzato](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
