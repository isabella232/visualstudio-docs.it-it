---
title: Impossibile creare un nome di associazione di associazione &lt; &gt; . i tipi di proprietà non corrispondono | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 97ec5a04-6e23-45a2-9226-d77ead854392
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 1c93221710f8adc2421f902f27fdb96d957c9cd2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72651145"
---
# <a name="cannot-create-an-association-ltassociation-namegt---property-types-do-not-match"></a>Impossibile creare un'associazione &lt;nome associazione&gt;. Le proprietà non hanno tipi corrispondenti
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Impossibile creare un'associazione \<association name> . i tipi di proprietà non corrispondono. Le proprietà non hanno tipi corrispondenti: \<property names> .

 Le associazioni vengono definite dalle **Proprietà associazione** selezionate nella finestra di dialogo **Editor di associazione**. Le proprietà di ciascun lato dell'associazione devono presentare lo stesso tipo di dati.

 Quelle elencate nel messaggio non presentano gli stessi tipi di dati.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Esaminare il messaggio e prendere nota delle proprietà menzionate in esso.

2. Fare clic su **OK** per chiudere la finestra di dialogo.

3. Controllare le **Proprietà associazione** e selezionare le proprietà che presentano lo stesso tipo di dati.

4. Fare clic su **OK**.

## <a name="see-also"></a>Vedere anche
 Procedura [: creare un'associazione (relazione) tra classi LINQ to SQL (o/r designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [procedura dettagliata: creazione di classi LINQ to SQL (o-r designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
