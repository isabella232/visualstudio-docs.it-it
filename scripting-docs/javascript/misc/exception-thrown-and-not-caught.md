---
description: È stata inclusa un'istruzione throw nel codice, ma non è stata inclusa in un blocco try oppure non è stato associato alcun blocco catch per intercettare l'errore.
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
ms.openlocfilehash: b8abcfced6dfe78dc18f4e31d2bd90d5e5a45a4a
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570635"
---
# <a name="exception-thrown-and-not-caught"></a>Eccezione generata e non rilevata
È stata inclusa un' `throw` istruzione nel codice, ma non è stata inclusa in un blocco **try** oppure non è stato associato alcun blocco **catch** per intercettare l'errore. Le eccezioni vengono generate all'interno del blocco **try** utilizzando l'istruzione **throw** e rilevate all'esterno del blocco **try** con un'istruzione **catch** .  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Racchiudere il codice che può generare un'eccezione in un blocco **try** e verificare che sia presente un blocco **catch** corrispondente.  
  
- Verificare che l'istruzione catch preveda il formato corretto dell'eccezione.  
  
- Se l'eccezione viene generata nuovamente, verificare che sia presente un'altra istruzione catch corrispondente.  
  
## <a name="see-also"></a>Vedi anche  
 [Error (oggetto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)   
 [Istruzione throw](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/throw)   
 [prova... rileva... finally (istruzione)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)
