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
ms.openlocfilehash: 05a9e4f51d5daf7a9e1b1153acbbe8b76b539b72
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572864"
---
# <a name="exception-thrown-and-not-caught"></a>Eccezione generata e non rilevata
È stata inclusa un'istruzione `throw` nel codice, ma non è stata inclusa in un blocco **try** oppure non è disponibile alcun blocco **catch** associato per intercettare l'errore. Le eccezioni vengono generate all'interno del blocco **try** utilizzando l'istruzione **throw** e rilevate all'esterno del blocco **try** con un'istruzione **catch** .  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Racchiudere il codice che può generare un'eccezione in un blocco **try** e verificare che sia presente un blocco **catch** corrispondente.  
  
- Verificare che l'istruzione catch preveda il formato corretto dell'eccezione.  
  
- Se l'eccezione viene generata nuovamente, verificare che sia presente un'altra istruzione catch corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
   [oggetto errore](../../javascript/reference/error-object-javascript.md)  
 [istruzione throw](../../javascript/reference/throw-statement-javascript.md)   
 [Istruzione try...catch...finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)