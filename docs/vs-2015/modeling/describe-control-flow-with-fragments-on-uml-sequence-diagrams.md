---
title: Descrivere il flusso di controllo con frammenti in diagrammi di sequenza UML | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.sequencediagram.combinedfragment.interactionoperand
- vs.teamarch.sequencediagram.combinedfragment
helpviewer_keywords:
- UML sequence diagrams, control flow
- UML sequence diagrams, fragments
- sequence diagrams, fragments
- sequence diagrams, control flow
ms.assetid: efcc0949-be7e-4cf4-99ef-47c36b3803ae
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 4ab4c65e554e9eef75a1761719ce19f3312e07ce
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51727655"
---
# <a name="describe-control-flow-with-fragments-on-uml-sequence-diagrams"></a>Descrivere il flusso di controllo con frammenti in diagrammi di sequenza UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In un diagramma di sequenza UML i *frammenti combinati* permettono di mostrare cicli, rami e altre alternative.  
  
 Un frammento combinato è costituito da uno o più *operandi interazione*, ognuno dei quali racchiude uno o più messaggi, utilizzi interazione o frammenti combinati.  
  
> [!NOTE]
>  Questo argomento descrive i frammenti nei diagrammi di sequenza. Per altre informazioni su come leggere i diagrammi di sequenza UML, vedere [diagrammi di sequenza UML: riferimento](../modeling/uml-sequence-diagrams-reference.md). Per altre informazioni su come creare diagrammi di sequenza UML, vedere [UML Sequence Diagrams: Guidelines](../modeling/uml-sequence-diagrams-guidelines.md).  
  
 ![Frammento con due operandi interazione combinato](../modeling/media/uml-seqfragments.png "UML_SeqFragments")  
  
 Gli elementi mostrati nella figura sono i seguenti.  
  
1.  Un frammento combinato. Esistono diversi tipi di frammenti combinati. Questo esempio è un frammento combinato Alt, che è possibile usare per indicare che possono verificarsi sequenze alternative di messaggi.  
  
2.  Operandi interazione. Ogni frammento combinato contiene almeno un operando interazione, che può contenere messaggi, utilizzi interazione e frammenti combinati di dimensioni minori. In questo esempio il frammento combinato Alt include due operazioni di interazione che mostrano sequenze alternative di messaggi.  
  
3.  È possibile selezionare ogni operando interazione separatamente facendo clic al suo interno. In questo esempio è selezionato l'operando interazione superiore, in modo da poter visualizzare il suo limite. In genere, è visibile solo la linea di separazione tra gli operandi interazione.  
  
    > [!NOTE]
    >  Per selezionare l'operando interazione superiore, è necessario fare clic non troppo vicino alla parte superiore del frammento combinato.  
  
4.  Clausole guard. È possibile assegnare una clausola guard a ogni operando interazione. La clausola guard descrive la condizione in cui verranno eseguiti i messaggi all'interno dell'operando interazione.  
  
## <a name="creating-combined-fragments"></a>Creazione di frammenti combinati  
 Per un elenco dei tipi di frammento che è possibile creare, vedere [Tipi di frammento combinato](#KindsOfFragment).  
  
#### <a name="to-create-a-combined-fragment"></a>Per creare un frammento combinato  
  
1. Selezionare un messaggio, o una sequenza di messaggi, che iniziano tutti nella stessa linea di vita o occorrenza esecuzione.  
  
   > [!NOTE]
   >  Se si selezionano più messaggi, questi devono formare una sequenza ininterrotta.  
  
2. Fare clic con il pulsante destro del mouse su uno dei messaggi, scegliere **Racchiudi tra**e quindi fare clic sul tipo di frammento combinato desiderato, ad esempio **Alterna frammento combinato**.  
  
    Viene visualizzato un nuovo frammento combinato. L'intestazione indica il tipo di frammento combinato selezionato, ad esempio **Alt**.  
  
    All'interno del frammento combinato è presente un frammento che contiene i messaggi selezionati.  
  
   È possibile aggiungere più operandi interazione ad alcuni tipi di frammento combinato.  
  
   Dopo avere riorganizzato la disposizione dei messaggi all'interno di un frammento combinato, scegliere **Ridisponi layout** dal menu di scelta rapida per ridimensionare il frame del frammento combinato.  
  
#### <a name="to-add-a-new-interaction-operand-to-a-combined-fragment"></a>Per aggiungere un nuovo operando interazione a un frammento combinato  
  
1. Fare clic con il pulsante destro del mouse in uno spazio vuoto nell'operando interazione (2), all'esterno di qualsiasi frammento contenuto e sotto l'intestazione del frammento combinato.  
  
2. Scegliere **Aggiungi**.  
  
3. Fare clic su **Operando interazione prima**o **Operando interazione dopo**.  
  
4. È possibile aggiungere messaggi all'interno del nuovo operando interazione usando gli strumenti dei messaggi oppure copiando e incollando messaggi esistenti.  
  
   È possibile impostare la proprietà **Guard** di un operando interazione per descrivere le condizioni in cui vengono eseguiti i messaggi al suo interno. Ad esempio, in un frammento combinato **Loop** è possibile usare la clausola guard per specificare la condizione durante la quale il ciclo continua. In un frammento combinato **Alt** è possibile specificare una condizione separata per ogni operando interazione.  
  
#### <a name="to-set-the-guard-of-an-interaction-operand"></a>Per impostare la clausola guard di un operando interazione  
  
1. Fare clic in uno spazio vuoto nell'operando interazione (2), all'esterno di qualsiasi frammento contenuto.  
  
    Viene visualizzato un bordo di selezione attorno all'operando interazione e attorno alla condizione guard.  
  
    L'intestazione nella finestra **Proprietà** indica **Operando interazione**.  
  
2. Digitare la condizione guard.  
  
    La condizione verrà visualizzata accanto alla parte superiore del frammento (4).  
  
   È possibile impostare le proprietà di alcuni tipi di frammenti combinati.  
  
#### <a name="to-set-or-view-the-properties-of-a-combined-fragment"></a>Per impostare o visualizzare le proprietà di un frammento combinato  
  
-   Fare clic con il pulsante destro del mouse sul titolo del frammento combinato e quindi scegliere **Proprietà**.  
  
    > [!NOTE]
    >  Tipi diversi di frammento combinato hanno proprietà diverse.  
  
##  <a name="KindsOfFragment"></a> Tipi di frammento combinato  
  
### <a name="fragments-describing-control-flow"></a>Frammenti che descrivono il flusso di controllo  
 Un diagramma di sequenza semplice mostra solo una sequenza tipica. È possibile usare i tipi di frammenti combinati indicati di seguito per descrivere le variazioni che possono verificarsi in occasioni diverse.  
  
|Tipo di frammento|Descrizione|  
|-------------------|-----------------|  
|**consenso esplicito**|Facoltativo. Racchiude una sequenza che può verificarsi o non verificarsi. È possibile specificare nella clausola guard la condizione in cui si verifica.|  
|**ALT**|Contiene un elenco di frammenti che includono sequenze alternative di messaggi. In ogni occasione si verifica una sola sequenza.<br /><br /> È possibile inserire una clausola guard in ogni frammento per indicare la condizione in cui può essere eseguito. Una clausola guard **else** indica un frammento che deve essere eseguito se nessun'altra clausola guard è true. Se tutte le clausole guard sono false e non è presente alcuna clausola guard **else**, non viene eseguito alcun frammento.|  
|**Loop**|Il frammento viene ripetuto un certo numero di volte. È possibile indicare nella clausola guard la condizione in cui si deve ripetere.<br /><br /> I frammenti combinati Loop includono le proprietà **Min** e **Max**, che indicano i numeri minimo e massimo di volte in cui il frammento può essere ripetuto. Il valore predefinito non prevede alcuna restrizione.|  
|**Break**|Se viene eseguito questo frammento, il resto della sequenza viene abbandonato. È possibile usare una clausola guard per indicare la condizione in cui si verificherà l'interruzione.|  
|**Par**|Parallelo. Gli eventi nei frammenti possono essere interfogliati.|  
|**Critico**|Usato in un frammento Par o Seq. Indica che i messaggi in questo frammento non devono essere interfogliati con altri messaggi.|  
|**Seq**|Sono presenti due o più frammenti dell'operando. I messaggi che interessano la stessa linea di vita devono verificarsi nell'ordine dei frammenti. Nei casi in cui non interessano le stesse linee di vita, i messaggi da frammenti diversi possono essere interfogliati in parallelo.|  
|**Strict**|Sono presenti due o più frammenti dell'operando. I frammenti devono verificarsi nell'ordine specificato.|  
  
### <a name="fragments-about-how-to-interpret-the-sequence"></a>Frammenti su come interpretare la sequenza  
 Per impostazione predefinita, il diagramma di sequenza indica una serie di messaggi che possono verificarsi. Nel sistema in esecuzione possono verificarsi altri messaggi che non si è scelto di mostrare nel diagramma.  
  
 I tipi di frammento seguenti possono essere usati per modificare questa interpretazione.  
  
|Tipo di frammento|Descrizione|  
|-------------------|-----------------|  
|**Prendere in considerazione**|Specifica un elenco dei messaggi descritti da questo frammento. Nel sistema in esecuzione possono verificarsi altri messaggi, ma questi non sono significativi ai fini della descrizione.<br /><br /> Digitare l'elenco nella proprietà **Messages** .|  
|**Ignora**|Specifica un elenco dei messaggi non descritti da questo frammento. I messaggi possono verificarsi nel sistema in esecuzione, ma non sono significativi ai fini della descrizione.<br /><br /> Digitare l'elenco nella proprietà **Messages** .|  
|**Assert**|Il frammento dell'operando specifica le uniche sequenze valide. Usato in genere in un frammento Consider o Ignore.|  
|**neg**|La sequenza mostrata in questo frammento non deve verificarsi. Usato in genere in un frammento Consider o Ignore.|  
  
## <a name="see-also"></a>Vedere anche  
 [Diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md)   
 [Diagrammi di sequenza UML: riferimento](../modeling/uml-sequence-diagrams-reference.md)   
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)



