---
title: Scelta di un modello di soluzione per un linguaggio specifico di dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b76b61bb0ff84d3e1f0948057b60f6f3fbb505ad
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75590566"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Scelta di un modello di soluzione per un linguaggio specifico di dominio
Per creare una soluzione per il linguaggio specifico di dominio, scegliere uno dei modelli di soluzione disponibili nella procedura guidata Finestra di progettazione Domain-Specific Language. Scegliendo il modello che è molto simile alla lingua che si desidera creare, è possibile ridurre al minimo le modifiche da apportare alla soluzione iniziale.

 I modelli di soluzione seguenti sono disponibili nella procedura guidata Finestra di progettazione Domain-Specific Language.

|Modello|Funzionalità|Descrizione|
|-|-|-|
|Diagrammi classi|-Forme raggruppamento<br />-Ereditarietà della classe<br />-Ereditarietà della relazione<br />-Ereditarietà della forma<br />-Proprietà relazione|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include entità e relazioni che dispongono di proprietà. Questo modello consente di creare un linguaggio specifico di dominio simile ai diagrammi classi UML. Le entità principali sono classi e interfacce, insieme alle relazioni di associazione, generalizzazione e implementazione. Una classe o interfaccia viene visualizzata come una casella contenente un elenco di attributi.|
|Diagrammi componente|-Porte|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include componenti, ovvero parti di un sistema software. Questo modello consente di creare un linguaggio specifico di dominio simile ai diagrammi componenti UML. Le entità principali sono componenti e porte, che vengono visualizzati come forme piccole all'esterno dei componenti.|
|Diagrammi di flusso attività|-Forme immagine e geometria<br />-   *Corsie*|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include flussi di lavoro, Stati o sequenze. Questo modello consente di creare un linguaggio specifico di dominio simile ai diagrammi di attività UML. L'entità principale è un'attività e la relazione principale è una transizione tra le attività. Il modello include diversi altri elementi, ad esempio stato di avvio, stato finale e una barra di sincronizzazione.|
|Linguaggio minimo|-Una classe e una forma<br />-Una relazione e un connettore|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio non è simile a quello degli altri modelli. Questo modello consente di creare un linguaggio specifico di dominio che dispone di due classi e una relazione, rappresentate nella casella **degli strumenti** come **Box** e **line**. Alla classe e alla relazione è associato un esempio di proprietà di stringa.|
|Finestra di progettazione WinForm minima|-Modello di dimensioni ridotte.<br />-Un Windows Form che Visualizza il modello.|Utilizzare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un Windows Form, anziché a una finestra di progettazione grafica.<br /><br /> Il modulo che funge da interfaccia utente per la lingua si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione del form.<br /><br /> Per ulteriori informazioni, vedere [creazione di un Domain-Specific Language basato su Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Finestra di progettazione WPF minima|-Modello di dimensioni ridotte<br />-Interfaccia utente Windows Presentation Foundation che Visualizza il modello|Utilizzare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un'interfaccia utente WPF, anziché a una finestra di progettazione grafica.<br /><br /> La finestra di progettazione per l'interfaccia utente si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione dell'interfaccia utente.<br /><br /> Per ulteriori informazioni, vedere [creazione di un Domain-Specific Language basato su WPF](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Libreria DSL|-Una libreria minima|Utilizzare questo modello se si desidera compilare una definizione DSL parziale che può essere importata in altre definizioni DSL.|

## <a name="see-also"></a>Vedere anche

- [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)
