---
title: La proprietà &lt;nome della proprietà&gt; non può essere eliminato perché è inclusa nell'associazione &lt;il nome dell'associazione&gt; | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 389873cc-92dd-48da-bfca-0f6c8e0ae3c2
author: gewarren
ms.author: gewarren
manager: douge
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 5121d79e6db6bdef1deb0ee04540295b2a109f72
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted-because-it-is-participating-in-the-association-ltassociation-namegt"></a>La proprietà &lt;nome della proprietà&gt; non può essere eliminato perché si trova nell'oggetto association &lt;il nome dell'associazione&gt;
La proprietà selezionata viene impostata come la **proprietà associazione** per l'associazione tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano a un'associazione tra classi di dati.  
  
 Impostare il **proprietà associazione** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Selezionare la linea di associazione in Progettazione relazionale oggetti che connette le classi di dati indicate nel messaggio di errore.  
  
2.  Fare doppio clic sulla linea per aprire la **Editor di associazione** la finestra di dialogo.  
  
3.  Rimuovere la proprietà di **proprietà associazione**.  
  
4.  Provare a eliminare nuovamente la proprietà.  
  
## <a name="see-also"></a>Vedere anche
[Messaggi di Object Relational Designer](../data-tools/o-r-designer-messages.md)  
[Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)