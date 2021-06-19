---
title: Utilizzo del diagramma di definizione DSL
description: Si apprenderà che il diagramma di una definizione di strumenti DSL è uno strumento importante per la definizione di un linguaggio specifico di dominio.
ms.custom: SEO-VS-2020
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
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: f401fe0509fc425fff873a7dc224c69359156861
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388074"
---
# <a name="working-with-the-dsl-definition-diagram"></a>Utilizzo del diagramma di definizione DSL
Il diagramma di una [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] definizione è uno strumento importante per la definizione del linguaggio specifico di dominio. Consente di aggiungere elementi al modello di dominio e definire relazioni sul diagramma ed è possibile modificare il layout del diagramma per renderlo più leggibile.

## <a name="the-layout-of-the-diagram"></a>Layout del diagramma
 Il [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] diagramma delle definizioni include due partizioni, **classes e relationships e** la partizione Diagram **Elements.** La **partizione Classi e relazioni visualizza** le classi di dominio, le relazioni di dominio e l'ereditarietà. La **partizione Elementi diagramma** visualizza le classi di forme, le classi connettore, le classi corsie e il diagramma della finestra di progettazione generato.

 Le classi di dominio possono essere visualizzate in più posizioni **nelle partizioni Classi** e Relazioni. In una definizione di classe di dominio viene visualizzato un albero di ereditarietà se si tratta della classe di base per altre classi di dominio e un albero delle relazioni se si tratta dell'origine delle relazioni di incorporamento o riferimento. I segnaposto delle classi di dominio vengono visualizzati come le destinazioni delle relazioni di incorporamento o riferimento. Per impostazione predefinita, gli elementi segnaposto vengono visualizzati con il **raggruppamento Proprietà dominio** compresso. Per questi elementi, non vengono mostrati l'ereditarietà o le relazioni di incorporamento o riferimento.

 Quando si aggiunge una classe di dominio, questa viene visualizzata nella parte inferiore della **partizione Classi e** relazioni. Quando si aggiunge una relazione di incorporamento o riferimento, questa viene posizionata a destra sotto la classe di dominio di origine.

 Man mano che si aggiungono classi e relazioni di dominio, può risultare difficile individuare una classe di dominio specifica. È possibile trovare una classe di dominio facendo clic con il pulsante destro del mouse su di essa in **Esplora DSL** e quindi scegliendo **Individua nel diagramma.**

 Nelle sezioni seguenti viene descritto come modificare l'aspetto del diagramma per renderlo più leggibile.

## <a name="copying-elements"></a>Copia di elementi
 È possibile usare i comandi Copia, Taglia e Incolla sugli elementi nel diagramma della definizione DSL.

## <a name="zooming-in-or-out-on-the-diagram"></a>Zoom avanti o indietro sul diagramma
 È possibile ingrandire o ridurre il diagramma usando la barra degli strumenti Finestra di progettazione DSL **per** impostare il livello di zoom.

## <a name="hiding-map-lines"></a>Nascondere linee mappa
 Le linee mappa sono linee tracciate tra una classe di dominio o una relazione di dominio e la forma o il connettore a cui è mappata. È possibile nascondere le linee della mappa facendo clic **sul pulsante Mostra linee** mappa sulla barra Finestra di progettazione DSL barra **degli** strumenti. Per visualizzare le linee, fare di nuovo clic sul pulsante.

## <a name="changing-the-diagram-layout"></a>Modifica del layout del diagramma
 È possibile modificare il layout della partizione **Classi e** relazioni come indicato di seguito.

### <a name="expandcollapse"></a>Expand/Collapse
 È possibile ridurre le dimensioni di un elemento forma raggruppamento che rappresenta una classe di dominio o una forma facendo clic con il pulsante destro del mouse su di essa e quindi scegliendo **Comprimi.** In questo modo viene **nascosto il raggruppamento Proprietà** dominio della forma. Per visualizzare di nuovo il **raggruppamento Proprietà dominio,** fare clic con il pulsante destro del mouse sulla forma e quindi scegliere **Espandi**.

### <a name="move-updown"></a>Move Up/Move Down
 È possibile spostare una classe di dominio o un elemento diagramma verso l'alto o verso il basso nella partizione facendo clic con il pulsante destro del mouse sull'elemento e quindi scegliendo Sposta **su** **o Sposta giù.** Se si sposta un elemento segnaposto visualizzato come destinazione di una relazione di incorporamento o riferimento, la relazione verrà spostata insieme all'elemento.

### <a name="expandcollapse-relationships-tree"></a>Expand/Collapse Relationships Tree
 Se una classe di dominio svolge il ruolo di origine nell'incorporamento o nelle relazioni di riferimento con altre classi di dominio, è possibile nascondere le relazioni facendo clic con il pulsante destro del mouse sulla definizione della classe di dominio e quindi scegliendo Comprimi albero **relazioni**. Per visualizzare le relazioni, fare clic con il pulsante destro del mouse sull'elemento di definizione e quindi scegliere **Espandi albero relazioni**.

### <a name="expandcollapse-inheritance-tree"></a>Expand/Collapse Inheritance Tree
 Se una classe di dominio è la classe di base di altre classi di dominio, è possibile nascondere l'albero di ereditarietà facendo clic con il pulsante destro del mouse sulla definizione della classe di dominio e quindi scegliendo **Comprimi albero ereditarietà**. Per visualizzare l'albero di ereditarietà, fare clic con il pulsante destro del mouse sull'elemento di definizione e quindi scegliere **Espandi albero ereditarietà**.

### <a name="bring-tree-here"></a>Bring Tree Here
 È possibile consolidare il diagramma facendo clic con il pulsante destro del mouse su una classe di dominio segnaposto e quindi scegliendo Bring Tree Here (Porta **albero qui).** La classe di dominio segnaposto diventa un elemento della definizione e visualizza gli alberi di ereditarietà e delle relazioni. L'elemento della definizione precedente diventa un elemento segnaposto se costituisce la destinazione di una relazione o l'elemento figlio in una relazione di ereditarietà; in caso contrario, non viene più visualizzato.

### <a name="split-tree"></a>Split Tree
 È possibile suddividere l'ereditarietà o gli alberi delle relazioni facendo clic con il pulsante destro del mouse sulla definizione di classe di dominio che li visualizza e quindi scegliendo **Split Tree (Dividi albero).** L'elemento della definizione diventa un elemento segnaposto e la classe di dominio della definizione, insieme ai relativi alberi di ereditarietà e delle relazioni, è ora visualizzata nella parte inferiore della partizione.

### <a name="show-as-class"></a>Show As Class
 Se una relazione di dominio ha relazioni derivate o se include relazioni di incorporamento o riferimento con altre relazioni di dominio, è possibile visualizzare la relazione come classe facendo clic con il pulsante destro del mouse sulla relazione e quindi scegliendo Mostra come **classe**. La relazione verrà visualizzata  con un raggruppamento Proprietà dominio e mostrerà gli alberi di ereditarietà e relazioni.

## <a name="see-also"></a>Vedi anche

- [Glossario di Strumenti Domain-Specific Language](/previous-versions/bb126564(v=vs.100))