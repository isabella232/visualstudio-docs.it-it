---
title: I tipi di proprietà non corrispondono
description: Impossibile creare un'associazione. i tipi di proprietà non corrispondono. Visualizza le informazioni su questo messaggio di Object Relational Designer di Visual Studio (O/R Designer).
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: bce5a285f3bccdc2be8004f0eba4546bb7964a42
ms.sourcegitcommit: 0893244403aae9187c9375ecf0e5c221c32c225b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2020
ms.locfileid: "94382052"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>Impossibile creare un'associazione &lt;nome associazione&gt;. Le proprietà non hanno tipi corrispondenti

Impossibile creare un'associazione \<association name> . i tipi di proprietà non corrispondono. Le proprietà non hanno tipi corrispondenti: \<property names> .

Le associazioni vengono definite dalle **Proprietà associazione** selezionate nella finestra di dialogo **Editor di associazione**. Le proprietà di ciascun lato dell'associazione devono presentare lo stesso tipo di dati.

Quelle elencate nel messaggio non presentano gli stessi tipi di dati.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Esaminare il messaggio e prendere nota delle proprietà menzionate in esso.

2. Fare clic su **OK** per chiudere la finestra di dialogo.

3. Controllare le **Proprietà associazione** e selezionare le proprietà che presentano lo stesso tipo di dati.

4. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura: creare un'associazione tra classi di LINQ to SQL (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)