---
title: Personalizzazione ed estensione di un linguaggio specifico di dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, creating solutions
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9040e65d3e9acce101ee6b481c2cd27d24285169
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75597165"
---
# <a name="customize-and-extend-a-domain-specific-language"></a>Personalizzare ed estendere un linguaggio specifico di dominio

Visual Studio Modeling and Visualization SDK (VMSDK) offre diversi livelli in cui è possibile definire gli strumenti di modellazione:

1. Definire un linguaggio specifico di dominio (DSL) utilizzando il diagramma di definizione DSL. È possibile creare rapidamente un linguaggio DSL con una notazione diagrammatiche, un modulo XML leggibile e gli strumenti di base necessari per generare codice e altri artefatti. Per ulteriori informazioni, vedere [come definire un Domain-Specific Language](../modeling/how-to-define-a-domain-specific-language.md).

2. Ottimizzare il linguaggio DSL utilizzando funzionalità più avanzate della definizione DSL. È ad esempio possibile fare in modo che vengano visualizzati altri collegamenti quando l'utente crea un elemento. Queste tecniche vengono principalmente realizzate nella definizione DSL e alcune richiedono alcune righe di codice programma.

3. Estendi gli strumenti di modellazione usando il codice programma. VMSDK è progettato in modo specifico per facilitare l'integrazione delle estensioni con il codice generato dalla definizione DSL. Per ulteriori informazioni, vedere [scrittura di codice per personalizzare un Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md).

> [!NOTE]
> Dopo aver aggiornato il file delle definizioni DSL, non dimenticare di fare clic su **trasforma tutti i modelli** nella barra degli strumenti di **Esplora soluzioni** prima di ricompilare la soluzione.

## <a name="article-reference"></a>Riferimento all'articolo

|Per ottenere questo effetto|Vedere questo argomento|
|-|-|
|Consente all'utente di impostare le proprietà relative al colore e allo stile di una forma.|Fare clic con il pulsante destro del mouse sulla classe Shape o Connector, scegliere **Aggiungi esposto**, quindi fare clic su un elemento.|
|Classi diverse di elementi del modello hanno un aspetto simile a quello del diagramma e condividono proprietà quali l'altezza iniziale e la larghezza, il colore e le descrizioni comandi.|Usare l'ereditarietà tra forme o classi di connettori. I mapping tra le forme derivate e le classi di dominio derivate ereditano i dettagli del mapping degli elementi padre.<br /><br /> In alternativa, eseguire il mapping di classi di dominio diverse alla stessa classe Shape.|
|Una classe di elemento del modello viene visualizzata da diversi contesti di forme.|Eseguire il mapping di più classi di forme alla stessa classe di dominio. Quando si compila la soluzione, seguire la segnalazione errori e fornire il codice richiesto per decidere quale forma utilizzare.|
|Il colore della forma o altre funzionalità, ad esempio tipo di carattere, indicano lo stato corrente.|Vedere [aggiornamento di forme e connettori per riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> Creare una regola che aggiorna le proprietà esposte. Vedere le [regole propagano le modifiche all'interno del modello](../modeling/rules-propagate-changes-within-the-model.md).<br /><br /> In alternativa, usare OnAssociatedPropertyChanged () per aggiornare le funzionalità non esposte, ad esempio le frecce dei collegamenti o il tipo di carattere.|
|L'icona di forma cambia per indicare lo stato.|Imposta la visibilità del mapping dell'elemento Decorator nella finestra Dettagli DSL. Individuare diversi elementi Decorator immagine nella stessa posizione. Vedere  [aggiornamento di forme e connettori per riflettere il modello](../modeling/updating-shapes-and-connectors-to-reflect-the-model.md).<br /><br /> In alternativa, eseguire l'override di `ImageField.GetDisplayImage()` . Vedere l'esempio in <xref:Microsoft.VisualStudio.Modeling.Diagrams.ImageField> .|
|Imposta un'immagine di sfondo in qualsiasi forma|Eseguire l'override di InitializeInstanceResources () per aggiungere un ImageField ancorato.|
|Annidare forme a qualsiasi profondità|Configurare un albero di incorporamento ricorsivo. Definire BoundsRules per contenere le forme.|
|Alleghi i connettori nei punti fissi sul limite di un elemento.|Definisce gli elementi terminali incorporati, rappresentati da porte di piccole dimensioni nel diagramma. Usare BoundsRules per correggere le porte sul posto. Vedere l'esempio di diagramma di circuito nell' [SDK di visualizzazione e modellazione](https://code.msdn.microsoft.com/Visualization-and-Modeling-313535db).|
|Campo di testo Visualizza un valore derivato da altri valori.|Eseguire il mapping dell'elemento Decorator del testo a una proprietà del dominio di archiviazione calcolata o personalizzata. Per altre informazioni, vedere [proprietà di archiviazione calcolate e personalizzate](../modeling/calculated-and-custom-storage-properties.md).|
|Propagazione delle modifiche tra gli elementi del modello o tra forme|Vedere [convalida in un Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md).|
|Propagare le modifiche alle risorse, ad esempio altre estensioni di Visual Studio all'esterno dello Store.|Vedere [i gestori eventi propagano le modifiche al di fuori del modello](../modeling/event-handlers-propagate-changes-outside-the-model.md).|
|Finestra delle proprietà Visualizza le proprietà di un elemento correlato.|Configurare l'invio della proprietà. Vedere [personalizzazione della finestra delle proprietà](../modeling/customizing-the-properties-window.md).|
|Categorie di proprietà|La finestra proprietà è divisa in sezioni denominate categorie. Impostare la **categoria** delle proprietà del dominio. Nella stessa sezione verranno visualizzate le proprietà con lo stesso nome di categoria. È inoltre possibile impostare la **categoria** di un ruolo di relazione.|
|Controllare l'accesso degli utenti alle proprietà del dominio|Set **è esplorabile** false per impedire la visualizzazione di una proprietà di dominio nel finestra Proprietà in fase di esecuzione. È comunque possibile eseguirne il mapping agli elementi Decorator di testo.<br /><br /> L' **interfaccia utente di sola lettura** impedisce agli utenti di modificare una proprietà di dominio.<br /><br /> L'accesso al programma alla proprietà del dominio non è interessato.|
|Modificare il nome, l'icona e la visibilità dei nodi in Esplora modelli del DSL.|Vedere [personalizzazione di Esplora modelli](../modeling/customizing-the-model-explorer.md).|
|Abilita copia, taglia e incolla|Impostare la proprietà **Abilita copia incolla** del nodo **Editor** in DSL Explorer.|
|Copia i collegamenti di riferimento e le relative destinazioni ogni volta che viene copiato un elemento. Ad esempio, copiare i commenti allegati a un elemento.|Impostare la proprietà **propaga copia** del ruolo di origine, rappresentata dalla riga su un lato della relazione di dominio nel diagramma di definizione DSL.<br /><br /> Scrivere codice per eseguire l'override di ProcessOnCopy per ottenere effetti più complessi.<br /><br /> Vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|
|Elimina, ripadre o ricollega gli elementi correlati quando viene eliminato un elemento.|Imposta il valore per la **propagazione dell'eliminazione** di un ruolo di relazione. Per gli effetti più complessi, eseguire l'override `ShouldVisitRelationship` `ShouldVisitRolePlayer` dei metodi e nella `MyDslDeleteClosure` classe, definiti in **DomainModel.cs**.|
|Mantiene il layout e l'aspetto delle forme in copia e trascinamento della selezione.|Aggiungere le forme e i connettori all'oggetto copiato `ElementGroupPrototype` . Il metodo più pratico per eseguire l'override è `ElementOperations.CreateElementGroupPrototype()`<br /><br /> Vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|
|Incollare le forme in una posizione prescelta, ad esempio la posizione del cursore attuale.|Eseguire l'override `ClipboardCommandSet.ProcessOnCopy()` di per usare la versione specifica del percorso di `ElementOperations.Merge().` , vedere [personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|
|Crea collegamenti aggiuntivi all'incolla|Eseguire l'override di ClipboardCommandSet. ProcessOnPasteCommand ()|
|Abilita il trascinamento della selezione da questo diagramma, altri elementi DSLs e Windows|Vedere [procedura: aggiungere un gestore di trascinamento della selezione](../modeling/how-to-add-a-drag-and-drop-handler.md)|
|Consentire il trascinamento di una forma o di uno strumento su una forma figlio, ad esempio una porta, come se fosse stato trascinato nell'elemento padre.|Definire una direttiva di Unione elementi nella classe dell'oggetto di destinazione per l'invio dell'oggetto rilasciato all'elemento padre. Vedere [personalizzazione della creazione e dello spostamento di elementi](../modeling/customizing-element-creation-and-movement.md).|
|Consente di trascinare una forma o uno strumento su una forma e di creare collegamenti o oggetti aggiuntivi. Ad esempio, per consentire l'eliminazione di un commento su un elemento a cui deve essere collegato.|Definire una direttiva di Unione elementi nella classe di dominio di destinazione e definire i collegamenti da generare. In casi complessi, è possibile aggiungere codice personalizzato. Vedere [personalizzazione della creazione e dello spostamento di elementi](../modeling/customizing-element-creation-and-movement.md).|
|Creare un gruppo di elementi con uno strumento. Ad esempio, un componente con un set fisso di porte.|Eseguire l'override del metodo di inizializzazione casella degli strumenti in ToolboxHelper.cs. Creare un prototipo di gruppo di elementi (EGP) contenente gli elementi e i relativi collegamenti di relazione. Vedere [personalizzazione degli strumenti e della casella degli](../modeling/customizing-tools-and-the-toolbox.md)strumenti.<br /><br /> Includere le forme principale e porta in EGP oppure definire BoundsRules per posizionare le forme della porta quando viene creata un'istanza di EGP.|
|Usare uno strumento di connessione per creare un'istanza di diversi tipi di relazione.|Aggiungere le direttive di connessione a collegamento (LCD) al generatore di connessione richiamato dallo strumento. Gli LCD determinano il tipo di relazione tra i tipi dei due elementi. Per fare in modo che ciò dipenda dagli Stati degli elementi, è possibile aggiungere codice personalizzato. Vedere [personalizzazione degli strumenti e della casella degli](../modeling/customizing-tools-and-the-toolbox.md)strumenti.|
|Sticky Tools: l'utente può fare doppio clic su qualsiasi strumento per creare più forme o connettori in successione.|In DSL Explorer selezionare il `Editor` nodo. Nella Finestra Proprietà impostare **utilizza gli elementi Sticky della casella degli strumenti**.|
|Definire i comandi di menu|Vedere [procedura: modificare un comando di menu standard](../modeling/how-to-modify-a-standard-menu-command-in-a-domain-specific-language.md)|
|Vincolare il modello con le regole di convalida|Vedere [convalida in un Domain-Specific Language](../modeling/validation-in-a-domain-specific-language.md)|
|Generare codice, file di configurazione o documenti da un linguaggio DSL.|[Generazione di codice da un linguaggio specifico di dominio](../modeling/generating-code-from-a-domain-specific-language.md)|
|Personalizzare il modo in cui i modelli vengono salvati in un file.|Vedere [personalizzazione dell'archiviazione file e della serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Salvare i modelli nei database o in altri supporti.|Eseguire l'override di *linguaggioutente*DocData<br /><br /> Vedere [personalizzazione dell'archiviazione file e della serializzazione XML](../modeling/customizing-file-storage-and-xml-serialization.md)|
|Integrare diversi DSLs in modo che funzionino come parte di un'applicazione.|Vedere [integrazione di modelli tramite ModelBus di Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md).|
|Consente di estendere il linguaggio DSL da terze parti e di controllare l'estensione.|[Estendere il DSL mediante MEF](../modeling/extend-your-dsl-by-using-mef.md)<br /><br /> [Condivisione di classi tra DSL utilizzando una libreria DSL](../modeling/sharing-classes-between-dsls-by-using-a-dsl-library.md)<br /><br /> [Definizione di un criterio di blocco per creare segmenti di sola lettura](../modeling/defining-a-locking-policy-to-create-read-only-segments.md)|

## <a name="see-also"></a>Vedere anche

- [Come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md)
- [Scrittura di codice per personalizzare un Domain-Specific Language](../modeling/writing-code-to-customise-a-domain-specific-language.md)
- [SDK di modellazione per Visual Studio (linguaggi specifici di dominio)](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
