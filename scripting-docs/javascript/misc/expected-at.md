---
description: Si è provato a creare una variabile da usare con le istruzioni di compilazione condizionale usando l' @set istruzione, ma non è stato inserito un simbolo di chiocciola @ prima del nome della variabile.
title: Previsto ' @' | Microsoft Docs
ms.date: 01/18/2017
ms.prod: visual-studio-windows
ms.technology: vs-javascript
ms.topic: error-reference
f1_keywords:
- VS.WebClient.Help.SCRIPT1032
dev_langs:
- JavaScript
- TypeScript
- DHTML
ms.assetid: 82ff8b74-1710-4358-9a26-dc92ab29c53b
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e7aa02ed1e436c92014d44e57f2c71ff7db5f99b
ms.sourcegitcommit: 691d2a47f92f991241fdb132a82c53a537198d50
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2021
ms.locfileid: "103570622"
---
# <a name="expected-"></a>Previsto '\@'
Si è provato a creare una variabile da usare con le istruzioni di compilazione condizionale usando l' `@set` istruzione, ma non è stato inserito un simbolo di chiocciola " **@** " prima del nome della variabile.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Aggiungere un simbolo di chiocciola " **@** " immediatamente prima del nome della variabile. Ad esempio:  
  
    ```JavaScript  
    @set @myvar = 1  
    ```  
  
## <a name="see-also"></a>Vedere anche  
 [@set Istruzione](https://developer.mozilla.org/docs/Archive/Web/JavaScript/Microsoft_Extensions/at-set)   
 [Compilazione condizionale](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/121hztk3(v=vs.84))   
 [Variabili di compilazione condizionale](/previous-versions/windows/internet-explorer/ie-developer/scripting-articles/s59bkzce(v=vs.84))
