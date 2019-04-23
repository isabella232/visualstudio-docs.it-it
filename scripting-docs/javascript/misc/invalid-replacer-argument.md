---
title: Argomento replacer non valido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5035
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 4727186f-facd-4aa6-9447-bbefbae83f07
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 46e01a4e6bb989fad2da6f979c79b7aba13df63a
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060787"
---
# <a name="invalid-replacer-argument"></a>Argomento Replacer non valido
È stato eseguito un tentativo di richiamare `JSON.stringify` con un argomento non valido. Il `replacer` argomento deve essere una funzione o una matrice.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Modifica il `replacer` argomento per una funzione o una matrice.  
  
## <a name="example"></a>Esempio  
 Il codice in questo esempio provoca un errore di runtime perché `memberfilter` è un oggetto anziché una funzione o una matrice.  
  
```JavaScript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
var memberfilter = new Object();  
  
// This line will cause a runtime error.  
var jsontext = JSON.stringify(contact, memberfilter, "\t");  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto JSON](../../javascript/reference/json-object-javascript.md)   
 [Funzione JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Errori di runtime JavaScript](../../javascript/reference/javascript-run-time-errors.md)