---
title: Impossibile eliminare la proprietà
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: jillfra
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: 6940da198fddc4213bbec1271164b20cfbeb6672
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54994160"
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