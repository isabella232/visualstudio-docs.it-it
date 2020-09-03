---
title: 'Diagrammi di sequenza UML: informazioni di riferimento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
f1_keywords:
- vs.teamarch.sequencediagram.diagram
- vs.teamarch.UMLModelExplorer.sequencediagram
- vs.teamarch.sequencediagram.toolbox
helpviewer_keywords:
- diagrams - modeling, sequence
- sequence diagrams
- UML diagrams, sequence
- diagrams - modeling, UML sequence
- UML, sequence diagrams
ms.assetid: 366fc324-aeeb-4894-bd13-ec2e40754b8e
caps.latest.revision: 43
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f9b02bbad4fa897404f6c20e12b1705a3ae9ac8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72661708"
---
# <a name="uml-sequence-diagrams-reference"></a>Diagrammi di sequenza UML: riferimenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In Visual Studio un *diagramma di sequenza* Mostra un'interazione, che rappresenta la sequenza di messaggi tra istanze di classi, componenti, sottosistemi o attori. Data e ora scorrono verso la parte inferiore del diagramma e mostrano il flusso di controllo da un partecipante a un altro. Usare i diagrammi di sequenza per visualizzare istanze ed eventi, invece di classi e metodi. Nel diagramma possono essere visualizzate più istanze dello stesso tipo e più di un'occorrenza dello stesso messaggio.

 I diagrammi sequenza UML fanno parte di un modello UML ed esistono soltanto all'interno dei progetti di modellazione UML. Per creare un diagramma di sequenza UML, scegliere **nuovo diagramma livello o UML**dal menu **architettura** . Sono disponibili altre informazioni su come creare e creare [diagrammi di sequenza UML](../modeling/uml-sequence-diagrams-guidelines.md) o [diagrammi di modellazione UML](../modeling/edit-uml-models-and-diagrams.md) in generale.

 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Version support for architecture and modeling tools](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-sequence-diagrams"></a>Lettura dei diagrammi di sequenza
 La tabella seguente descrive gli elementi che è possibile visualizzare in un diagramma di sequenza. Scopri di più sulle proprietà di questi [elementi](../modeling/properties-of-elements-on-uml-sequence-diagrams.md).

 ![Parti di un diagramma di sequenza](../modeling/media/uml-sequence.png "UML_Sequence")

|**Con forme**|**elemento**|**Descrizione**|
|---------------|-----------------|---------------------|
|1|**Linea di vita**|Linea verticale che rappresenta la sequenza di eventi che si verificano in un partecipante durante un'interazione, mentre il tempo avanza lungo la linea. Questo partecipante può essere un'istanza di una classe, un componente o un attore.|
|2|**Actor**|Partecipante esterno al sistema in fase di sviluppo.<br /><br /> È possibile fare in modo che un simbolo attore venga visualizzato nella parte superiore di una linea di vita impostando la relativa proprietà **Actor** .|
|3|**Messaggio sincrono**|Il mittente attende una risposta a un messaggio sincrono prima di continuare. Il diagramma mostra sia la chiamata che il risultato della chiamata. I messaggi sincroni vengono usati per rappresentare chiamate di funzione comuni all'interno di un programma, oltre ad altri tipi di messaggio con un comportamento analogo.|
|4|**Messaggio asincrono**|Messaggio che non richiede una risposta prima che il mittente continui. Un messaggio asincrono mostra solo una chiamata dal mittente. Usarlo per rappresentare la comunicazione tra thread separati o la creazione di un nuovo thread.|
|5|**Occorrenza dell'esecuzione**|Rettangolo ombreggiato verticale che viene visualizzato sulla linea di vita di un partecipante e rappresenta il periodo durante il quale il partecipante esegue un'operazione.<br /><br /> L'esecuzione inizia nel punto in cui il partecipante riceve un messaggio. Se il messaggio di avvio è un messaggio sincrono, l'esecuzione terminerà con una freccia di «ritorno» al mittente.|
|6|**Messaggio di callback**|Messaggio restituito a un partecipante in attesa del risultato di una chiamata precedente. L'occorrenza dell'esecuzione risultante viene visualizzata sopra quella esistente.|
|7|**Auto-messaggio**|Messaggio da un partecipante a se stesso. L'occorrenza dell'esecuzione risultante viene visualizzata sopra quella di invio.|
|8|**Crea messaggio**|Messaggio che crea un partecipante. Se un partecipante riceve un messaggio di creazione, dovrebbe essere il primo a riceverlo.|
|9|**Messaggio trovato**|Messaggio asincrono da un partecipante sconosciuto o non specificato.|
|10|**Messaggio perso**|Messaggio asincrono a un partecipante sconosciuto o non specificato.|
|11|**Commento**|È possibile allegare un commento a qualsiasi punto di una linea di vita.|
|12|**Utilizzo interazione**|Include una sequenza di messaggi definiti in un altro diagramma.<br /><br /> Per creare un **uso interazione**, fare clic sullo strumento, quindi trascinare tra le linee di vita che si desidera includere.|
|13|**Frammento combinato**|Raccolta di frammenti. Ogni frammento può includere uno o più messaggi. Esistono diversi tipi di frammenti combinati. Per altre informazioni, vedere [descrivere il flusso di controllo con frammenti nei diagrammi di sequenza UML](../modeling/describe-control-flow-with-fragments-on-uml-sequence-diagrams.md).<br /><br /> Per creare un frammento, fare clic con il pulsante destro del mouse su un messaggio, scegliere **Racchiudi tra**e quindi fare clic su un tipo di frammento.|
|14|**Protezione del frammento**|Può essere usato per dichiarare una condizione rilevante per l'eventuale esecuzione della frammentazione.<br /><br /> Per impostare una protezione, selezionare un frammento, quindi selezionare la protezione e digitare un valore.|
|**X**|**Evento di eliminazione**|Rappresenta il punto in cui l'oggetto viene eliminato o non più accessibile. Viene visualizzato nella parte inferiore di ogni linea di vita.|
||**Interazione**|Raccolta di messaggi e linee di vita visualizzata nel diagramma di sequenza. Per visualizzare le proprietà di un'interazione, è necessario selezionarla in **Esplora modelli UML**.|
||**Diagramma sequenza**|Diagramma che visualizza un'interazione. Per visualizzare le proprietà, fare clic su una parte vuota del diagramma. **Nota:**  I nomi del diagramma di sequenza, l'interazione visualizzata e il file che contiene il diagramma possono essere tutti diversi.|

## <a name="see-also"></a>Vedere anche
 [Diagrammi di sequenza UML: linee guida](../modeling/uml-sequence-diagrams-guidelines.md) [modificare modelli UML e](../modeling/edit-uml-models-and-diagrams.md) diagrammi [caso d'uso UML: riferimento](../modeling/uml-use-case-diagrams-reference.md) [diagrammi classi UML: riferimento](../modeling/uml-class-diagrams-reference.md) [diagrammi componenti UML:](../modeling/uml-component-diagrams-reference.md) riferimento [diagrammi componenti UML](../modeling/uml-component-diagrams-reference.md) : informazioni di riferimento
