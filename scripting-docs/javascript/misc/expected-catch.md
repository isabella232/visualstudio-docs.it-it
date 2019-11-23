---
title: Previsto ' Catch ' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: reference
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
ms.openlocfilehash: 8cad981e4ba469f67645aca601e6b58c18e1fab6
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573435"
---
# <a name="expected-catch"></a>Previsto 'catch'
È stato usato il blocco **try** per la gestione delle eccezioni, ma non è stata scritta l'istruzione **catch** associata. Il meccanismo di gestione delle eccezioni richiede che il codice che può avere esito negativo, insieme al codice che non deve essere eseguito se si verifica un'eccezione, venga incapsulato all'interno di un blocco **try** . Le eccezioni vengono generate all'interno del blocco **try** utilizzando l'istruzione **throw** e rilevate all'esterno del blocco **try** con una o più istruzioni **catch** .  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere il blocco **catch** associato.  
  
- Provare a usare un blocco **finally** anziché un blocco **catch** .  
  
## <a name="see-also"></a>Vedere anche  
 [prova... rileva...  istruzione finally](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)  
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)