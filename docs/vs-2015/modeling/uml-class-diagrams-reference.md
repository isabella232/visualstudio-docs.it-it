---
title: 'Diagrammi classi UML: Riferimento | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.teamarch.common.generalization.properties
- vs.teamarch.logicalclassdiagram.toolbox
- vs.teamarch.UMLModelExplorer.association
- vs.teamarch.common.unspecifiedtype.properties
- vs.teamarch.logicalclassdiagram.diagram
- vs.teamarch.UMLModelExplorer.logicalclassdiagram
- vs.teamarch.UMLModelExplorer.generalization
- vs.teamarch.common.unspecifiedtype
helpviewer_keywords:
- UML diagrams, class
- diagrams - modeling, class
- UML, class diagrams
- class diagrams - UML
- diagrams - modeling, UML class
ms.assetid: b7c88be0-0d86-4d65-af74-f37e8812d20f
caps.latest.revision: 43
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 239b5427c4e19b15e44d683def0e2d6c82dccdfe
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529092"
---
# <a name="uml-class-diagrams-reference"></a>Diagrammi classi UML: riferimento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [diagrammi classi UML: riferimento](https://docs.microsoft.com/visualstudio/modeling/uml-class-diagrams-reference).  
  
Un diagramma classi UML descrive le strutture di oggetti e informazioni usate dall'applicazione, sia internamente che per comunicare con i relativi utenti. Descrive le informazioni senza riferimento ad alcuna implementazione specifica. Le relative classi e relazioni possono essere implementate in diversi modi, ad esempio tabelle di database, nodi XML o composizioni di oggetti software.  
  
> [!NOTE]
>  In questo argomento vengono illustrati i diagrammi classi UML. Esiste un altro tipo di diagramma classi, quello .NET, usato per visualizzare il codice programma. Per altre informazioni, vedere [progettazione e visualizzazione di classi e tipi](http://go.microsoft.com/fwlink/?LinkId=142231).  
  
 Per creare un diagramma classi UML, nelle **Architecture** menu, scegliere **nuovo diagramma livello o UML**. Per altre informazioni su come creare diagrammi classi UML, vedere [diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md). Per altre informazioni su come creare e disegnare diagrammi di modellazione, vedere [modelli e diagrammi UML modifica](../modeling/edit-uml-models-and-diagrams.md).  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="reading-class-diagrams"></a>Lettura dei diagrammi classi  
 Nella tabella in questa sezione vengono descritti gli elementi che è possibile visualizzare in un diagramma classi UML. Per informazioni sulle proprietà di questi elementi, vedere gli argomenti seguenti:  
  
-   [Proprietà di tipi in diagrammi classi UML](../modeling/properties-of-types-on-uml-class-diagrams.md)  
  
-   [Proprietà di attributi in diagrammi classi UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)  
  
-   [Proprietà di operazioni in diagrammi classi UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)  
  
-   [Proprietà delle associazioni nei diagrammi classi UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)  
  
 ![Tre classi che mostrano relazioni e le proprietà](../modeling/media/uml-classovreading.png "UML_ClassOvReading")  
  
|**Forma**|**Elemento**|**Descrizione**|  
|---------------|-----------------|---------------------|  
|1|**Classe**|Una definizione di oggetti che condividono caratteristiche strutturali o comportamentali specifiche. Per altre informazioni, vedere [diagrammi di classi di proprietà di tipi in UML](../modeling/properties-of-types-on-uml-class-diagrams.md).|  
|1|Classificatore|Il nome generale per una classe, interfaccia o enumerazione. Sono classificatori anche componenti, casi di utilizzo e attori.|  
|2|Controllo di compressione/espansione|Se non è possibile visualizzare i dettagli di un classificatore, fare clic sul'espansore nella parte superiore sinistra del classificatore. Potrebbe anche essere necessario fare clic su [+] in ogni segmento.|  
|3|**Attributo**|Un valore tipizzato associato a ogni istanza di un classificatore.<br /><br /> Per aggiungere un attributo, scegliere il **attributi** della sezione e quindi premere **invio**. Digitare la firma dell'attributo. Per altre informazioni, vedere [diagrammi di classi di proprietà di attributi su UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md).|  
|4|**Operazione**|Un metodo o funzione che può essere eseguito da istanze di un classificatore. Per aggiungere un'operazione, scegliere il **Operations** della sezione e quindi premere **invio**. Digitare la firma dell'operazione. Per altre informazioni, vedere [proprietà di operazioni su UML diagrammi classi](../modeling/properties-of-operations-on-uml-class-diagrams.md).|  
|5|**Associazione**|Una relazione tra i membri di due classificatori. Per altre informazioni, vedere [proprietà delle associazioni nei UML diagrammi classi](../modeling/properties-of-associations-on-uml-class-diagrams.md).|  
|5a|**Aggregazione**|Un'associazione che rappresenta una relazione proprietà condivisa. Il **aggregazione** del ruolo proprietario è impostata su **condiviso**.|  
|5b|**Composizione**|Un'associazione che rappresenta una relazione di parte intera. Il **aggregazione** del ruolo proprietario è impostata su **composito**.|  
|6|**Nome dell'associazione**|Il nome di un'associazione. Il nome può essere lasciato vuoto.|  
|7|**Nome del ruolo**|Il nome di un ruolo, ovvero un'estremità di un'associazione. Può essere usato per fare riferimento all'oggetto associato. Nella figura precedente per ogni ordine `O`, `O.ChosenMenu` è il menu associato.<br /><br /> Ogni ruolo dispone di proprietà personalizzate, elencate sotto le proprietà dell'associazione.|  
|8|**Molteplicità**|Indica il numero di oggetti a questa estremità che può essere collegato a ogni oggetto all'altra estremità. Nell'esempio ogni ordine deve essere collegato a un solo menu.<br /><br /> **\*** significa che non vi è alcun limite al numero di collegamenti che possono essere apportati.|  
|9|**Generalizzazione**|Il *specifici* classificatore eredita parte della definizione dalle *generali* classificatore. Il classificatore generale si trova all'estremità della freccia del connettore. Attributi, associazioni e operazioni vengono ereditati dal classificatore specifico.<br /><br /> Usare la **ereditarietà** lo strumento per creare una generalizzazione tra due classificatori.|  
  
 ![Pacchetto contenente l'interfaccia e l'enumerazione](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")  
  
|Forma|Elemento|Descrizione|  
|-----------|-------------|-----------------|  
|10|**Interface**|Una definizione di parte del comportamento visibile esternamente di un oggetto. Per altre informazioni, vedere [diagrammi di classi di proprietà di tipi in UML](../modeling/properties-of-types-on-uml-class-diagrams.md).|  
|11|**Enumerazione**|Un classificatore costituito da un set di valori letterali.|  
|12|**Pacchetto**|Un gruppo di classificatori, associazioni, azioni, linee di vita, componenti e pacchetti. Un diagramma classi logico mostra che i classificatori e i pacchetti del membro sono contenuti all'interno del pacchetto.<br /><br /> Ambito dei nomi all'interno di pacchetti in modo che **Class1** entro **Package1** è diverso dal **Class1** all'esterno del pacchetto. Il nome del pacchetto viene visualizzato come parte del **nome qualificato** le proprietà del relativo contenuto.<br /><br /> È possibile impostare il **pacchetto collegato** proprietà di un diagramma UML per fare riferimento a un pacchetto. Tutti gli elementi creati nel diagramma diventeranno quindi parte del pacchetto Verranno visualizzati sotto il pacchetto **Esplora modelli UML**.|  
|13|**Import**|Una relazione tra pacchetti, con cui viene indicato che un pacchetto include tutte le definizioni di un altro pacchetto.|  
|14|**dipendenza**|La definizione o l'implementazione del classificatore dipendente potrebbe cambiare se viene modificato il classificatore all'estremità della freccia.|  
  
 ![Realizzazione con connettore e simbolo](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")  
  
|Forma|**Elemento**|Descrizione|  
|-----------|-----------------|-----------------|  
|15|**Realizzazione**|La classe implementa le operazioni e gli attributi definiti dall'interfaccia.<br /><br /> Usare la **ereditarietà** lo strumento per creare una realizzazione tra una classe e un'interfaccia.|  
|16|**Realizzazione**|Una presentazione alternativa della stessa relazione. L'etichetta sul simbolo identifica l'interfaccia.<br /><br /> Per creare questa presentazione, selezionare una relazione realizzazione esistente. Fare clic sul tag azioni accanto all'associazione. Fare clic sul tag azioni e quindi fare clic su **Mostra come simbolo**.|  
  
## <a name="see-also"></a>Vedere anche  
 [Modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md)   
 [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md)   
 [Proprietà di tipi in diagrammi classi UML](../modeling/properties-of-types-on-uml-class-diagrams.md)   
 [Proprietà di attributi in diagrammi classi UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)   
 [Proprietà di operazioni in diagrammi classi UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)   
 [Proprietà delle associazioni nei diagrammi classi UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)



