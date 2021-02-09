---
title: La proprietà partecipa all'associazione
description: Impossibile eliminare la proprietà perché partecipa all'associazione. Visualizzare le informazioni su questo messaggio Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- data-storage
ms.openlocfilehash: 99115a3c04aec71e7d000dfa4e707eacb0e28cf3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99866398"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Impossibile eliminare la proprietà &lt;nome proprietà&gt; perché partecipa all'associazione &lt;nome associazione&gt;

La proprietà selezionata viene impostata come **Proprietà associazione** per l'associazione tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano a un'associazione tra classi di dati.

Impostare **Proprietà associazione** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Selezionare la linea di associazione nella **finestra di progettazione O/R** che connette le classi di dati indicate nel messaggio di errore.

2. Fare doppio clic sulla linea per aprire la finestra di dialogo **Editor di associazione**.

3. Rimuovere la proprietà dalle **Proprietà associazione**.

4. Provare a eliminare nuovamente la proprietà.

## <a name="see-also"></a>Vedi anche

- [Strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)