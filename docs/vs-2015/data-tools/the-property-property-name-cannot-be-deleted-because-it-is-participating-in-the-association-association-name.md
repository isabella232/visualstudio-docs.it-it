---
title: Impossibile eliminare la proprietà &lt;property nome &gt; perché partecipa al nome del &lt;association di associazione &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 53bf12a84a705ddca0cacffc36028698cb08443a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667265"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Impossibile eliminare la proprietà &lt;nome proprietà&gt; perché partecipa all'associazione &lt;nome associazione&gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La proprietà selezionata viene impostata come **Proprietà associazione** per l'associazione tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano a un'associazione tra classi di dati.

 Impostare **Proprietà associazione** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. Selezionare la linea di associazione in Progettazione relazionale oggetti che connette le classi di dati indicate nel messaggio di errore.

2. Fare doppio clic sulla linea per aprire la finestra di dialogo **Editor di associazione**.

3. Rimuovere la proprietà dalle **Proprietà associazione**.

4. Provare a eliminare nuovamente la proprietà.

## <a name="see-also"></a>Vedere anche
 [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md) [procedura: creare un'associazione (relazione) tra classi LINQ to SQL (o/r designer)](../data-tools/how-to-create-an-association-relationship-between-linq-to-sql-classes-o-r-designer.md) [procedura dettagliata: creazione di classi di LINQ to SQL (o-r designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) [LINQ to SQL](https://msdn.microsoft.com/library/73d13345-eece-471a-af40-4cc7a2f11655)
