---
title: Aggiungere stereotipi a elementi del modello UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 5bba638a595a01f17e4b7e4f8269a69cb6e466a1
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63430493"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Aggiungere stereotipi a elementi del modello UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile aggiungere uno stereotipo a un elemento del modello UML per aggiungervi annotazioni e fornirlo di proprietà specializzate. Per aggiungere uno stereotipo a un elemento del modello, lo stereotipo deve essere definito in un profilo ed è necessario collegare il profilo a un pacchetto o al modello contenente l'elemento del modello. Ogni stereotipo può essere aggiunto solo a determinati tipi di elemento del modello, ad esempio classi UML, casi di utilizzo o componenti.  
  
 Ad esempio, per definire una classe UML con lo stereotipo «specification», è necessario crearlo in un pacchetto o in un modello collegato al profilo standard L2.  
  
 Per impostazione predefinita, ogni modello è collegato ai profili standard UML L2 e L3.  
  
### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Per collegare un profilo a un modello o a un pacchetto  
  
1. Aprire **Esplora modelli UML**. Nel **architettura** dal menu **Windows**, quindi fare clic su **Esplora modelli UML**.  
  
2. Individuare un pacchetto o un modello contenente tutti gli elementi a cui applicare gli stereotipi nel profilo.  
  
3. Fare doppio clic il pacchetto o il modello e quindi fare clic su **proprietà**.  
  
4. Nel **proprietà** impostare nella finestra di **profili** proprietà per i profili che contengono gli stereotipi che si desidera utilizzare.  
  
     Gli stereotipi del profilo ora saranno disponibili in tutti gli elementi all'interno del modello o del pacchetto. Se il pacchetto contiene altri pacchetti, gli stereotipi saranno disponibili anche negli elementi negli altri pacchetti.  
  
### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Per aggiungere stereotipi a elementi del modello o a relazioni  
  
1. Fare doppio clic sull'elemento del modello o la relazione, in un diagramma o nel **Esplora modelli UML**, quindi fare clic su **proprietà**.  
  
    > [!NOTE]
    > Per aggiungere gli stessi stereotipi a più elementi, è possibile selezionare più elementi e quindi fare clic con il pulsante destro del mouse su uno di essi.  
  
2. Scegliere il **stereotipi** proprietà e selezionare gli stereotipi che si desidera applicare.  
  
     Gli stereotipi selezionati vengono visualizzati tra «frecce di espansione» nell'elemento del modello, per la maggior parte dei tipi di elemento e di relazione.  
  
    > [!NOTE]
    > Se non è possibile visualizzare il **stereotipi** proprietà, o se lo stereotipo desiderato non viene visualizzata, verificare che l'elemento del modello si trova all'interno di un pacchetto o un modello a cui è stato collegato il profilo appropriato.  
  
3. Alcuni stereotipi consentono di impostare i valori di altre proprietà per l'elemento del modello. Per visualizzare queste proprietà, espandere la **stereotipi** proprietà.  
  
### <a name="to-create-model-elements-within-a-package"></a>Per creare elementi del modello in un pacchetto  
  
1. Creare un pacchetto in un diagramma classi UML, o nel **Esplora modelli UML**.  
  
2. Aggiungere gli elementi del modello al pacchetto in uno dei modi seguenti:  
  
    - In un diagramma classi UML fare clic sullo strumento per un elemento e quindi fare clic all'interno del pacchetto nel diagramma.  
  
         \- oppure -  
  
    - In Esplora modelli UML, fare clic sul pacchetto, scegliere **Add**, quindi fare clic su un tipo di elemento.  
  
         \- oppure -  
  
    - In Esplora modelli UML trascinare un elemento esistente nel pacchetto.  
  
         \- oppure -  
  
    - Collegare un diagramma al pacchetto e quindi creare gli elementi nel diagramma.  
  
         A tale scopo, fare doppio clic su una parte vuota del diagramma e quindi fare clic su **proprietà**. Nel **delle proprietà** impostare nella finestra **pacchetto collegato** per il pacchetto desiderato.  
  
         Tutti i nuovi elementi creati nel diagramma verranno definiti in questo pacchetto.  
  
         È possibile farlo solo con alcuni tipi di diagramma.  
  
## <a name="see-also"></a>Vedere anche  
 [Definire un profilo per estendere UML](../modeling/define-a-profile-to-extend-uml.md)   
 [Personalizzare il modello con profili e stereotipi](../modeling/customize-your-model-with-profiles-and-stereotypes.md)   
 [Definire pacchetti e spazi dei nomi](../modeling/define-packages-and-namespaces.md)   
 [Colorare le classi UML per stereotipo](http://code.msdn.microsoft.com/UML-Color-Classes-by-07de2b70)
