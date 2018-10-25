---
title: Compilazione condizionale disattivata | Microsoft Docs
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
- VS.WebClient.Help.SCRIPT1030
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 59a030b0-a6c6-47f2-b90e-c0ed204d5116
caps.latest.revision: 9
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8f2eabb900e24072c8f390061b5d6081de9bc889
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49914242"
---
# <a name="conditional-compilation-is-turned-off"></a>Compilazione condizionale disattivata
Si è provato a usare una variabile di compilazione condizionale senza prima compilazione condizionale di attivazione in. Attivare la compilazione condizionale indica il [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] compilatore a interpretare gli indicatori che iniziano con come variabili di compilazione condizionale. È possibile anteporre al codice con l'istruzione condizionale:  
  
```  
/*@cc_on @*/  
```  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Aggiungere l'istruzione seguente all'inizio del codice condizionale:  
  
    ```JavaScript  
    /*@cc_on @*/  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [@cc_on Istruzione](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [@if Istruzione](../../javascript/reference/at-if-statement-javascript.md)   
 [Istruzione @set](../../javascript/reference/at-set-statement-javascript.md)