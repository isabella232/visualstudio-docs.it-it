---
description: È stata usata un'istruzione return nell'ambito globale del codice.
title: istruzione ' Return ' esterna alla funzione | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: c275db9b2b13f6730ef62a757502b1d51a59ee43
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571662"
---
# <a name="return-statement-outside-of-function"></a>Istruzione 'return' esterna alla funzione
È stata usata un' `return` istruzione nell'ambito globale del codice. L' `return` istruzione deve essere presente solo all'interno del corpo di una funzione.  
  
 La chiamata di una funzione con l' `()` operatore è un'espressione. Tutte le espressioni hanno valori; l' `return` istruzione viene utilizzata per specificare il valore restituito da una funzione. Il modulo generale è:  
  
```js
  
return [ expression ];  
```  
  
 Quando l' `return` istruzione viene eseguita, l' *espressione* viene valutata e restituita come valore della funzione. Se non è presente alcuna espressione, viene restituito **undefined** .  
  
 L'esecuzione della funzione si interrompe quando `return` viene eseguita l'istruzione, anche se sono ancora presenti altre istruzioni nel corpo della funzione. L'eccezione a questa regola è rappresentata dal caso in cui l'istruzione **return** si verifica all'interno di un blocco **try** ed è presente un blocco **finally** corrispondente, il codice nel blocco **finally** verrà eseguito prima che la funzione restituisca.  
  
 Se una funzione restituisce perché raggiunge la fine del corpo della funzione senza eseguire un' `return` istruzione, il valore restituito è il valore non **definito** (ciò significa che il risultato della funzione non può essere usato come parte di un'espressione più grande).  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Rimuovere l' `return` istruzione dal corpo principale del codice (ambito globale).  
  
## <a name="see-also"></a>Vedi anche  
 [return (istruzione)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/return)   
 [Oggetto Function](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function)   
 [Proprietà caller (Function)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Function/caller)
