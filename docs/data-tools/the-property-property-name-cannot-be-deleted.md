---
title: Impossibile eliminare la proprietà
description: La proprietà non può essere eliminata. Visualizzare informazioni su questo Visual Studio Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 95caaef5270b5e5a59567a8d91380347f10fef69c1b2a21de87b7030e6ce98f4
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121346791"
---
# <a name="the-property-property-name-cannot-be-deleted"></a>Impossibile eliminare la proprietà \<property name>

Impossibile eliminare la proprietà perché è impostata come \<property name> proprietà Discriminator **per** l'ereditarietà tra \<class name> e \<class name>

La proprietà selezionata è impostata come **Proprietà Discriminator** per l'ereditarietà tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano alla configurazione dell'ereditarietà tra le classi di dati.

Impostare **Proprietà Discriminator** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. In **Object Relational Designer** selezionare la linea di ereditarietà che connette le classi di dati indicate nel messaggio di errore.

2. Impostare **Proprietà Discriminator** su una diversa proprietà.

3. Provare a eliminare nuovamente la proprietà.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)