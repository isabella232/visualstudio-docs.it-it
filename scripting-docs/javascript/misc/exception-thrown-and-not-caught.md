---
title: Eccezione generata e non rilevata | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
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
ms.openlocfilehash: 44f207d2e32a7ca79ee0d5851a80261c5da9743d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85814590"
---
# <a name="exception-thrown-and-not-caught"></a>Eccezione generata e non rilevata
È stata inclusa un' `throw` istruzione nel codice, ma non è stata inclusa in un blocco **try** oppure non è stato associato alcun blocco **catch** per intercettare l'errore. Le eccezioni vengono generate all'interno del blocco **try** utilizzando l'istruzione **throw** e rilevate all'esterno del blocco **try** con un'istruzione **catch** .  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Racchiudere il codice che può generare un'eccezione in un blocco **try** e verificare che sia presente un blocco **catch** corrispondente.  
  
- Verificare che l'istruzione catch preveda il formato corretto dell'eccezione.  
  
- Se l'eccezione viene generata nuovamente, verificare che sia presente un'altra istruzione catch corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Error (oggetto)](../../javascript/reference/error-object-javascript.md)   
 [Istruzione throw](../../javascript/reference/throw-statement-javascript.md)   
 [prova... rileva... finally (istruzione)](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)