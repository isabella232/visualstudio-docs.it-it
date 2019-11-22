---
title: 'Diagrammi classi UML: informazioni di riferimento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: reference
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: da4e0e3bab904b660f3d843e105b7d256a63a1b5
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74297223"
---
# <a name="uml-class-diagrams-reference"></a>Diagrammi classi UML: riferimento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Un diagramma classi UML descrive le strutture di oggetti e informazioni usate dall'applicazione, sia internamente che per comunicare con i relativi utenti. Descrive le informazioni senza riferimento ad alcuna implementazione specifica. Le relative classi e relazioni possono essere implementate in diversi modi, ad esempio tabelle di database, nodi XML o composizioni di oggetti software.

> [!NOTE]
> In questo argomento vengono illustrati i diagrammi classi UML. Esiste un altro tipo di diagramma classi, quello .NET, usato per visualizzare il codice programma. Per altre informazioni, vedere [Progettazione e visualizzazione di classi e tipi](https://go.microsoft.com/fwlink/?LinkId=142231).

 Per creare un diagramma classi UML, scegliere **Nuovo diagramma livello o UML** dal menu **Architettura**. Per altre informazioni su come creare diagrammi classi UML, vedere [Diagrammi classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md). Per altre informazioni su come creare e creare diagrammi di modellazione, vedere [modificare modelli e diagrammi UML](../modeling/edit-uml-models-and-diagrams.md).

 Per informazioni sulle versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="reading-class-diagrams"></a>Lettura dei diagrammi classi
 Nella tabella in questa sezione vengono descritti gli elementi che è possibile visualizzare in un diagramma classi UML. Per informazioni sulle proprietà di questi elementi, vedere gli argomenti seguenti:

- [Proprietà di tipi in diagrammi classi UML](../modeling/properties-of-types-on-uml-class-diagrams.md)

- [Proprietà di attributi in diagrammi classi UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md)

- [Proprietà di operazioni in diagrammi classi UML](../modeling/properties-of-operations-on-uml-class-diagrams.md)

- [Proprietà delle associazioni nei diagrammi classi UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)

  ![Tre classi che mostrano relazioni e proprietà](../modeling/media/uml-classovreading.png "UML_ClassOvReading")

| **Forma** |       **Elemento**        |                                                                                                                                                             **Descrizione**                                                                                                                                                              |
|-----------|--------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|     1     |        **Classe**         |                                                           Una definizione di oggetti che condividono caratteristiche strutturali o comportamentali specifiche. Per altre informazioni, vedere [proprietà dei tipi nei diagrammi classi UML](../modeling/properties-of-types-on-uml-class-diagrams.md).                                                            |
|     1     |        Classificatore        |                                                                                                             Il nome generale per una classe, interfaccia o enumerazione. Sono classificatori anche componenti, casi di utilizzo e attori.                                                                                                             |
|     2     | Controllo di compressione/espansione |                                                                                         Se non è possibile visualizzare i dettagli di un classificatore, fare clic sul'espansore nella parte superiore sinistra del classificatore. Potrebbe anche essere necessario fare clic su [+] in ogni segmento.                                                                                         |
|     3     |      **Attributo**       |   Un valore tipizzato associato a ogni istanza di un classificatore.<br /><br /> Per aggiungere un attributo, fare clic sulla sezione **Attributi** e quindi premere **INVIO**. Digitare la firma dell'attributo. Per altre informazioni, vedere [proprietà degli attributi nei diagrammi classi UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md).   |
|     4     |      **Operazione**       | Un metodo o funzione che può essere eseguito da istanze di un classificatore. Per aggiungere un'operazione, fare clic sulla sezione **Operazioni** e quindi premere **INVIO**. Digitare la firma dell'operazione. Per altre informazioni, vedere [proprietà delle operazioni sui diagrammi classi UML](../modeling/properties-of-operations-on-uml-class-diagrams.md). |
|     5     |     **Associazione**      |                                                                  Una relazione tra i membri di due classificatori. Per altre informazioni, vedere [proprietà delle associazioni nei diagrammi classi UML](../modeling/properties-of-associations-on-uml-class-diagrams.md).                                                                   |
|    5a     |     **Aggregazione**      |                                                                                                    Un'associazione che rappresenta una relazione proprietà condivisa. La proprietà **Aggregazione** del ruolo proprietario è impostata su **Condiviso**.                                                                                                     |
|    5b     |     **Composizione**      |                                                                                                      Un'associazione che rappresenta una relazione di parte intera. La proprietà **Aggregazione** del ruolo proprietario è impostata su **Composito**.                                                                                                      |
|     6     |   **Nome associazione**   |                                                                                                                                         Il nome di un'associazione. Il nome può essere lasciato vuoto.                                                                                                                                          |
|     7     |      **Nome ruolo**       |                       Il nome di un ruolo, ovvero un'estremità di un'associazione. Può essere usato per fare riferimento all'oggetto associato. Nella figura precedente per ogni ordine `O`, `O.ChosenMenu` è il menu associato.<br /><br /> Ogni ruolo dispone di proprietà personalizzate, elencate sotto le proprietà dell'associazione.                       |
|     8     |     **Molteplicità**     |                                         Indica il numero di oggetti a questa estremità che può essere collegato a ogni oggetto all'altra estremità. Nell'esempio ogni ordine deve essere collegato a un solo menu.<br /><br /> **\\** \* significa che non esiste alcun limite massimo per il numero di collegamenti che è possibile effettuare.                                         |
|     9     |    **Generalizzazione**    |  Il classificatore *specifico* eredita parte della definizione dal classificatore *generale*. Il classificatore generale si trova all'estremità della freccia del connettore. Attributi, associazioni e operazioni vengono ereditati dal classificatore specifico.<br /><br /> Usare lo strumento **Ereditarietà** per creare una generalizzazione tra due classificatori.   |

 ![Pacchetto contenente l'interfaccia e l'enumerazione](../modeling/media/uml-classovpackage.png "UML_ClassOvPackage")

|Forma|Elemento|description|
|-----------|-------------|-----------------|
|10|**Interface**|Una definizione di parte del comportamento visibile esternamente di un oggetto. Per altre informazioni, vedere [proprietà dei tipi nei diagrammi classi UML](../modeling/properties-of-types-on-uml-class-diagrams.md).|
|11|**Enumerazione**|Un classificatore costituito da un set di valori letterali.|
|12|**Pacchetto**|Un gruppo di classificatori, associazioni, azioni, linee di vita, componenti e pacchetti. Un diagramma classi logico mostra che i classificatori e i pacchetti del membro sono contenuti all'interno del pacchetto.<br /><br /> I nomi hanno come ambito i pacchetti in modo che **Class1** all'interno di **package1** sia diverso da **Class1** all'esterno del pacchetto. Il nome del pacchetto viene visualizzato come parte della proprietà **Nome completo** del contenuto.<br /><br /> È possibile impostare la proprietà **Pacchetto collegato** di un diagramma UML per fare riferimento a un pacchetto. Tutti gli elementi creati nel diagramma diventeranno quindi parte del pacchetto e verranno visualizzati sotto il pacchetto **Esplora modelli UML**.|
|13|**Importaa**|Una relazione tra pacchetti, con cui viene indicato che un pacchetto include tutte le definizioni di un altro pacchetto.|
|14|**Dipendenza**|La definizione o l'implementazione del classificatore dipendente potrebbe cambiare se viene modificato il classificatore all'estremità della freccia.|

 ![Realizzazione mostrata con connettore e Lollipop](../modeling/media/uml-classovrealize.png "UML_ClassOvRealize")

|Forma|**Elemento**|description|
|-----------|-----------------|-----------------|
|15|**Realizzazione**|La classe implementa le operazioni e gli attributi definiti dall'interfaccia.<br /><br /> Usare lo strumento **Ereditarietà** per creare una realizzazione tra una classe e un'interfaccia.|
|16|**Realizzazione**|Una presentazione alternativa della stessa relazione. L'etichetta sul simbolo identifica l'interfaccia.<br /><br /> Per creare questa presentazione, selezionare una relazione realizzazione esistente. Fare clic sul tag azioni accanto all'associazione. Fare clic sul tag azioni e quindi su **Mostra come simbolo**.|

## <a name="see-also"></a>Vedere anche
 [Modificare modelli e](../modeling/edit-uml-models-and-diagrams.md) DIAGRAMmi UML diagrammi [classi UML: linee guida](../modeling/uml-class-diagrams-guidelines.md) [proprietà dei tipi in diagrammi classi UML](../modeling/properties-of-types-on-uml-class-diagrams.md) [proprietà di attributi in diagrammi classi UML](../modeling/properties-of-attributes-on-uml-class-diagrams.md) [proprietà di operazioni in diagrammi classi UML](../modeling/properties-of-operations-on-uml-class-diagrams.md) [proprietà di associazioni nei diagrammi classi UML](../modeling/properties-of-associations-on-uml-class-diagrams.md)
