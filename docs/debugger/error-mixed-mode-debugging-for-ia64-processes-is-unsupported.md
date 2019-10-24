---
title: 'Errore: il debug in modalità mista per i processi IA64 non è supportato | Microsoft Docs'
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
ms.openlocfilehash: 0bddbb1572bd0258eae2052eb34dfa3d0d67a134
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72737630"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Errore: il debug in modalità mista per i processi IA64 non è supportato
Il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non supporta il debug di codice nativo e gestito misto in un processo basato su Itanium.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Compilare una versione a 32 bit dell'applicazione per il debug.

## <a name="see-also"></a>Vedere anche
- [Remote Debugging](../debugger/remote-debugging.md)