---
title: Previsto ']' nell'espressione regolare (JavaScript) | Microsoft Docs
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
ms.openlocfilehash: e0b34ae4bdf04d261647b9096cda13eec75617c5
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349426"
---
# <a name="expected--in-regular-expression-javascript"></a>Prevista ']' nell'espressione regolare (JavaScript)
Si ha provato a creare una classe di caratteri per trovare una corrispondenza di espressione regolare, ma non include la parentesi quadra chiusa. Le combinazioni di caratteri letterali singoli possono essere assemblate in classi di caratteri, posizionandoli all'interno di parentesi quadre. Una classe di caratteri corrisponde a qualsiasi carattere che contiene. Ad esempio, / [lettere abc] corrisponde a una qualsiasi lettera "a", "b" o "c".  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere la parentesi quadra chiusa all'espressione regolare.  
  
    > [!NOTE]
    >  Se si desidera corrisponde una parentesi singola, eseguirne l'escape con una barra rovesciata - \\[, in modo che non viene interpretato come un carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto di espressione regolare](../../javascript/reference/regular-expression-object-javascript.md)   
 [Sintassi di espressione regolare (JavaScript)](https://msdn.microsoft.com/library/1400241x)