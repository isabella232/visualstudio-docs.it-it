---
title: 'Procedura: Creare associazioni tra tipi (Progettazione classi)'
description: Informazioni su come creare associazioni tra tipi diversi in Progettazione classi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.classdesigner.associationline
helpviewer_keywords:
- types [Visual Studio], associations
- association lines, defining (Class Designer)
- defining association lines (Class Designer)
- associations, types
- association lines
ms.assetid: adccb9c8-2f8a-4086-9fa9-f70f99fb6e00
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f72cb173b5ece347bb2d9eb1b4ef0e8d2317b21d
ms.sourcegitcommit: 86e98df462b574ade66392f8760da638fe455aa0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/19/2020
ms.locfileid: "94901609"
---
# <a name="how-to-create-associations-between-types-in-class-designer"></a>Procedura: Creare associazioni tra tipi in Progettazione classi

Le linee di associazione in **Progettazione classi** mostrano la correlazione tra le classi di un diagramma. Una linea di associazione rappresenta una classe che corrisponde al tipo di una proprietà o di un campo di un'altra classe del progetto. Le linee di associazione vengono in genere utilizzate per illustrare le relazioni più importanti tra le classi del progetto.

Anche se è possibile visualizzare tutti i campi e tutte le proprietà come associazioni, è opportuno effettuare questa operazione solo per i membri importanti, a seconda degli elementi si intende evidenziare nel diagramma. I membri meno importanti possono essere visualizzati come membri normali oppure possono essere nascosti.

> [!NOTE]
> **Progettazione classi** supporta solo associazioni unidirezionali.

## <a name="to-define-an-association-line-in-the-class-diagram"></a>Per definire una linea di associazione in Diagramma classi

1. Nella casella degli strumenti, in **Progettazione classi**, selezionare **associazione**.

2. Disegnare una linea tra le due forme da collegare con un'associazione.

     Nella prima classe verrà creata una nuova proprietà, visualizzata come una linea di associazione (non come una proprietà all'interno di un raggruppamento della forma) con un nome predefinito. Il tipo di questa proprietà è la forma a cui punta la linea di associazione.

## <a name="to-change-the-name-of-an-association"></a>Per cambiare il nome di un'associazione

Sulla superficie del diagramma fare clic sull'etichetta della linea di associazione e modificarla.

In alternativa, seguire questi passaggi:

1. Selezionare la forma che contiene la proprietà visualizzata come associazione.

   La forma acquisisce lo stato attivo e i relativi membri vengono visualizzati nelle finestre **Dettagli classe** e **Proprietà**.

2. Nella finestra **Dettagli classe** o **Proprietà** modificare il campo del nome relativo alla proprietà e premere **Invio**.

   Il nome viene aggiornato nella finestra **Dettagli classe**, sulla linea di associazione, nella finestra **Proprietà** e nel codice.

## <a name="see-also"></a>Vedere anche

- [Procedura: passare dalla notazione membro alla notazione associazione](how-to-change-between-member-notation-and-association-notation.md)
