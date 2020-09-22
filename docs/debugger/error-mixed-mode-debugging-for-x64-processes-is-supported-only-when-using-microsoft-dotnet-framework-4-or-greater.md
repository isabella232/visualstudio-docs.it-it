---
title: Il debug in modalità mista per i processi x64 è supportato solo quando si usa Microsoft .NET Framework 4 o versione successiva | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: e8cfc3ac5cb606637fe5c2818750168a239a46fa
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852615"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Errore: il debug in modalità mista per i processi x64 è supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva
Per eseguire il debug di codice nativo e gestito misto in un processo a 64 bit, è necessario avere .NET Framework versione 4. Il debug in modalità mista di processi a 64 bit con versioni .NET Framework precedenti a 4 non è supportato.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Effettuare uno dei passaggi indicati di seguito.

  - Aggiornare il .NET Framework alla versione 4.

  - Compilare una versione a 32 bit dell'applicazione per il debug.

## <a name="see-also"></a>Vedere anche
- [Debug remoto](../debugger/remote-debugging.md)