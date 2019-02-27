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
ms.openlocfilehash: 4a25f72fccfd072243d6d0fdfd1d311c1a3bb6f4
ms.sourcegitcommit: 23feea519c47e77b5685fec86c4bbd00d22054e3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/26/2019
ms.locfileid: "56841450"
---
# <a name="expected-catch"></a>Previsto 'catch'
È stato usato la gestione delle eccezioni **provare** blocca, ma non scritto personalmente associato **catch** istruzione. Meccanismo di gestione delle eccezioni richiede che il codice può avere esito negativo, oltre al codice che non deve essere eseguita se si verifica un'eccezione, essere incapsulati all'interno di un **provare** blocco. Le eccezioni generate dall'interno la **provare** bloccato tramite il **throw** istruzione e rilevata di fuori il **provare** blocco con uno o più **catch**le istruzioni.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere l'oggetto associato **catch** blocco.  
  
-   Provare a usare una **infine** block invece di un **catch** blocco.  
  
## <a name="see-also"></a>Vedere anche  
 [try... catch... finally istruzione](../../javascript/reference/try-dot-dot-dot-catch-dot-dot-dot-finally-statement-javascript.md)   
 [Oggetto Error](../../javascript/reference/error-object-javascript.md)