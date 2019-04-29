---
title: Impossibile eliminare la proprietà perché partecipa all'associazione
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6563cc81be8f026a9b2230b0664c678b5649ca9e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565945"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Impossibile eliminare la proprietà &lt;nome proprietà&gt; perché partecipa all'associazione &lt;nome associazione&gt;

La proprietà selezionata viene impostata come **Proprietà associazione** per l'associazione tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano a un'associazione tra classi di dati.

Impostare **Proprietà associazione** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Selezionare la linea di associazione in **Object Relational Designer** che connette le classi di dati indicate nel messaggio di errore.

2. Fare doppio clic sulla linea per aprire la finestra di dialogo **Editor di associazione**.

3. Rimuovere la proprietà dalle **Proprietà associazione**.

4. Provare a eliminare nuovamente la proprietà.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)