---
description: È stato effettuato un tentativo di richiamare JSON. stringify con un argomento non valido.
title: Argomento sostitutivo non valido | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 95a73d6fcbcf1350eece52e2cd58693646617a28
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570895"
---
# <a name="invalid-replacer-argument"></a>Argomento Replacer non valido
È stato effettuato un tentativo di richiamare `JSON.stringify` con un argomento non valido. L' `replacer` argomento deve essere una funzione o una matrice.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Modificare l' `replacer` argomento in una funzione o in una matrice.  
  
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
  
## <a name="see-also"></a>Vedi anche  
 [JSON (oggetto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON)   
 [Funzione JSON. Parse](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)   
 [Errori di runtime JavaScript](/microsoft-edge/devtools-guide/console/error-and-status-codes#javascript-run-time-errors)
