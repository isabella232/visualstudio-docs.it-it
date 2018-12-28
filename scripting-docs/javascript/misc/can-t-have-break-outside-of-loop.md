---
title: Impossibile utilizzare 'break' all'esterno del ciclo | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1019
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 11d02172-2a78-4705-a730-d21111db5f42
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ce142e07a47b73778ebae6b26452806b3a036d41
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/27/2018
ms.locfileid: "53802407"
---
# <a name="cant-have-break-outside-of-loop"></a>Impossibile utilizzare 'break' all'esterno di un ciclo
Si è provato a usare il **interruzione** (parola chiave) all'esterno di un ciclo. Il **INTERR** parola chiave viene usata per interrompere un ciclo o `switch` istruzione. Deve essere incorporato nel corpo di un ciclo o `switch` istruzione. Tuttavia, un **etichetta** possibile seguire la parola chiave break.  
  
```  
break labelname;  
```  
  
 È necessario solo il form con etichette del **break** parola chiave quando si utilizzano cicli annidati o `switch` istruzioni ed è necessario interrompere un ciclo che non corrisponde a quello più interno.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Assicurarsi che il **interruzione** (parola chiave) viene visualizzato all'interno di un'istruzione di ciclo o un commutatore di inclusione.  
  
## <a name="see-also"></a>Vedere anche  
 [Istruzione break](../../javascript/reference/break-statement-javascript.md)   
 [Controllo del flusso di programma](../../javascript/controlling-program-flow-javascript.md)   
 [Risoluzione dei problemi relativi agli script](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)