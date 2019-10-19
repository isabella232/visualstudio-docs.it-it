---
title: Throw deve essere seguito da un'espressione nella stessa riga di codice sorgente | Microsoft Docs
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
ms.openlocfilehash: 8854acb3d1992283899c4ff095f5d754c05f55a1
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572753"
---
# <a name="throw-must-be-followed-by-an-expression-on-the-same-source-line"></a>La parola chiave 'throw' deve essere seguita da un'espressione nella stessa riga di codice sorgente
È stata usata la parola chiave `throw`, ma non è stata seguita da un'espressione nella stessa riga di codice sorgente. Un'istruzione `throw` è costituita da due parti: la parola chiave `throw`, seguita dall'espressione da generare. Esempio:  
  
```JavaScript  
if (denominator == 0) {  
 throw new DivideByZeroException();  
}  
```  
  
 Non è possibile dividere questi due componenti.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Verificare che la parola chiave `throw` e l'espressione da generare vengano visualizzate nella stessa riga.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [oggetto errore](../../javascript/reference/error-object-javascript.md)  
 [istruzione throw](../../javascript/reference/throw-statement-javascript.md)    
 [Istruzione try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)