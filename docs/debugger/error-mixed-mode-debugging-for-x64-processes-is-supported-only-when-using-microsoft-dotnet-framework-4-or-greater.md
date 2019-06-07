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
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 9ef0daf5fd28bd829edcdce412839b03ed8347bf
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66745431"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Errore: Il debug in modalità mista per i processi x64 è supportato solo quando si esegue una versione di Microsoft .NET Framework precedente alla 4
Per eseguire il debug di codice nativo e gestito misto in un processo a 64 bit, è necessario disporre di .NET Framework versione 4. Debug in modalità mista di processi a 64 bit con le versioni di .NET Framework precedenti alla 4 non è supportato.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Effettuare uno dei passaggi indicati di seguito.

  - Eseguire l'aggiornamento alla versione 4 di .NET Framework.

  - Compilare una versione a 32 bit dell'applicazione per il debug.

## <a name="see-also"></a>Vedere anche
- [Remote Debugging](../debugger/remote-debugging.md)