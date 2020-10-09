---
title: Previsto ' Catch ' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 47411a6376cd843b3a12cf74ed1800775b98cd83
ms.sourcegitcommit: e38419bb842d587fd9e37c24b6cf3fc5c2e74817
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/09/2020
ms.locfileid: "91861960"
---
# <a name="expected-catch"></a>Previsto 'catch'
È stato usato il blocco **try** per la gestione delle eccezioni, ma non è stata scritta l'istruzione **catch** associata. Il meccanismo di gestione delle eccezioni richiede che il codice che può avere esito negativo, insieme al codice che non deve essere eseguito se si verifica un'eccezione, venga incapsulato all'interno di un blocco **try** . Le eccezioni vengono generate all'interno del blocco **try** utilizzando l'istruzione **throw** e rilevate all'esterno del blocco **try** con una o più istruzioni **catch** .  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere il blocco **catch** associato.  
  
- Provare a usare un blocco **finally** anziché un blocco **catch** .  
  
## <a name="see-also"></a>Vedere anche  
 [prova... rileva... finally (istruzione)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)   
 [Error (oggetto)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)