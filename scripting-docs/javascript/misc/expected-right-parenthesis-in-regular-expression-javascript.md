---
title: Previsto &#39;)&#39; nell'espressione regolare (JavaScript) | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- VS.WebClient.Help.SCRIPT5020
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b5d1075a41d2b97d10166b1372e8df3a93dd9d8e
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279128"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Previsto &#39;)&#39; nell'espressione regolare (JavaScript)
Si ha provato a creare un'acquisizione di espressioni regolari, asserzione o gruppo, ma non include la parentesi di chiusura. Tra parentesi hanno scopi diversi nelle espressioni regolari. In primo luogo, vengono usati per acquisire le sottoespressioni, per specificare le asserzioni, o per raggruppare i modelli in modo che gli elementi possono essere considerati come una singola unità da *, +,? e così via.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere le parentesi di chiusura all'estrema destra.  
  
    > [!NOTE]
    >  Se si desidera corrisponde una parentesi singola, eseguirne l'escape con una barra rovesciata - \\(: in modo che non viene interpretato come un carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](https://msdn.microsoft.com/library/1400241x)