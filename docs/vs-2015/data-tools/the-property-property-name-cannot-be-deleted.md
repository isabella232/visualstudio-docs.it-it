---
title: Non è possibile eliminare il nome della proprietà &lt;property &gt; | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: 5
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: aca36919cb4c82d6ca76e0f3eecbbacd48cde768
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667246"
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>Impossibile eliminare il nome della proprietà &lt;property &gt;
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Impossibile eliminare la proprietà \<property nome > perché è impostata come proprietà Discriminator per l'ereditarietà tra nome \<class > e nome \<class >

 La proprietà selezionata è impostata come **Proprietà Discriminator** per l'ereditarietà tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano alla configurazione dell'ereditarietà tra le classi di dati.

 Impostare **Proprietà Discriminator** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.

### <a name="to-correct-this-error"></a>Per correggere l'errore

1. In Progettazione relazionale oggetti selezionare la linea di ereditarietà che connette le classi di dati indicate nel messaggio di errore.

2. Impostare **Proprietà Discriminator** su una diversa proprietà.

3. Provare a eliminare nuovamente la proprietà.

## <a name="see-also"></a>Vedere anche
 Procedura [: configurare l'ereditarietà tramite l'ereditarietà delle classi di dati o/r designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md) [(o/r designer)](../data-tools/data-class-inheritance-o-r-designer.md) [procedura dettagliata: creazione di classi di LINQ to SQL tramite ereditarietà a tabella singola (o/r designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
