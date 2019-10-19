---
title: Riferimento circolare nell'argomento value non supportato | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5034
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 5d06f0fa-86f5-49d1-8d50-af1759990f43
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 542fca58778a7b85b3044ce984b6ea049db12509
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572343"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Riferimento circolare nell'argomento Value non supportato
È stato effettuato un tentativo di richiamare `JSON.stringify` con un valore non valido. Il `value` argomento, una matrice o un oggetto, contiene un riferimento circolare.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Rimuovere il riferimento circolare dall'argomento.  
  
## <a name="example"></a>Esempio  
 Il codice in questo esempio causa un errore di runtime perché `john` dispone di un riferimento a `mary` e `mary` contiene un riferimento a `john`. per rimuovere il riferimento circolare, rimuovere o annullare la `brother` della proprietà dall'oggetto `mary` o dalla proprietà `sister` dall'oggetto `john`.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 [oggetto JSON](../../javascript/reference/json-object-javascript.md)  
 [Funzione JSON. parse](../../javascript/reference/json-parse-function-javascript.md)    
 [Errori di runtime JavaScript](../../javascript/reference/javascript-run-time-errors.md)