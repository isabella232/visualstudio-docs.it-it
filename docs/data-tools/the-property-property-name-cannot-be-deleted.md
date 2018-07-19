---
title: La proprietà non può essere eliminata
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 7e85860de7494ae7d93ad37bd0a115fa786f0a87
ms.sourcegitcommit: f37affbc1b885dfe246d4b2c295a6538b383a0ca
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/02/2018
ms.locfileid: "37174013"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>La proprietà \<nome proprietà > non può essere eliminato

La proprietà \<nome proprietà > non può essere eliminato perché è impostato come il **Discriminator Property** per l'ereditarietà tra \<nome classe > e \<nome classe >

La proprietà selezionata viene impostata come la **Discriminator Property** per l'ereditarietà tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano alla configurazione dell'ereditarietà tra le classi di dati.

Impostare il **Discriminator Property** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Nel **O/R Designer**, selezionare la linea di ereditarietà che connette le classi di dati indicata nel messaggio di errore.

2. Impostare il **discriminatore** proprietà su una diversa proprietà.

3. Provare a eliminare nuovamente la proprietà.

## <a name="see-also"></a>Vedere anche

- [Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)
- [Strumenti LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)