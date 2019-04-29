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
ms.openlocfilehash: bae4ed0a335a9c12d16cb46208f77c4b66f12547
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62946329"
---
# <a name="exception-thrown-and-not-caught"></a>Eccezione generata e non rilevata
È incluso un `throw` istruzione nel codice, ma non è stato racchiuso all'interno di un **provare** blocco, o è stato associato alcun **catch** blocco per l'errore intercettato. Le eccezioni generate dall'interno la **provare** bloccato tramite il **throw** istruzione e rilevata di fuori il **provare** blocco con un **catch** istruzione.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Racchiudere il codice che può generare un'eccezione in un **provare** block e assicurarsi che ci sia un corrispondente **catch** blocco.  
  
- Assicurarsi che l'istruzione catch si aspetta che la forma corretta dell'eccezione.  
  
- Se viene nuovamente generata l'eccezione, assicurarsi che sia presente un'altra istruzione catch corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)   
 [Throw (istruzione)](../../javascript/reference/throw-statement-javascript.md)   
 [Istruzione try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)