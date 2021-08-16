---
title: I tipi di proprietà non corrispondono
description: Impossibile creare un'associazione. I tipi di proprietà non corrispondono. Visualizzare informazioni su questo Visual Studio Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 08848d8db091303bdc980b9017352013d9d42ef61631fb9558d91e538a0b470c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121380715"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>Impossibile creare un'associazione &lt;nome associazione&gt;. Le proprietà non hanno tipi corrispondenti

Impossibile creare \<association name> un'associazione. I tipi di proprietà non corrispondono. Le proprietà non hanno tipi corrispondenti: \<property names> .

Le associazioni vengono definite dalle **Proprietà associazione** selezionate nella finestra di dialogo **Editor di associazione**. Le proprietà di ciascun lato dell'associazione devono presentare lo stesso tipo di dati.

Quelle elencate nel messaggio non presentano gli stessi tipi di dati.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Esaminare il messaggio e prendere nota delle proprietà menzionate in esso.

2. Fare clic su **OK** per chiudere la finestra di dialogo.

3. Controllare le **Proprietà associazione** e selezionare le proprietà che presentano lo stesso tipo di dati.

4. Fare clic su **OK**.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Procedura: Creare un'associazione tra LINQ to SQL classi (O/R Designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md)