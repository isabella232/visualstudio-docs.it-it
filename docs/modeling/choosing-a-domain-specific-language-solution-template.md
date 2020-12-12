---
title: Scelta di un modello di soluzione per un linguaggio specifico di dominio
description: Per informazioni su come creare una soluzione di linguaggio specifico di dominio, scegliere uno dei modelli di soluzione disponibili nella procedura guidata Domain-Specific Language Designer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e2e0c96c93e3583a7d2877a5f4f7bd70561b650b
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363536"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Scelta di un modello di soluzione per un linguaggio specifico di dominio
Per creare una soluzione per il linguaggio specifico di dominio, scegliere uno dei modelli di soluzione disponibili nella procedura guidata Domain-Specific Language Designer. Scegliendo il modello che è molto simile alla lingua che si desidera creare, è possibile ridurre al minimo le modifiche da apportare alla soluzione iniziale.

 Nella procedura guidata Domain-Specific Designer Language sono disponibili i modelli di soluzione seguenti.

|Modello|Funzionalità|Description|
|-|-|-|
|Diagrammi classi|-Forme raggruppamento<br />-Ereditarietà della classe<br />-Ereditarietà della relazione<br />-Ereditarietà della forma<br />-Proprietà relazione|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include entità e relazioni che dispongono di proprietà. Questo modello consente di creare un linguaggio specifico di dominio simile ai diagrammi classi UML. Le entità principali sono classi e interfacce, insieme alle relazioni di associazione, generalizzazione e implementazione. Una classe o interfaccia viene visualizzata come una casella contenente un elenco di attributi.|
|Diagrammi componente|-Porte|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include componenti, ovvero parti di un sistema software. Questo modello consente di creare un linguaggio specifico di dominio simile ai diagrammi componenti UML. Le entità principali sono componenti e porte, che vengono visualizzati come forme piccole all'esterno dei componenti.|
|Diagrammi di flusso attività|-Forme immagine e geometria<br />-   *Corsie*|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include flussi di lavoro, Stati o sequenze. Questo modello consente di creare un linguaggio specifico di dominio simile ai diagrammi di attività UML. L'entità principale è un'attività e la relazione principale è una transizione tra le attività. Il modello include diversi altri elementi, ad esempio stato di avvio, stato finale e una barra di sincronizzazione.|
|Linguaggio minimo|-Una classe e una forma<br />-Una relazione e un connettore|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio non è simile a quello degli altri modelli. Questo modello consente di creare un linguaggio specifico di dominio che dispone di due classi e una relazione, rappresentate nella casella **degli strumenti** come **Box** e **line**. Alla classe e alla relazione è associato un esempio di proprietà di stringa.|
|Finestra di progettazione WinForm minima|-Modello di dimensioni ridotte.<br />-Un Windows Form che Visualizza il modello.|Utilizzare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un Windows Form, anziché a una finestra di progettazione grafica.<br /><br /> Il modulo che funge da interfaccia utente per la lingua si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione del form.<br /><br /> Per ulteriori informazioni, vedere [Creating a Windows Forms-Based Domain-Specific Language](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Finestra di progettazione WPF minima|-Modello di dimensioni ridotte<br />-Interfaccia utente Windows Presentation Foundation che Visualizza il modello|Utilizzare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un'interfaccia utente WPF, anziché a una finestra di progettazione grafica.<br /><br /> La finestra di progettazione per l'interfaccia utente si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione dell'interfaccia utente.<br /><br /> Per ulteriori informazioni, vedere [creazione di un WPF-Based Domain-Specific linguaggio](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Libreria DSL|-Una libreria minima|Utilizzare questo modello se si desidera compilare una definizione DSL parziale che può essere importata in altre definizioni DSL.|

## <a name="see-also"></a>Vedi anche

- [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)
