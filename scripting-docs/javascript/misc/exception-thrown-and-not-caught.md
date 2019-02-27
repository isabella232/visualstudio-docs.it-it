---
title: Eccezione generata e non rilevata | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
f1_keywords:
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e1e34be9f8eab5171af0e2553d5777b0958bf3c2
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56840870"
---
# <a name="exception-thrown-and-not-caught"></a>Eccezione generata e non rilevata
È incluso un `throw` istruzione nel codice, ma non è stato racchiuso all'interno di un **provare** blocco, o è stato associato alcun **catch** blocco per l'errore intercettato. Le eccezioni generate dall'interno la **provare** bloccato tramite il **throw** istruzione e rilevata di fuori il **provare** blocco con un **catch** istruzione.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Racchiudere il codice che può generare un'eccezione in un **provare** block e assicurarsi che ci sia un corrispondente **catch** blocco.  
  
-   Assicurarsi che l'istruzione catch si aspetta che la forma corretta dell'eccezione.  
  
-   Se viene nuovamente generata l'eccezione, assicurarsi che sia presente un'altra istruzione catch corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)   
 [Throw (istruzione)](../../javascript/reference/throw-statement-javascript.md)   
 [Istruzione try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)