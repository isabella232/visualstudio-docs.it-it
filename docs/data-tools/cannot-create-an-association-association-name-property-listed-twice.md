---
title: Proprietà elencata due volte
description: Impossibile creare un'associazione. La proprietà è elencata due volte. Visualizzare informazioni su questo Visual Studio Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.technology: vs-data-tools
ms.assetid: 3ced8bda-210e-4caf-9d8f-96cdbba19251
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: ed577ac9c0ca5263e651433da9cfea1f8bf613ab
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631553"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossibile creare un'associazione &lt;nome associazione&gt;. La stessa proprietà è elencata più volte

Impossibile creare un'associazione \<association name> . La stessa proprietà è elencata più volte: \<property name> .

Le associazioni vengono definite dalle **Proprietà associazione** selezionate nella finestra di dialogo **Editor di associazione**. Le proprietà possono essere elencate una sola volta per ogni classe nell'associazione.

La proprietà specificata nel messaggio viene visualizzata più volte nelle **Proprietà associazione** della classe padre o figlio.

## <a name="to-resolve-this-condition"></a>Risoluzione del problema

- Esaminare il messaggio e prendere nota della proprietà specificata in esso.

- Fare clic su **OK** per chiudere la finestra del messaggio.

- Controllare le **Proprietà associazione** e rimuovere le voci duplicate.

- Fare clic su **OK**.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura: Creare un'associazione tra LINQ to SQL classi (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)
