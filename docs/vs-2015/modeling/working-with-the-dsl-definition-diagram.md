---
title: Uso del diagramma di definizione DSL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
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
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 14e365d6bbe99634135bfad133d840b98e22e3b0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72663044"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Utilizzo del diagramma di definizione DSL
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Il diagramma di una definizione [!INCLUDE[dsl](../includes/dsl-md.md)] è uno strumento importante per la definizione del linguaggio specifico di dominio. Consente di aggiungere elementi al modello di dominio e definire relazioni sul diagramma ed è possibile modificare il layout del diagramma per renderlo più leggibile.

## <a name="the-layout-of-the-diagram"></a>Layout del diagramma
 Il diagramma di definizione [!INCLUDE[dsl](../includes/dsl-md.md)] dispone di due partizioni, la partizione **classi e relazioni** e la partizione **elementi diagramma** . Nella partizione **classi e relazioni** vengono visualizzate le classi di dominio, le relazioni di dominio e l'ereditarietà. Nella partizione **elementi diagramma** vengono visualizzate le classi di forme, le classi del connettore, le classi di corsie e il diagramma della finestra di progettazione generata.

 Le classi di dominio possono apparire in più posizioni nelle partizioni **classi e relazioni** . In una definizione di classe di dominio viene visualizzato un albero di ereditarietà se si tratta della classe di base per altre classi di dominio e un albero delle relazioni se si tratta dell'origine delle relazioni di incorporamento o riferimento. I segnaposto delle classi di dominio vengono visualizzati come le destinazioni delle relazioni di incorporamento o riferimento. Per impostazione predefinita, gli elementi segnaposto vengono visualizzati con il raggruppamento delle **proprietà del dominio** compresso. Per questi elementi, non vengono mostrati l'ereditarietà o le relazioni di incorporamento o riferimento.

 Quando si aggiunge una classe di dominio, questa viene visualizzata nella parte inferiore della partizione **classi e relazioni** . Quando si aggiunge una relazione di incorporamento o riferimento, questa viene posizionata a destra sotto la classe di dominio di origine.

 Man mano che si aggiungono classi e relazioni di dominio, può risultare difficile individuare una classe di dominio specifica. È possibile trovare una classe di dominio facendo clic con il pulsante destro del mouse su di essa in **DSL Explorer** e quindi scegliendo **individua nel diagramma**.

 Nelle sezioni seguenti viene descritto come modificare l'aspetto del diagramma per renderlo più leggibile.

## <a name="copying-elements"></a>Copia di elementi
 È possibile usare i comandi Copia, Taglia e Incolla sugli elementi nel diagramma della definizione DSL.

## <a name="zooming-in-or-out-on-the-diagram"></a>Zoom avanti o indietro sul diagramma
 È possibile ingrandire o ridurre il diagramma utilizzando la barra degli strumenti **finestra di progettazione DSL** per impostare il livello di zoom.

## <a name="hiding-map-lines"></a>Nascondere linee mappa
 Le linee mappa sono linee tracciate tra una classe di dominio o una relazione di dominio e la forma o il connettore a cui è mappata. È possibile nascondere le linee mappa facendo clic sul pulsante **Mostra linee mappa** sulla barra degli strumenti **finestra di progettazione DSL** . Per visualizzare le linee, fare di nuovo clic sul pulsante.

## <a name="changing-the-diagram-layout"></a>Modifica del layout del diagramma
 È possibile modificare il layout delle **classi e** della partizione delle relazioni come indicato di seguito.

### <a name="expandcollapse"></a>Expand/Collapse
 È possibile ridurre le dimensioni di un elemento della forma di raggruppamento che rappresenta una classe di dominio o una forma facendo clic con il pulsante destro del mouse su di essa e quindi scegliendo **Comprimi**. Questo nasconde il raggruppamento delle **proprietà del dominio** della forma. Per visualizzare di nuovo il raggruppamento delle **proprietà del dominio** , fare clic con il pulsante destro del mouse sulla forma e scegliere **Espandi**.

### <a name="move-updown"></a>Move Up/Move Down
 È possibile spostare una classe di dominio o un elemento del diagramma verso l'alto o verso il basso nella partizione facendo clic con il pulsante destro del mouse sull'elemento e scegliendo **Sposta su** o **Sposta giù**. Se si sposta un elemento segnaposto visualizzato come destinazione di una relazione di incorporamento o riferimento, la relazione verrà spostata insieme all'elemento.

### <a name="expandcollapse-relationships-tree"></a>Expand/Collapse Relationships Tree
 Se una classe di dominio svolge il ruolo di origine nelle relazioni di incorporamento o riferimento con altre classi di dominio, è possibile nascondere le relazioni facendo clic con il pulsante destro del mouse sulla definizione della classe di dominio e quindi scegliendo **Comprimi albero relazioni**. Per visualizzare le relazioni, fare clic con il pulsante destro del mouse sull'elemento definition, quindi scegliere **Espandi relazioni albero**.

### <a name="expandcollapse-inheritance-tree"></a>Expand/Collapse Inheritance Tree
 Se una classe di dominio è la classe base di altre classi di dominio, è possibile nascondere l'albero di ereditarietà facendo clic con il pulsante destro del mouse sulla definizione della classe di dominio e scegliendo **Comprimi albero di ereditarietà**. Per visualizzare l'albero di ereditarietà, fare clic con il pulsante destro del mouse sull'elemento definition, quindi scegliere **Espandi albero di ereditarietà**.

### <a name="bring-tree-here"></a>Bring Tree Here
 Per consolidare il diagramma, fare clic con il pulsante destro del mouse su una classe di dominio segnaposto e quindi scegliere **Bring Tree qui**. La classe di dominio segnaposto diventa un elemento della definizione e visualizza gli alberi di ereditarietà e delle relazioni. L'elemento della definizione precedente diventa un elemento segnaposto se costituisce la destinazione di una relazione o l'elemento figlio in una relazione di ereditarietà; in caso contrario, non viene più visualizzato.

### <a name="split-tree"></a>Split Tree
 È possibile suddividere gli alberi di ereditarietà o di relazioni facendo clic con il pulsante destro del mouse sulla definizione della classe di dominio che li Visualizza e quindi scegliendo **Split Tree**. L'elemento della definizione diventa un elemento segnaposto e la classe di dominio della definizione, insieme ai relativi alberi di ereditarietà e delle relazioni, è ora visualizzata nella parte inferiore della partizione.

### <a name="show-as-class"></a>Show As Class
 Se una relazione di dominio dispone di relazioni derivate o se presenta relazioni di incorporamento o riferimento con altre relazioni di dominio, è possibile visualizzare la relazione come classe facendo clic con il pulsante destro del mouse sulla relazione e quindi scegliendo **Mostra come classe**. La relazione verrà visualizzata con un raggruppamento delle **proprietà del dominio** e mostrerà gli alberi ereditarietà e relazioni.

## <a name="see-also"></a>Vedere anche
 [Glossario di Strumenti Domain-Specific Language](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)
