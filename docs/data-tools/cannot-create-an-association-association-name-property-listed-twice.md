---
title: Impossibile creare un'associazione. La stessa proprietà è elencata più volte
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: da5ee57dda360f9851737fe061ee02c6aeae4c8e
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54954748"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossibile creare un'associazione &lt;nome associazione&gt;. La stessa proprietà è elencata più volte

Impossibile creare un'associazione \<nome associazione>. La stessa proprietà è elencata più volte: \<nome proprietà>.

Le associazioni vengono definite dalle **Proprietà associazione** selezionate nella finestra di dialogo **Editor di associazione**. Le proprietà possono essere elencate una sola volta per ogni classe nell'associazione.

La proprietà specificata nel messaggio viene visualizzata più volte nelle **Proprietà associazione** della classe padre o figlio.

## <a name="to-resolve-this-condition"></a>Risoluzione del problema

- Esaminare il messaggio e prendere nota della proprietà specificata in esso.

- Fare clic su **OK** per chiudere la finestra del messaggio.

- Controllare le **Proprietà associazione** e rimuovere le voci duplicate.

- Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura: Creare un'associazione tra classi LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)