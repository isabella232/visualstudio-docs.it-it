---
title: Previsto ')' nell'espressione regolare (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: 6c344105010e406ef4936fdcca58baffbd610088
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347424"
---
# <a name="expected--in-regular-expression-javascript"></a>Prevista ')' nell'espressione regolare (JavaScript)
Si ha provato a creare un'acquisizione di espressioni regolari, asserzione o gruppo, ma non include la parentesi di chiusura. Tra parentesi hanno scopi diversi nelle espressioni regolari. In primo luogo, vengono usati per acquisire le sottoespressioni, per specificare le asserzioni, o per raggruppare i modelli in modo che gli elementi possono essere considerati come una singola unità da *, +,? e così via.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere le parentesi di chiusura all'estrema destra.  
  
    > [!NOTE]
    >  Se si desidera corrisponde una parentesi singola, eseguirne l'escape con una barra rovesciata - \\(: in modo che non viene interpretato come un carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](https://msdn.microsoft.com/library/1400241x)