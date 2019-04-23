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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 5c4414651249aa7622e7f7be59e6150a4925f1b8
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60089341"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Errore: Il debug in modalità mista per i processi IA64 non è supportato
Il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non supporta il debug di codice nativo e gestito misto in un processo basato su Itanium.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Compilare una versione a 32 bit dell'applicazione per il debug.

## <a name="see-also"></a>Vedere anche
- [Remote Debugging](../debugger/remote-debugging.md)