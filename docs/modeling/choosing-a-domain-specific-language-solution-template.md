---
title: Scelta di un modello di soluzione per un linguaggio specifico di dominio
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.openlocfilehash: ca1cb693977a5197bdf6adfe399ed269e0211a00
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/26/2019
ms.locfileid: "55071072"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Scelta di un modello di soluzione per un linguaggio specifico di dominio
Per creare una soluzione domain-specific language, scegliere uno dei modelli di soluzione che sono disponibili nella procedura guidata finestra di progettazione di linguaggio specifico di dominio. Scegliendo il modello che rispecchia maggiormente la lingua che si desidera creare, è possibile ridurre al minimo le modifiche da apportare alla soluzione di partenza.

 I seguenti modelli di soluzione sono disponibili nella procedura guidata finestra di progettazione di linguaggio specifico di dominio.

|Modello|Funzionalità|Descrizione|
|-|-|-|
|Diagrammi classi|-Forme raggruppamento<br />-Ereditarietà classe<br />-Ereditarietà relazione<br />: Ereditarietà delle forme<br />-Proprietà relazione|Usare questo modello di soluzione se il linguaggio specifico di dominio include entità e relazioni che dispongono di proprietà. Questo modello crea un linguaggio specifico di dominio che è simile a diagrammi classi UML. Le entità principali sono le classi e interfacce, insieme alle relazioni di associazione, generalizzazione e l'implementazione. Una classe o interfaccia viene visualizzata come una casella che contiene un elenco di attributi.|
|Diagrammi dei componenti|-Le porte|Usare questo modello di soluzione se il linguaggio specifico di dominio include i componenti, ovvero parti di un sistema software. Questo modello crea un linguaggio specifico di dominio che è simile a diagrammi dei componenti UML. Le entità principali sono i componenti e le porte, che vengono visualizzati come forme di piccole dimensioni all'esterno dei componenti.|
|Diagrammi di flusso attività|-Immagini e forme geometriche<br />-   *Corsie*|Usare questo modello di soluzione se il linguaggio specifico di dominio sono inclusi i flussi di lavoro, stati o le sequenze. Questo modello crea un linguaggio specifico di dominio che è simile a diagrammi di attività UML. L'entità principale è un'attività e la relazione principale è una transizione tra le attività. Il modello include diversi altri elementi, ad esempio stato di avvio, lo stato finale e una barra di sincronizzazione.|
|Linguaggio minimo|-Una classe e forma<br />-Una relazione e connettore|Usare questo modello di soluzione se il linguaggio specifico di dominio non corrisponde a altri modelli. Questo modello consente di creare un linguaggio specifico di dominio che dispone di due classi e una relazione, che sono rappresentati nel **casella degli strumenti** come **casella** e **riga**. La classe e la relazione di avere una proprietà di stringa di esempio.|
|Progettazione Windows Form minimo|-Un modello di piccole dimensioni.<br />-Un Windows Form che consente di visualizzare il modello.|Usare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un modulo di Windows, anziché una finestra di progettazione grafica.<br /><br /> Il form che funge da interfaccia utente per la lingua è nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione di form.<br /><br /> Per altre informazioni, vedere [creazione di un linguaggio specifico di dominio Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Finestra di progettazione WPF minimo|-Un modello di piccole dimensioni<br />-Un'interfaccia utente di Windows Presentation Foundation che consente di visualizzare il modello|Usare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un'interfaccia utente WPF, anziché una finestra di progettazione grafica.<br /><br /> La finestra di progettazione per l'interfaccia utente si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione dell'interfaccia utente.<br /><br /> Per altre informazioni, vedere [creazione di un linguaggio specifico di dominio WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Libreria DSL|-Una libreria minima|Usare questo modello se si desidera compilare una definizione DSL parziale che può essere importata in altre definizioni DSL.|

## <a name="see-also"></a>Vedere anche

- [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)
