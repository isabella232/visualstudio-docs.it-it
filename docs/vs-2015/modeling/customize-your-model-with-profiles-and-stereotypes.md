---
title: Personalizzare il modello con profili e stereotipi | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: alexhomer1
ms.author: gewarren
manager: douge
ms.openlocfilehash: 2dd494b475b5d9068597857a2f4df12e5fed8e2f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47526044"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Personalizzare il modello con profili e stereotipi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [personalizzare il modello con profili e stereotipi](https://docs.microsoft.com/visualstudio/modeling/customize-your-model-with-profiles-and-stereotypes).  
  
In Visual Studio è possibile adattare gli elementi di modello UML standard, come classi e componenti, in modo da personalizzarli per scopi specifici. È possibile applicare una *stereotipo* a un elemento del modello che è possibile modificare l'elenco di proprietà dell'elemento. Gli stereotipi vengono definiti all'interno di raccolte chiamate *profili*.  
  
 Per individuare le versioni di Visual Studio che supportano questa funzionalità, vedere [Supporto delle versioni per gli strumenti di architettura e modellazione](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
 Per usare uno stereotipo, è necessario collegare un pacchetto a un profilo. In questo modo, è possibile applicare gli stereotipi definiti nel profilo agli elementi nel pacchetto. Alcuni profili vengono installati con Visual Studio. È anche possibile definire profili personalizzati.  
  
 Gli stereotipi possono essere impostati nell'elenco Proprietà di un elemento. Per i tipi di forma principali in un diagramma, gli stereotipi applicati vengono visualizzati anche nella forma, come mostrato nell'esempio.  
  
 ![Una classe UML con uno stereotipo. ](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")  
  
> [!NOTE]
>  Se si usa un profilo per creare un modello e quindi si condivide il modello con altri utenti, questi non potranno visualizzare gli stereotipi a meno che non abbiano installato lo stesso profilo nel proprio computer.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Aggiungere stereotipi a elementi del modello UML](../modeling/add-stereotypes-to-uml-model-elements.md)|Inserimento di un elemento di modello in un pacchetto, collegamento del pacchetto a un profilo e applicazione di uno stereotipo all'elemento.|  
|[Stereotipi standard per modelli UML](../modeling/standard-stereotypes-for-uml-models.md)|I profili standard UML L2 e L3 vengono installati con Visual Studio e a essi è collegato ogni modello per impostazione predefinita. Questi profili forniscono stereotipi che è possibile usare per annotare i modelli.<br /><br /> Ad esempio, è possibile applicare lo stereotipo «specificazione» a una classe per indicare che è destinata solo a definire il comportamento visibile esternamente delle sue istanze.|  
|[Definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md)|È possibile definire stereotipi e strumenti personalizzati, adattati all'area della propria applicazione.<br /><br /> Ad esempio, se si sviluppa software bancario, si potrebbe definire uno stereotipo «conto» da applicare alle classi. Sarebbe quindi possibile usare diagrammi classi per definire tipi diversi di conto e le rispettive relazioni.|  
|[Installare un profilo UML](../modeling/install-a-uml-profile.md)|Se si è ricevuto un profilo UML da un altro utente, è possibile installarlo nel proprio computer.|  
|[Definire un elemento della casella degli strumenti di modellazione personalizzata](../modeling/define-a-custom-modeling-toolbox-item.md)|Un elemento personalizzato della Casella degli strumenti evita la necessità di ripetere l'impostazione di uno stereotipo in nuovi elementi.|  
|[Colorare le classi UML per stereotipo](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)|Questo codice di esempio estende i diagrammi UML, impostando automaticamente il colore di una forma UML in base allo stereotipo dell'elemento.|


