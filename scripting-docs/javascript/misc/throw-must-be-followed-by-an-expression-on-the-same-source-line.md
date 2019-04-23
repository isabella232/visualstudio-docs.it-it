---
title: Istruzione throw deve essere seguita da un'espressione nella stessa riga di origine | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 4c8ed951fb30b84f114f8f44a60e94b88f0f1d0f
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60069523"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>La parola chiave 'throw' deve essere seguita da un'espressione nella stessa riga di codice sorgente
È stata usata la `throw` (parola chiave), ma non è stata seguita, con un'espressione nella stessa riga di origine. Oggetto `throw` istruzione è costituita da due parti: il `throw` parola chiave, seguita dall'espressione generata. Ad esempio:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 È possibile suddividere questi due componenti.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Assicurarsi che il `throw` (parola chiave) e l'espressione generata viene visualizzata nella stessa riga.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)   
 [Throw (istruzione)](../../javascript/reference/throw-statement-javascript.md)   
 [Istruzione try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)