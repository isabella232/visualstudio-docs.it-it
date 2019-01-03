---
title: Utilizzo del diagramma di definizione DSL
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.dsldesigner.diagram
- vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords:
- Domain-Specific Language Tools, diagram
- Domain-Specific Language Tools, Split Tree
- Domain-Specific Language Tools, Show Map Lines
- Domain-Specific Language Tools, Show As Class
- Domain-Specific Language Tools, Bring Tree Here
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: 2c95d1a096d2b7d90292711ae53117321e54746b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53888426"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Utilizzo del diagramma di definizione DSL
Il diagramma di un [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] definizione è uno strumento importante per la definizione di linguaggio specifico di dominio. Consente di aggiungere elementi al modello di dominio e definire relazioni sul diagramma ed è possibile modificare il layout del diagramma per renderlo più leggibile.

## <a name="the-layout-of-the-diagram"></a>Layout del diagramma
 Il [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] diagramma di definizione ha due partizioni, il **Classes and Relationships** partizione e il **Diagram Elements** partizione. Il **Classes and Relationships** partizione consente di visualizzare le classi di dominio, relazioni di dominio e l'ereditarietà. Il **Diagram Elements** partizione consente di visualizzare le classi di forma, connettore classi, classi di corsia e il diagramma della finestra di progettazione generato.

 Classi di dominio può essere presente in più posizioni nel **Classes and Relationships** partizioni. In una definizione di classe di dominio viene visualizzato un albero di ereditarietà se si tratta della classe di base per altre classi di dominio e un albero delle relazioni se si tratta dell'origine delle relazioni di incorporamento o riferimento. I segnaposto delle classi di dominio vengono visualizzati come le destinazioni delle relazioni di incorporamento o riferimento. Per impostazione predefinita, gli elementi segnaposto sono visualizzati con il **delle proprietà di dominio** raggruppamento compressa. Per questi elementi, non vengono mostrati l'ereditarietà o le relazioni di incorporamento o riferimento.

 Quando si aggiunge una classe di dominio, viene visualizzato nella parte inferiore del **Classes and Relationships** partizione. Quando si aggiunge una relazione di incorporamento o riferimento, questa viene posizionata a destra sotto la classe di dominio di origine.

 Man mano che si aggiungono classi e relazioni di dominio, può risultare difficile individuare una classe di dominio specifica. È possibile trovare una classe di dominio facendo clic su esso nel **DSL Explorer** e quindi scegliendo **Locate in Diagram**.

 Nelle sezioni seguenti viene descritto come modificare l'aspetto del diagramma per renderlo più leggibile.

## <a name="copying-elements"></a>Copia di elementi
 È possibile usare i comandi Copia, Taglia e Incolla sugli elementi nel diagramma della definizione DSL.

## <a name="zooming-in-or-out-on-the-diagram"></a>Zoom avanti o indietro sul diagramma
 È possibile eseguire lo zoom avanti o indietro sul diagramma usando il **finestra di progettazione DSL** sulla barra degli strumenti per impostare il livello di zoom.

## <a name="hiding-map-lines"></a>Nascondere linee mappa
 Le linee mappa sono linee tracciate tra una classe di dominio o una relazione di dominio e la forma o il connettore a cui è mappata. È possibile nascondere linee mappa facendo il **Show Map Lines** pulsante il **finestra di progettazione DSL** sulla barra degli strumenti. Per visualizzare le linee, fare di nuovo clic sul pulsante.

## <a name="changing-the-diagram-layout"></a>Modifica del layout del diagramma
 È possibile modificare il layout del **Classes and Relationships** partizione come indicato di seguito.

### <a name="expandcollapse"></a>Expand/Collapse
 È possibile ridurre le dimensioni di un elemento della forma raggruppamento che rappresenta una classe di dominio o una forma facendo clic destro e quindi scegliendo **Comprimi**. Ciò consente di nascondere il **delle proprietà di dominio** raggruppamento della forma. Per visualizzare il **Domain Properties** compartment. anche in questo caso, fare doppio clic la forma e quindi fare clic su **Espandi**.

### <a name="move-updown"></a>Move Up/Move Down
 È possibile spostare un elemento di classe o il diagramma del dominio verso l'alto o verso il basso nella partizione facendo l'elemento e scegliendo **Move Up** oppure **Sposta giù**. Se si sposta un elemento segnaposto visualizzato come destinazione di una relazione di incorporamento o riferimento, la relazione verrà spostata insieme all'elemento.

### <a name="expandcollapse-relationships-tree"></a>Expand/Collapse Relationships Tree
 Se una classe di dominio svolge un ruolo di origine in una relazione di incorporamento o riferimento con altre classi di dominio, è possibile nascondere le relazioni facendo clic sulla definizione di classe di dominio e quindi scegliendo **Collapse Relationships Tree**. Per mostrare le relazioni, fare clic sull'elemento di definizione e quindi fare clic su **Expand Relationships Tree**.

### <a name="expandcollapse-inheritance-tree"></a>Expand/Collapse Inheritance Tree
 Se una classe di dominio è la classe di base di altre classi di dominio, è possibile nascondere l'albero di ereditarietà facendo la definizione di classe di dominio e quindi scegliendo **Collapse Inheritance Tree**. Per visualizzare l'albero di ereditarietà, fare clic sull'elemento di definizione e quindi fare clic su **Expand Inheritance Tree**.

### <a name="bring-tree-here"></a>Bring Tree Here
 È possibile consolidare il diagramma facendo clic su una classe di dominio segnaposto e scegliendo **Bring Tree Here**. La classe di dominio segnaposto diventa un elemento della definizione e visualizza gli alberi di ereditarietà e delle relazioni. L'elemento della definizione precedente diventa un elemento segnaposto se costituisce la destinazione di una relazione o l'elemento figlio in una relazione di ereditarietà; in caso contrario, non viene più visualizzato.

### <a name="split-tree"></a>Split Tree
 È possibile interrompere uscita alberi di ereditarietà o delle relazioni facendo clic sulla definizione della classe di dominio che li visualizza e quindi facendo clic su **Dividi albero**. L'elemento della definizione diventa un elemento segnaposto e la classe di dominio della definizione, insieme ai relativi alberi di ereditarietà e delle relazioni, è ora visualizzata nella parte inferiore della partizione.

### <a name="show-as-class"></a>Show As Class
 Se una relazione di dominio ha relazioni derivate o se ha relazioni di incorporamento o riferimento con altre relazioni di dominio, è possibile visualizzare la relazione come classe facendo clic sulla relazione e quindi facendo clic su **Show As Class** . Verrà visualizzata la relazione con un **delle proprietà di dominio** raggruppamento e verranno visualizzati gli alberi di ereditarietà e le relazioni.

## <a name="see-also"></a>Vedere anche

- [Glossario sugli strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)