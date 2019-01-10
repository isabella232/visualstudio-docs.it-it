---
title: 'Errore: Modalità mista di debug per i processi x64 è supportato solo quando si usa Microsoft .NET Framework 4 o versione successiva | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: troubleshooting
f1_keywords:
- vs.debug.error.interop_unsupported_x64
dev_langs:
- CSharp
- VB
- FSharp
- C++
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 4098689338d0c0c647964e4d13e59ab860e42e4c
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53827404"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Errore: Il debug in modalità mista per i processi x64 è supportato solo quando si esegue una versione di Microsoft .NET Framework precedente alla 4
Per eseguire il debug di codice nativo e gestito misto in un processo a 64 bit, è necessario disporre di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versione 4. Il debug in modalità mista dei processi a 64 bit con versioni di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] precedenti alla 4 non è supportato.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
- Effettuare uno dei passaggi indicati di seguito.  
  
  - Aggiornare [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] alla versione 4.  
  
  - Compilare una versione a 32 bit dell'applicazione per il debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Remote Debugging](../debugger/remote-debugging.md)