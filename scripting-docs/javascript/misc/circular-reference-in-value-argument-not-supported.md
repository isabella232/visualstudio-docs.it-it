---
title: Riferimento circolare nell'argomento value non supportato | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 633ed9c37e8ccde0844205910a8fa2dc12d91414
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85817619"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Riferimento circolare nell'argomento Value non supportato
È stato effettuato un tentativo di richiamare `JSON.stringify` con un valore non valido. L' `value` argomento, una matrice o un oggetto, contiene un riferimento circolare.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Rimuovere il riferimento circolare dall'argomento.  
  
## <a name="example"></a>Esempio  
 Il codice in questo esempio causa un errore di runtime perché `john` contiene un riferimento a `mary` e `mary` contiene un riferimento a `john` . per rimuovere il riferimento circolare, rimuovere o annullare la proprietà dall'oggetto `brother` `mary` o dalla `sister` proprietà dall' `john` oggetto.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [JSON (oggetto)](../../javascript/reference/json-object-javascript.md)   
 [Funzione JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Errori di runtime JavaScript](../../javascript/reference/javascript-run-time-errors.md)