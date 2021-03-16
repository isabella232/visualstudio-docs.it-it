---
description: Si è tentato di creare una classe di caratteri per una corrispondenza di espressione regolare, ma non è stata inclusa la parentesi quadra chiusa.
title: Previsto ']' nell'espressione regolare (JavaScript) | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b5e7a25f6fbef3bf87d084b149ee9f356981600
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570947"
---
# <a name="expected--in-regular-expression-javascript"></a>Prevista ']' nell'espressione regolare (JavaScript)
Si è tentato di creare una classe di caratteri per una corrispondenza di espressione regolare, ma non è stata inclusa la parentesi quadra chiusa. Le singole combinazioni di caratteri letterali possono essere assemblate in classi di caratteri inserendole tra parentesi quadre. Una classe di caratteri trova la corrispondenza con qualsiasi carattere contenuto. Ad esempio,/[ABC]/corrisponde a una qualsiasi delle lettere "a", "b" o "c".  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere la parentesi quadra chiusa all'espressione regolare.  
  
    > [!NOTE]
    > Se si desidera trovare la corrispondenza con una singola parentesi quadre, eseguire l'escape con una barra rovesciata, in \\ modo che non venga interpretata come carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] .  
  
## <a name="see-also"></a>Vedi anche  
 [Oggetto Regular Expression](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/RegExp)   
 [Sintassi delle espressioni regolari (JavaScript)](/previous-versions/1400241x(v=vs.100))
