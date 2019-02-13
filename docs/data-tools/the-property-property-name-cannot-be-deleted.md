---
title: Impossibile eliminare la proprietà
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 4b1e0652d19b10b1d1ede7b1b950d89ca1bf670c
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2019
ms.locfileid: "55939645"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Impossibile eliminare la proprietà \<nome proprietà>

Impossibile eliminare la proprietà \<nome proprietà>, perché è usata come **Proprietà Discriminator** per l'ereditarietà tra \<nome classe> e \<nome classe>

La proprietà selezionata è impostata come **Proprietà Discriminator** per l'ereditarietà tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano alla configurazione dell'ereditarietà tra le classi di dati.

Impostare **Proprietà Discriminator** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. In **Object Relational Designer** selezionare la linea di ereditarietà che connette le classi di dati indicate nel messaggio di errore.

2. Impostare **Proprietà Discriminator** su una diversa proprietà.

3. Provare a eliminare nuovamente la proprietà.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)