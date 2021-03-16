---
description: È stato usato il blocco try per la gestione delle eccezioni, ma non è stata scritta l'istruzione catch associata.
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
ms.openlocfilehash: b5cf6087ff5a299c575ac4f2cd5eb8a3e206b7e0
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103571038"
---
# <a name="expected-catch"></a>Previsto 'catch'
È stato usato il blocco **try** per la gestione delle eccezioni, ma non è stata scritta l'istruzione **catch** associata. Il meccanismo di gestione delle eccezioni richiede che il codice che può avere esito negativo, insieme al codice che non deve essere eseguito se si verifica un'eccezione, venga incapsulato all'interno di un blocco **try** . Le eccezioni vengono generate all'interno del blocco **try** utilizzando l'istruzione **throw** e rilevate all'esterno del blocco **try** con una o più istruzioni **catch** .  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere il blocco **catch** associato.  
  
- Provare a usare un blocco **finally** anziché un blocco **catch** .  
  
## <a name="see-also"></a>Vedi anche  
 [prova... rileva... finally (istruzione)](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Statements/try...catch)   
 [Oggetto Error](https://developer.mozilla.org/docs/Web/JavaScript/Reference/Global_Objects/Error)
