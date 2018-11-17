---
title: Non è possibile modificare la finestra di dialogo valore | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
caps.latest.revision: 12
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 19ef7640939ba1ad9a22dcf519636c64df011394
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51782401"
---
# <a name="cannot-change-value-dialog-box"></a>Impossibile modificare il valore (finestra di dialogo)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Error  
 `The value of this variable cannot be changed` &#124;`The name` *name* `does not exist in the current context` &#124; *vari altri messaggi*  
  
 Questa finestra di messaggio viene visualizzata quando si tenta di modificare il contenuto di una variabile in un valore non consentito in una finestra del debugger (finestre Auto, Espressioni di controllo o Variabili locali) o nella finestra di dialogo Controllo immediato. Se, ad esempio, si tenta di impostare il valore di una variabile Integer in una stringa di caratteri, viene visualizzata questa finestra di messaggio.  
  
## <a name="solution"></a>Soluzione  
 Assicurarsi che l'input digitato nella finestra del debugger o nella finestra di dialogo Controllo immediato rappresenti un valore consentito per la variabile che si sta tentando di impostare.  
  
## <a name="see-also"></a>Vedere anche  
 [Espressioni nel debugger](../debugger/expressions-in-the-debugger.md)



