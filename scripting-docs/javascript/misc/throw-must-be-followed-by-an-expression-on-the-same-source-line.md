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
ms.openlocfilehash: b7bc7ff09152cd0ce7b95c6de73ea98446529c44
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85815526"
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
 [Error (oggetto)](../../javascript/reference/error-object-javascript.md)   
 [Istruzione throw](../../javascript/reference/throw-statement-javascript.md)   
 [prova... rileva... finally (istruzione)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)