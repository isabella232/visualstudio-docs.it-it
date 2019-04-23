---
title: Previsto 'catch' | Microsoft Docs
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
ms.openlocfilehash: 941d49a530b14e2af64ddcb599dd775feb347de0
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60053228"
---
# <a name="expected-catch"></a>Previsto 'catch'
È stato usato la gestione delle eccezioni **provare** blocca, ma non scritto personalmente associato **catch** istruzione. Meccanismo di gestione delle eccezioni richiede che il codice può avere esito negativo, oltre al codice che non deve essere eseguita se si verifica un'eccezione, essere incapsulati all'interno di un **provare** blocco. Le eccezioni generate dall'interno la **provare** bloccato tramite il **throw** istruzione e rilevata di fuori il **provare** blocco con uno o più **catch**le istruzioni.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere l'oggetto associato **catch** blocco.  
  
- Provare a usare una **infine** block invece di un **catch** blocco.  
  
## <a name="see-also"></a>Vedere anche  
 [try... catch... finally istruzione](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)