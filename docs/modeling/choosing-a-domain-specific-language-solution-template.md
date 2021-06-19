---
title: Scelta di un modello di soluzione per un linguaggio specifico di dominio
description: Informazioni su come creare una soluzione di linguaggio specifico di dominio scegliendo uno dei modelli di soluzione disponibili nella creazione guidata Domain-Specific Language Designer.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1c638c5a45427fd474f085ff58c9d38682ee054
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385435"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Scelta di un modello di soluzione per un linguaggio specifico di dominio
Per creare una soluzione di linguaggio specifico di dominio, scegliere uno dei modelli di soluzione disponibili nella Domain-Specific Language Designer. Scegliendo il modello più simile al linguaggio che si vuole creare, è possibile ridurre al minimo le modifiche che è necessario apportare alla soluzione iniziale.

 I modelli di soluzione seguenti sono disponibili nella creazione guidata Domain-Specific Language Designer.

|Modello|Funzionalità|Descrizione|
|-|-|-|
|Diagrammi classi|- Forme raggruppamento<br />- Ereditarietà delle classi<br />- Ereditarietà delle relazioni<br />- Ereditarietà delle forme<br />- Proprietà della relazione|Usare questo modello di soluzione se il linguaggio specifico di dominio include entità e relazioni con proprietà. Questo modello crea un linguaggio specifico di dominio simile ai diagrammi classi UML. Le entità principali sono classi e interfacce, insieme alle relazioni di associazione, generalizzazione e implementazione. Una classe o un'interfaccia viene visualizzata come casella contenente un elenco di attributi.|
|Diagrammi dei componenti|- Porte|Usare questo modello di soluzione se il linguaggio specifico di dominio include componenti, ad esempio parti di un sistema software. Questo modello crea un linguaggio specifico di dominio simile ai diagrammi dei componenti UML. Le entità principali sono componenti e porte, che vengono visualizzate come piccole forme all'esterno dei componenti.|
|Diagrammi di flusso delle attività|- Forme immagine e geometria<br />-   *Corsie*|Usare questo modello di soluzione se il linguaggio specifico di dominio include flussi di lavoro, stati o sequenze. Questo modello crea un linguaggio specifico di dominio simile ai diagrammi di attività UML. L'entità principale è un'attività e la relazione principale è una transizione tra attività. Il modello include diversi altri elementi, ad esempio lo stato iniziale, lo stato finale e una barra di sincronizzazione.|
|Linguaggio minimo|- Una classe e una forma<br />- Una relazione e un connettore|Usare questo modello di soluzione se il linguaggio specifico di dominio non è simile agli altri modelli. Questo modello crea un linguaggio specifico di dominio con due classi e una relazione, rappresentate nella casella degli **strumenti** **come Box** e **Line.** La classe e la relazione hanno ognuna una proprietà stringa di esempio.|
|Finestra di progettazione WinForm minima|- Un modello di piccole dimensioni.<br />- Windows Form che visualizza il modello.|Usare questo modello se si vuole compilare un'applicazione in cui un DSL è associato a un Windows Form, anziché a una finestra di progettazione grafica.<br /><br /> Il modulo che funge da interfaccia utente per la lingua si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire progettazione form.<br /><br /> Per altre informazioni, vedere [Creazione di un linguaggio Forms-Based Domain-Specific Windows](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Progettazione WPF minima|- Un modello di piccole dimensioni<br />- Interfaccia Windows Presentation Foundation utente che visualizza il modello|Usare questo modello se si vuole compilare un'applicazione in cui un DSL è associato a un'interfaccia utente WPF, anziché a una finestra di progettazione grafica.<br /><br /> La finestra di progettazione per l'interfaccia utente si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione dell'interfaccia utente.<br /><br /> Per altre informazioni, vedere [Creazione di un WPF-Based Domain-Specific lingua.](../modeling/creating-a-wpf-based-domain-specific-language.md)|
|Libreria DSL|- Una libreria minima|Usare questo modello se si vuole compilare una definizione DSL parziale che può essere importata in altre definizioni DSL.|

## <a name="see-also"></a>Vedi anche

- [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)
