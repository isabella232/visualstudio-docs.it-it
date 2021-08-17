---
title: La proprietà partecipa all'associazione
description: Impossibile eliminare la proprietà perché fa parte dell'associazione. Visualizzare informazioni su questo Object Relational Designer (O/R Designer).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: error-reference
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: dc732273719484b7f2f3eaf26a39a8ff518ee3dc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122067007"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>Impossibile eliminare la proprietà &lt;nome proprietà&gt; perché partecipa all'associazione &lt;nome associazione&gt;

La proprietà selezionata viene impostata come **Proprietà associazione** per l'associazione tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano a un'associazione tra classi di dati.

Impostare **Proprietà associazione** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.

## <a name="to-correct-this-error"></a>Per correggere l'errore

1. Selezionare la riga di associazione in **Progettazione O/R** che connette le classi di dati indicate nel messaggio di errore.

2. Fare doppio clic sulla linea per aprire la finestra di dialogo **Editor di associazione**.

3. Rimuovere la proprietà dalle **Proprietà associazione**.

4. Provare a eliminare nuovamente la proprietà.

## <a name="see-also"></a>Vedi anche

- [LINQ to SQL strumenti in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)