---
title: Funzione prevista | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5002
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f62ade94-9f6f-4832-9b9b-49a06a385bbe
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f177bf81a43c45dcff4cef3040c64425ed544057
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/01/2020
ms.locfileid: "85816969"
---
# <a name="function-expected"></a>Prevista funzione
Si è provato a richiamare uno dei metodi del **prototipo di funzione** su un oggetto che non era un `Function` oggetto oppure è stato usato un oggetto in un contesto di chiamata di funzione. Il codice seguente, ad esempio, genera questo errore perché **ad esempio** non è una funzione.  
  
```JavaScript  
var example = new Object();  // Create a new object called "example".  
var x = example();           // Try and call example as if it were a function.  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Chiamare solo i metodi del **prototipo di funzione** sugli `Function` oggetti.  
  
- Assicurarsi di usare l'operatore `()` di chiamata di funzione per chiamare solo funzioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Function](../../javascript/reference/function-object-javascript.md)   
 [Proprietà prototype (Object)](../../javascript/reference/prototype-property-object-javascript.md)