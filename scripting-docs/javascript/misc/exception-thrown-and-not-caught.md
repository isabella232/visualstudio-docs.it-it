---
title: Eccezione generata e non rilevata | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT5022
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: b5235490-a8e7-42e3-804e-d85235bc6f05
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 839ff08da4d26406b508a206c809b0813d2b32e1
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349036"
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