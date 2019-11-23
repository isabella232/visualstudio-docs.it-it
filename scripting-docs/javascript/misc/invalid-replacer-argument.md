---
title: Argomento sostitutivo non valido | Microsoft Docs
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
ms.openlocfilehash: 9ba76a2121dfb3853e38bacbdf49c985103c2a35
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573801"
---
# <a name="invalid-replacer-argument"></a>Argomento Replacer non valido
È stato effettuato un tentativo di richiamare `JSON.stringify` con un argomento non valido. L'argomento `replacer` deve essere una funzione o una matrice.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Modificare l'argomento `replacer` in una funzione o in una matrice.  
  
## <a name="example"></a>Esempio  
 Il codice in questo esempio causa un errore di runtime perché `memberfilter` è un oggetto anziché una funzione o una matrice.  
  
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
   [oggetto JSON](../../javascript/reference/json-object-javascript.md)  
 [Funzione JSON. parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Errori di runtime JavaScript](../../javascript/reference/javascript-run-time-errors.md)