---
title: 'Errore: In modalità mista debug per i processi x64 è supportato solo quando si usa Microsoft .NET Framework 4 o versioni successive | Microsoft Docs'
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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1423cbcfcae53948f7b9c9cd52eb90f57251bc24
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697923"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Errore: il debug in modalità mista per i processi x64 è supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva
Per eseguire il debug di codice nativo e gestito misto in un processo a 64 bit, è necessario disporre di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] versione 4. Il debug in modalità mista dei processi a 64 bit con versioni di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] precedenti alla 4 non è supportato.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Effettuare uno dei passaggi indicati di seguito.

  - Aggiornare [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] alla versione 4.

  - Compilare una versione a 32 bit dell'applicazione per il debug.

## <a name="see-also"></a>Vedere anche
- [Remote Debugging](../debugger/remote-debugging.md)