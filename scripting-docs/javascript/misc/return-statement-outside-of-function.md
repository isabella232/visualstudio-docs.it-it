---
title: istruzione ' return' esterna (funzione) | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 82ba1488692f8e8b59063b8f9a52b0682d27e7f8
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2019
ms.locfileid: "54096447"
---
# <a name="return-statement-outside-of-function"></a>Istruzione 'return' esterna alla funzione
È stato usato un `return` istruzione nell'ambito globale del codice. Il `return` istruzione deve essere visualizzato solo all'interno del corpo di una funzione.  
  
 Richiamo di una funzione con il `()` operatore è un'espressione. Tutte le espressioni hanno valori. il `return` istruzione viene utilizzata per specificare il valore restituito da una funzione. Il formato generale è:  
  
```js
  
return [ expression ];  
```  
  
 Quando la `return` istruzione viene eseguita, *espressione* viene valutata e restituita come valore della funzione. Se nessuna espressione **indefinito** viene restituito.  
  
 Esecuzione della funzione si interrompe quando il `return` istruzione viene eseguita, anche se sono presenti altre istruzioni rimanenti ancora nel corpo della funzione. L'eccezione a questa regola è se il **restituire** istruzione si trova all'interno di un **provare** blocco, ed è presente un corrispondente **infine** blocco, il codice nel  **infine** blocco verrà eseguite prima che la funzione restituisce.  
  
 Se una funzione restituisce perché raggiunge la fine del corpo della funzione senza l'esecuzione di un `return` istruzione, il valore restituito è il **indefinito** valore (in questo caso il risultato di funzione non può essere utilizzato come parte di un'espressione più ampia ).  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Rimuovere il `return` istruzione dal corpo principale del codice (ambito globale).  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione return](../../javascript/reference/return-statement-javascript.md)   
 [Oggetto funzione](../../javascript/reference/function-object-javascript.md)   
 [Proprietà caller (Function)](../../javascript/reference/caller-property-function-javascript.md)