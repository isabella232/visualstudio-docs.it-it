---
title: Scelta di un modello di soluzione Domain-Specific Language | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 26
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6522e3a1ad10f221f0ed7fc1761559ee9bc3f9b9
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668344"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Scelta di un modello di soluzione per un linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per creare una soluzione per il linguaggio specifico di dominio, scegliere uno dei modelli di soluzione disponibili nella procedura guidata Finestra di progettazione Domain-Specific Language. Scegliendo il modello che è molto simile alla lingua che si desidera creare, è possibile ridurre al minimo le modifiche da apportare alla soluzione iniziale.

 I modelli di soluzione seguenti sono disponibili nella procedura guidata Finestra di progettazione Domain-Specific Language.

> [!NOTE]
> Lo scopo dei modelli è fornire un DSL iniziale. I modelli denominati diagrammi classi e componenti non sono diagrammi UML completi. Se si desidera creare un modello UML, considerare gli strumenti di modellazione UML, che forniscono un set di diagrammi integrati intorno a un singolo modello. Sono estensibili e possono essere integrati con il linguaggio DSL con ModelBus. Per altre informazioni, vedere [creare modelli per l'app](../modeling/create-models-for-your-app.md).

|Modello|Funzionalità|Descrizione|
|--------------|--------------|-----------------|
|Diagrammi classi|-Forme raggruppamento<br />-Ereditarietà della classe<br />-Ereditarietà della relazione<br />-Ereditarietà della forma<br />-Proprietà relazione|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include entità e relazioni che dispongono di proprietà. Questo modello consente di creare un linguaggio specifico di dominio simile ai diagrammi classi UML. Le entità principali sono classi e interfacce, insieme alle relazioni di associazione, generalizzazione e implementazione. Una classe o interfaccia viene visualizzata come una casella contenente un elenco di attributi.|
|Diagrammi componente|-Porte|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include componenti, ovvero parti di un sistema software. Questo modello consente di creare un linguaggio specifico di dominio simile ai diagrammi componenti UML. Le entità principali sono componenti e porte, che vengono visualizzati come forme piccole all'esterno dei componenti.|
|Diagrammi di flusso attività|-Forme immagine e geometria<br />*corsie* -   |Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include flussi di lavoro, Stati o sequenze. Questo modello consente di creare un linguaggio specifico di dominio simile ai diagrammi di attività UML. L'entità principale è un'attività e la relazione principale è una transizione tra le attività. Il modello include diversi altri elementi, ad esempio stato di avvio, stato finale e una barra di sincronizzazione.|
|Linguaggio minimo|-Una classe e una forma<br />-Una relazione e un connettore|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio non è simile a quello degli altri modelli. Questo modello consente di creare un linguaggio specifico di dominio che dispone di due classi e una relazione, rappresentate nella casella **degli strumenti** come **Box** e **line**. Alla classe e alla relazione è associato un esempio di proprietà di stringa.|
|Finestra di progettazione WinForm minima|-Modello di dimensioni ridotte.<br />-Un Windows Form che Visualizza il modello.|Utilizzare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un Windows Form, anziché a una finestra di progettazione grafica.<br /><br /> Il modulo che funge da interfaccia utente per la lingua si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione del form.<br /><br /> Per ulteriori informazioni, vedere [creazione di un Domain-Specific Language basato su Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Finestra di progettazione WPF minima|-Modello di dimensioni ridotte<br />-Interfaccia utente Windows Presentation Foundation che Visualizza il modello|Utilizzare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un'interfaccia utente WPF, anziché a una finestra di progettazione grafica.<br /><br /> La finestra di progettazione per l'interfaccia utente si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione dell'interfaccia utente.<br /><br /> Per ulteriori informazioni, vedere [creazione di un Domain-Specific Language basato su WPF](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Libreria DSL|-Una libreria minima|Utilizzare questo modello se si desidera compilare una definizione DSL parziale che può essere importata in altre definizioni DSL.|

## <a name="see-also"></a>Vedere anche
 [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)
