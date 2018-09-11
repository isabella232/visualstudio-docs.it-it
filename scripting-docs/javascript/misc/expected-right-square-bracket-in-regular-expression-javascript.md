---
title: Previsto &#39;]&#39; nell'espressione regolare (JavaScript) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 64ef929ba309f0b496e72f3cf740daf6970d08fb
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44283717"
---
# <a name="expected-3939-in-regular-expression-javascript"></a>Previsto &#39;]&#39; nell'espressione regolare (JavaScript)
Si ha provato a creare una classe di caratteri per trovare una corrispondenza di espressione regolare, ma non include la parentesi quadra chiusa. Le combinazioni di caratteri letterali singoli possono essere assemblate in classi di caratteri, posizionandoli all'interno di parentesi quadre. Una classe di caratteri corrisponde a qualsiasi carattere che contiene. Ad esempio, / [lettere abc] corrisponde a una qualsiasi lettera "a", "b" o "c".  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere la parentesi quadra chiusa all'espressione regolare.  
  
    > [!NOTE]
    >  Se si desidera corrisponde una parentesi singola, eseguirne l'escape con una barra rovesciata - \\[, in modo che non viene interpretato come un carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](https://msdn.microsoft.com/library/1400241x)