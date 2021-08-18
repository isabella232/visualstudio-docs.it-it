---
title: Scelta di un modello di soluzione per un linguaggio specifico di dominio
description: Informazioni su come creare una soluzione per un linguaggio specifico di dominio scegliendo uno dei modelli di soluzione disponibili nella Domain-Specific Guidata linguaggio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.technology: vs-ide-modeling
ms.workload:
- multiple
ms.openlocfilehash: 1b3d680df7f04b91c7640d54d994f38b84e41e10
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122085676"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Scelta di un modello di soluzione per un linguaggio specifico di dominio
Per creare una soluzione per un linguaggio specifico di dominio, scegliere uno dei modelli di soluzione disponibili nella creazione guidata Domain-Specific Language Designer. Scegliendo il modello più simile al linguaggio che si vuole creare, è possibile ridurre al minimo le modifiche da apportare alla soluzione iniziale.

 I modelli di soluzione seguenti sono disponibili nella Domain-Specific Guidata linguaggio.

|Modello|Funzionalità|Descrizione|
|-|-|-|
|Diagrammi classi|- Raggruppamento di forme<br />- Ereditarietà delle classi<br />- Ereditarietà delle relazioni<br />- Ereditarietà delle forme<br />- Proprietà delle relazioni|Usare questo modello di soluzione se il linguaggio specifico di dominio include entità e relazioni con proprietà. Questo modello crea un linguaggio specifico di dominio simile ai diagrammi classi UML. Le entità principali sono classi e interfacce, insieme a relazioni di associazione, generalizzazione e implementazione. Una classe o un'interfaccia viene visualizzata come casella contenente un elenco di attributi.|
|Diagrammi dei componenti|- Porte|Usare questo modello di soluzione se il linguaggio specifico di dominio include componenti, ad esempio parti di un sistema software. Questo modello crea un linguaggio specifico di dominio simile ai diagrammi dei componenti UML. Le entità principali sono i componenti e le porte, che appaiono come piccole forme all'esterno dei componenti.|
|Diagrammi Flow attività|- Forme immagine e geometria<br />-   *Corsie*|Usare questo modello di soluzione se il linguaggio specifico di dominio include flussi di lavoro, stati o sequenze. Questo modello crea un linguaggio specifico di dominio simile ai diagrammi di attività UML. L'entità principale è un'attività e la relazione principale è una transizione tra le attività. Il modello include diversi altri elementi, ad esempio lo stato iniziale, lo stato finale e una barra di sincronizzazione.|
|Linguaggio minimo|- Una classe e una forma<br />- Una relazione e un connettore|Usare questo modello di soluzione se il linguaggio specifico di dominio non è simile agli altri modelli. Questo modello crea un linguaggio specifico di dominio che ha due classi e una relazione, rappresentate nella casella degli **strumenti** **come Box** e **Line.** La classe e la relazione hanno ognuna una proprietà stringa di esempio.|
|Finestra di progettazione Windows Form minima|: modello di piccole dimensioni.<br />: modulo Windows che visualizza il modello.|Usare questo modello se si vuole compilare un'applicazione in cui un DSL è associato a un form Windows, anziché a una finestra di progettazione grafica.<br /><br /> Il modulo che funge da interfaccia utente per la lingua si trova nella cartella Dsl\UI.<br /><br /> È consigliabile compilare il progetto prima di aprire progettazione form.<br /><br /> Per altre informazioni, vedere [Creating a Windows Forms-Based Domain-Specific Language](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Wpf Designer minimo|- Un modello di piccole dimensioni<br />- Interfaccia Windows Presentation Foundation utente che visualizza il modello|Usare questo modello se si vuole compilare un'applicazione in cui un DSL è associato a un'interfaccia utente WPF anziché a una finestra di progettazione grafica.<br /><br /> La finestra di progettazione per l'interfaccia utente si trova nella cartella Dsl\UI.<br /><br /> È consigliabile compilare il progetto prima di aprire la finestra di progettazione dell'interfaccia utente.<br /><br /> Per altre informazioni, vedere [Creating a WPF-Based Domain-Specific Language](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Libreria DSL|- Una libreria minima|Usare questo modello se si vuole compilare una definizione DSL parziale che può essere importata in altre definizioni DSL.|

## <a name="see-also"></a>Vedi anche

- [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)
