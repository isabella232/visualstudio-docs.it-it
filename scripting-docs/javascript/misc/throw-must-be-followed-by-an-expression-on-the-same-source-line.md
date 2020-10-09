---
title: Throw deve essere seguito da un'espressione nella stessa riga di codice sorgente | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b03b7747-01a1-40c6-af80-a1dd70bc5781
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b1ce004eb523497b912e8d7ec29c3b03044f0220
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861995"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>La parola chiave 'throw' deve essere seguita da un'espressione nella stessa riga di codice sorgente
È stata usata la `throw` parola chiave, ma non è stata seguita da un'espressione nella stessa riga di codice sorgente. Un' `throw` istruzione è costituita da due parti: la `throw` parola chiave, seguita dall'espressione da generare. Ad esempio:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Non è possibile dividere questi due componenti.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che la `throw` parola chiave e l'espressione da generare vengano visualizzate nella stessa riga.  
  
## <a name="see-also"></a>Vedere anche  
 [Error (oggetto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Istruzione throw](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [prova... rileva... finally (istruzione)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)