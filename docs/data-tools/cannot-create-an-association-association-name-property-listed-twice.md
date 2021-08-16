---
title: Proprietà elencata due volte
description: "Impossibile creare un'associazione: proprietà elencata due volte. Visualizzare informazioni su questo Visual Studio Object Relational Designer (O/R Designer)."
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
ms.openlocfilehash: 391d24219063d2c1973361260a36b14d7a30a09e6d00a73476867d15c777130a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380728"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-listed-twice"></a>Impossibile creare un'associazione &lt;nome associazione&gt;. La stessa proprietà è elencata più volte

Impossibile creare un'associazione \<association name> . La stessa proprietà è elencata più di una volta: \<property name> .

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
