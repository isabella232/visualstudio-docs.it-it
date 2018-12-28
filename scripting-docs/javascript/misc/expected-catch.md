---
title: Previsto 'catch' | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1033
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: f1cd947f-eba2-411e-8e84-8ca86f608643
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 244635605abafc5c0bd22c5203b105aa6e7dc669
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2018
ms.locfileid: "53801982"
---
# <a name="expected-catch"></a>Previsto 'catch'
È stato usato la gestione delle eccezioni **provare** blocca, ma non scritto personalmente associato **catch** istruzione. Meccanismo di gestione delle eccezioni richiede che il codice può avere esito negativo, oltre al codice che non deve essere eseguita se si verifica un'eccezione, essere incapsulati all'interno di un **provare** blocco. Le eccezioni generate dall'interno la **provare** bloccato tramite il **throw** istruzione e rilevata di fuori il **provare** blocco con uno o più **catch**le istruzioni.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere l'oggetto associato **catch** blocco.  
  
-   Provare a usare una **infine** block invece di un **catch** blocco.  
  
## <a name="see-also"></a>Vedere anche  
 [try... catch... finally istruzione](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)