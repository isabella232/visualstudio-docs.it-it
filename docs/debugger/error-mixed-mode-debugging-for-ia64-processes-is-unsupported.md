---
title: 'Errore: Debug in modalità mista per i processi IA64 non è supportato | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_ia64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 56df416b7142e0ff9f7e96b8c1b2cba6e73b65a9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53916780"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Errore: Il debug in modalità mista per i processi IA64 non è supportato
Il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non supporta il debug di codice nativo e gestito misto in un processo basato su Itanium.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
-   Compilare una versione a 32 bit dell'applicazione per il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Remote Debugging](../debugger/remote-debugging.md)