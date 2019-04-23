---
title: Personalizzazione ed estensione di un linguaggio specifico di dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8383e82091ec9cc62f5b08dcc89f1e1e74239030
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60096790"
---
# <a name="customizing-and-extending-a-domain-specific-language"></a>Personalizzazione ed estensione di un linguaggio specifico di dominio
Visual Studio Modeling e visualizzazione SDK (VMSDK) offre diversi livelli in corrispondenza del quale è possibile definire gli strumenti di modellazione:

1. Definire un linguaggio specifico di dominio (DSL) mediante il diagramma di definizione DSL. È possibile creare rapidamente un linguaggio DSL con una notazione basata su diagramma, un formato XML leggibile e gli strumenti di base necessarie per generare il codice e altri elementi.

     Per altre informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).

2. Ottimizzare il linguaggio DSL utilizzando le funzionalità più avanzate della definizione DSL. Ad esempio, è possibile visualizzare collegamenti aggiuntivi quando l'utente crea un elemento. Queste tecniche vengono realizzate nella definizione DSL e alcune richiedono poche righe di codice del programma.

3. Estendere gli strumenti di modellazione usando codice programma. VMSDK è progettato in modo specifico per facilitare l'integrazione delle estensioni con il codice generato dalla definizione DSL.  Per altre informazioni, vedere [scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
>  Dopo aver aggiornato il file di definizione DSL, non dimenticare di fare clic su **Trasforma tutti i modelli** sulla barra degli strumenti di Esplora soluzioni prima di ricompilare la soluzione.

## <a name="customShapes"></a> In questa sezione

|Per ottenere questo effetto|Fare riferimento a questo argomento|
|-|-|
|Consentire all'utente di impostare le proprietà di colore e stile di una forma.|La classe di forma o connettore di fare doppio clic su, scegliere **Aggiungi esposta**, fare clic su un elemento.<br /><br /> Visualizzare [personalizzazione della presentazione nel diagramma](../modeling/customizing-presentation-on-the-diagram.md).|
|Diverse classi di elemento del modello simile nel diagramma, la condivisione di proprietà, ad esempio l'altezza iniziale e la larghezza, colore, le descrizioni comandi.|Utilizzare l'ereditarietà tra le forme o classi di connettore. I mapping tra le forme derivate e le classi di dominio derivate ereditano i dettagli del mapping di elementi padre.<br /><br /> In alternativa, eseguire il mapping di classi di dominio diverso per la stessa classe shape.|
|Una classe di elemento del modello viene visualizzata per contesti di diverse forme.|Eseguire il mapping di più di una classe di forma alla stessa classe di dominio. Quando si compila la soluzione, seguire la segnalazione errori e fornire il codice richiesto per decidere quale forma da utilizzare.|
|Colore della forma o altre funzionalità, ad esempio tipo di carattere indicano lo stato corrente.|Visualizzare [aggiornamento di forme e connettori per riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Creare una regola che aggiorna le proprietà esposte. Visualizzare [le regole propagano le modifiche apportate all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> In alternativa, usare OnAssociatedPropertyChanged() da aggiornare non esposto a funzionalità quali le frecce di collegamento o del tipo di carattere.|
|Icona su Cambia forma per indicare lo stato.|Impostare la visibilità del mapping dell'elemento decorator nella finestra Dettagli DSL. Individuare elementi Decorator di immagine diversi nella stessa posizione. Visualizzare [aggiornamento di forme e connettori per riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> In alternativa, eseguire l'override `ImageField.GetDisplayImage()`. Vedere l'esempio in <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField>.|
|Impostare un'immagine di sfondo per qualsiasi forma|Eseguire l'override InitializeInstanceResources() per aggiungere un ancoraggio ImageField. Visualizzare [personalizzazione della presentazione nel diagramma](../modeling/customizing-presentation-on-the-diagram.md).|
|Annidare forme a qualsiasi profondità|Consente di impostare una ricorsiva dell'albero di incorporamento. Definire BoundsRules per contenere le forme. Visualizzare [personalizzazione della presentazione nel diagramma](../modeling/customizing-presentation-on-the-diagram.md).|
|Collegare i connettori in fissi punti sul bordo di un elemento.|Definire gli elementi incorporati terminali, rappresentati dalle porte di piccole dimensioni nel diagramma. Usare BoundsRules per risolvere le porte posto. Vedere l'esempio di diagramma circuito [Visualization and Modeling SDK](http://go.microsoft.com/fwlink/?LinkID=186128).|
|Campo di testo viene visualizzato un valore derivato da altri valori.|Eseguire il mapping dell'elemento decorator di testo a una proprietà di dominio Calculated o archiviazione personalizzata. Per altre informazioni, vedere [calcolate e le proprietà di archiviazione personalizzate](../modeling/calculated-and-custom-storage-properties.md).|
|Propagazione delle modifiche tra gli elementi del modello, oppure tra le forme|Visualizzare [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md).|
|Propagare le modifiche alle risorse, ad esempio altre estensioni di Visual Studio all'esterno dell'archivio.|Visualizzare [gestori eventi propagano le modifiche all'esterno del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Finestra delle proprietà vengono visualizzate le proprietà di un elemento correlato.|Impostare le proprietà di inoltro. Visualizzare [personalizzazione della finestra proprietà](../modeling/customizing-the-properties-window.md).|
|Categorie di proprietà|Finestra delle proprietà è suddiviso in sezioni denominate le categorie. Impostare il **categoria** delle proprietà di dominio. Proprietà con lo stesso nome di categoria verranno visualizzate nella stessa sezione. È anche possibile impostare il **categoria** di un ruolo della relazione.|
|Controllare l'accesso utente alle proprietà di dominio|Impostare **è visualizzabile** false per impedire che una proprietà di dominio visualizzati nella finestra proprietà in fase di esecuzione. È possibile comunque eseguirne il mapping di elementi Decorator di testo.<br /><br /> **È di sola lettura nell'interfaccia utente** impedisce agli utenti di modificare una proprietà di dominio.<br /><br /> Accesso ai programmi per la proprietà di dominio non è interessato.|
|Modificare il nome, l'icona e la visibilità dei nodi in Esplora modelli del linguaggio DSL.|Visualizzare [personalizzazione di Esplora modelli](../modeling/customizing-the-model-explorer.md).|
|Abilitare la copia, Taglia e Incolla|Impostare il **Abilita Copia/Incolla** proprietà delle **Editor** nodo in Esplora DSL.|
|Copiare i collegamenti di riferimento e alle destinazioni, ogni volta che un elemento viene copiato. Ad esempio, copiare i commenti collegati a un elemento.|Impostare il **propaga copia** proprietà del ruolo di origine (rappresentato dalla linea su un lato della relazione di dominio nel diagramma di definizione DSL).<br /><br /> Scrivere codice per eseguire l'override ProcessOnCopy per ottenere effetti più complessi.<br /><br /> Visualizzare [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|
|Eliminare, assegnare un nuovo elemento o ricollegare elementi correlati quando viene eliminato un elemento.|Impostare il **Propaga eliminazione** pari a un ruolo della relazione. Per ottenere effetti più complessi, eseguire l'override `ShouldVisitRelationship` e `ShouldVisitRolePlayer` metodi nel `MyDslDeleteClosure` classe, definita nella **DomainModel.cs**.|
|Mantenere il layout di forme e appaiono sulla copia e trascinare.|Aggiungere le forme e connettori per l'insieme copiato `ElementGroupPrototype`. È il metodo più semplice per eseguire l'override `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Visualizzare [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|
|Incollare le forme in una posizione prescelta, ad esempio la posizione del cursore attuale.|Eseguire l'override `ClipboardCommandSet.ProcessOnCopy()` usare la versione del percorso specifica `ElementOperations.Merge().` vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|
|Creare collegamenti aggiuntivi quando si incolla|Override ClipboardCommandSet.ProcessOnPasteCommand()|
|Abilita il trascinamento da questo diagramma, altri linguaggi specifici di dominio e Windows elementi|Vedere [How to: Aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Consentire una forma o dello strumento è possibile trascinare una forma figlio, ad esempio una porta, come se si sono stato trascinato l'elemento padre.|Definire una direttiva di unione elementi nella classe di oggetto di destinazione, per inoltrare l'oggetto rilasciato per l'elemento padre. Visualizzare [personalizzazione di spostamento e la creazione dell'elemento](../modeling/customizing-element-creation-and-movement.md).|
|Consentire una forma o lo strumento è possibile trascinare una forma e collegamenti aggiuntivi o gli oggetti creati. Ad esempio, per consentire a trascinare un elemento a cui è possibile collegare un commento.|Definire una direttiva di unione elementi nella classe di dominio di destinazione e i collegamenti da generare. In scenari complessi, è possibile aggiungere codice personalizzato. Visualizzare [personalizzazione di spostamento e la creazione dell'elemento](../modeling/customizing-element-creation-and-movement.md).|
|Creare un gruppo di elementi con uno degli strumenti. Ad esempio, un componente con un set fisso di porte.|Eseguire l'override del metodo di inizializzazione della casella degli strumenti in ToolboxHelper.cs. Creare un prototipo di gruppo elemento (EGP) che contiene gli elementi e i relativi collegamenti di relazione. Visualizzare [personalizzazione di strumenti e la casella degli strumenti](../modeling/customizing-tools-and-the-toolbox.md).<br /><br /> Includere le forme dell'entità e la porte in EGP oppure definire BoundsRules per posizionare le forme porta quando viene creata un'istanza di EGP.|
|Usare uno strumento di connessione per creare un'istanza di diversi tipi di relazione.|Aggiungere direttive di connessione collegamento (LCD) per il generatore di connessione che viene richiamato dallo strumento. Il monitor LCD a determinare il tipo della relazione tra i tipi dei due elementi. Per semplificare questa dipendono gli stati degli elementi, è possibile aggiungere codice personalizzato. Visualizzare [personalizzazione di strumenti e la casella degli strumenti](../modeling/customizing-tools-and-the-toolbox.md).|
|Sticky strumenti - l'utente può fare doppio clic su qualsiasi strumento per creare molte forme o connettori in successione.|In Esplora DSL, selezionare il `Editor` nodo. Nella finestra Proprietà impostare **Usa permanenti gli elementi della casella degli strumenti**.|
|Definire i comandi di menu|Vedere [How to: Modificare un comando di menu standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Vincolare il modello con le regole di convalida|Vedere [convalida in un linguaggio specifico di dominio](../modeling/validation-in-a-domain-specific-language.md)|
|Generare codice, i file di configurazione o documenti da un linguaggio DSL.|[Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Personalizzare la modalità con cui i modelli vengono salvati in file.|Vedere [personalizzazione dell'archiviazione di File e serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Salvare i modelli per i database o altri supporti.|Eseguire l'override *Linguaggioutente*DocData<br /><br /> Vedere [personalizzazione dell'archiviazione di File e serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integrare diverse soluzioni DSL in modo che funzionano come parte di un'applicazione.|Visualizzare [l'integrazione di modelli tramite Modelbus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Consenti il linguaggio DSL di essere esteso da terze parti e controllare l'estensione.|[Estendere il DSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Condivisione di classi tra DSL usando una libreria DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definizione di un criterio di blocco per creare segmenti di sola lettura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Vedere anche

- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Scrittura di codice per personalizzare un linguaggio specifico di dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
