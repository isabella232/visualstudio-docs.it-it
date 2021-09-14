---
title: Finestra di dialogo Non è possibile modificare il valore | Microsoft Docs
description: Esaminare la finestra di dialogo Non è possibile modificare il valore, visualizzata in Visual Studio se si tenta di modificare una variabile in un valore non valido in una finestra del debugger o in Un controllo immediato.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.debug.variables.failededit
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Cannot Change Value dialog box
- variables [debugger], editing
ms.assetid: 19e930c2-5fbf-4c83-aae8-a1dc3f8fcae8
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: dcdb605421c1e18b6a27e5d93999dc6e3d2320f8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126630924"
---
# <a name="cannot-change-value-dialog-box"></a>Impossibile modificare il valore (finestra di dialogo)
## <a name="error"></a>Errore
 `The value of this variable cannot be changed` &#124; `The name` *nome* `does not exist in the current context` &#124; altri *messaggi*

 Questa finestra di messaggio viene visualizzata quando si tenta di modificare il contenuto di una variabile in un valore non consentito in una finestra del debugger (finestre Auto, Espressioni di controllo o Variabili locali) o nella finestra di dialogo Controllo immediato. Se, ad esempio, si tenta di impostare il valore di una variabile Integer in una stringa di caratteri, viene visualizzata questa finestra di messaggio.

## <a name="solution"></a>Soluzione
 Assicurarsi che l'input digitato nella finestra del debugger o nella finestra di dialogo Controllo immediato rappresenti un valore consentito per la variabile che si sta tentando di impostare.

## <a name="see-also"></a>Vedi anche

- [Espressioni nel debugger](../debugger/expressions-in-the-debugger.md)