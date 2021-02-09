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
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: 01f8bf0b018ed5dd91cedcc221a037f3502815e7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99871494"
---
# <a name="error-mixed-mode-debugging-for-x64-processes-is-supported-only-when-using-microsoft-net-framework-4-or-greater"></a>Errore: il debug in modalità mista per i processi x64 è supportato solo quando si utilizza Microsoft .NET Framework 4 o versione successiva
Per eseguire il debug di codice nativo e gestito misto in un processo a 64 bit, è necessario avere .NET Framework versione 4. Il debug in modalità mista di processi a 64 bit con versioni .NET Framework precedenti a 4 non è supportato.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Effettuare uno dei passaggi indicati di seguito.

  - Aggiornare il .NET Framework alla versione 4.

  - Compilare una versione a 32 bit dell'applicazione per il debug.

## <a name="see-also"></a>Vedi anche
- [Debug remoto](../debugger/remote-debugging.md)