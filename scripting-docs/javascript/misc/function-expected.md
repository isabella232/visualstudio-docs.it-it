---
title: Prevista funzione | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: aa2db3e95d4baece288c9f984a7a9cf7a82c9d1d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49928932"
---
# <a name="function-expected"></a>Prevista funzione
Che si è tentato di richiamare una delle **prototipo di funzione** metodi su un oggetto che non era un `Function` oggetto oppure è utilizzato un oggetto in un contesto di chiamata di funzione. Ad esempio, il codice seguente genera l'errore in quanto **esempio** non è una funzione.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Chiamare solo **prototipo di funzione** metodi su `Function` oggetti.  
  
-   Assicurarsi di usare l'operatore di chiamata di funzione `()` chiamare solo funzioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto funzione](../../javascript/reference/function-object-javascript.md)   
 [Proprietà prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)