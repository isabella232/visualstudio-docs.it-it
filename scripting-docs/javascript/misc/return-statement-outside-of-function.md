---
title: istruzione ' Return ' esterna alla funzione | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1018
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 03568f9f-5f4f-4a10-a738-9a73f3832b9e
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: a90af6de8e2c238e3660111b19d13c1eaf628c9e
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573695"
---
# <a name="return-statement-outside-of-function"></a>Istruzione 'return' esterna alla funzione
È stata usata un'istruzione `return` nell'ambito globale del codice. L'istruzione `return` deve essere presente solo all'interno del corpo di una funzione.  
  
 La chiamata di una funzione con l'operatore `()` è un'espressione. Tutte le espressioni hanno valori; l'istruzione `return` viene utilizzata per specificare il valore restituito da una funzione. Il modulo generale è:  
  
```js
  
return [ expression ];  
```  
  
 Quando viene eseguita l'istruzione `return`, l' *espressione* viene valutata e restituita come valore della funzione. Se non è presente alcuna espressione, viene restituito **undefined** .  
  
 L'esecuzione della funzione si interrompe quando viene eseguita l'istruzione `return`, anche se sono ancora presenti altre istruzioni nel corpo della funzione. L'eccezione a questa regola è rappresentata dal caso in cui l'istruzione **return** si verifica all'interno di un blocco **try** ed è presente un blocco **finally** corrispondente, il codice nel blocco **finally** verrà eseguito prima che la funzione restituisca.  
  
 Se una funzione restituisce perché raggiunge la fine del corpo della funzione senza eseguire un'istruzione `return`, il valore restituito è il valore non **definito** (ciò significa che il risultato della funzione non può essere usato come parte di un'espressione più grande).  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Rimuovere l'istruzione `return` dal corpo principale del codice (ambito globale).  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione return](../../javascript/reference/return-statement-javascript.md)   
 @No__t_1 [oggetto funzione](../../javascript/reference/function-object-javascript.md)  
 [Proprietà caller (Function)](../../javascript/reference/caller-property-function-javascript.md)