---
title: Riferimento circolare nell'argomento value non supportato | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: ''
ms.suite: ''
ms.technology:
- javascript
ms.tgt_pltfrm: ''
ms.topic: article
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
ms.openlocfilehash: d25489065ceece41108a75c9d3763a95e4adb924
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349075"
---
# <a name="circular-reference-in-value-argument-not-supported"></a>Riferimento circolare nell'argomento Value non supportato
È stato eseguito un tentativo di richiamare `JSON.stringify` con un valore che non è valido. Il `value` argomento, una matrice o oggetto, contiene un riferimento circolare.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Rimuovere il riferimento circolare nell'argomento.  
  
## <a name="example"></a>Esempio  
 Il codice in questo esempio provoca un errore di runtime perché `john` contiene un riferimento a `mary` e `mary` contiene un riferimento a `john`. Per rimuovere il riferimento circolare, rimuovere o annullare l'impostazione della proprietà `brother` dal `mary` oggetto o il `sister` proprietà dal `john` oggetto.  
  
```JavaScript  
var john = new Object();  
var mary = new Object();  
john.sister = mary;  
mary.brother = john;  
  
// This line causes a runtime error.  
var error = JSON.stringify(john);  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto JSON](../../javascript/reference/json-object-javascript.md)   
 [Funzione JSON. Parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Errori di runtime JavaScript](../../javascript/reference/javascript-run-time-errors.md)