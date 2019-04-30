---
title: Previsto ')' nell'espressione regolare (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 7daf5d876f68168ce0b58ea2cc9b52a309107bc6
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63446537"
---
# <a name="expected--in-regular-expression-javascript"></a>Prevista ')' nell'espressione regolare (JavaScript)
Si ha provato a creare un'acquisizione di espressioni regolari, asserzione o gruppo, ma non include la parentesi di chiusura. Tra parentesi hanno scopi diversi nelle espressioni regolari. In primo luogo, vengono usati per acquisire le sottoespressioni, per specificare le asserzioni, o per raggruppare i modelli in modo che gli elementi possono essere considerati come una singola unità da *, +,? e così via.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere le parentesi di chiusura all'estrema destra.  
  
    > [!NOTE]
    > Se si desidera corrisponde una parentesi singola, eseguirne l'escape con una barra rovesciata - \\(: in modo che non viene interpretato come un carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](https://msdn.microsoft.com/library/1400241x)