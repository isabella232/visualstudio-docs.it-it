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
ms.openlocfilehash: 6a0e3eb6d1275e5598ad44ea553e22f0b53eeb45
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91862765"
---
# <a name="exception-thrown-and-not-caught"></a>Eccezione generata e non rilevata
È stata inclusa un' `throw` istruzione nel codice, ma non è stata inclusa in un blocco **try** oppure non è stato associato alcun blocco **catch** per intercettare l'errore. Le eccezioni vengono generate all'interno del blocco **try** utilizzando l'istruzione **throw** e rilevate all'esterno del blocco **try** con un'istruzione **catch** .  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Racchiudere il codice che può generare un'eccezione in un blocco **try** e verificare che sia presente un blocco **catch** corrispondente.  
  
- Verificare che l'istruzione catch preveda il formato corretto dell'eccezione.  
  
- Se l'eccezione viene generata nuovamente, verificare che sia presente un'altra istruzione catch corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Error (oggetto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Istruzione throw](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [prova... rileva... finally (istruzione)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)