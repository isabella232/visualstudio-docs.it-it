---
title: Il debug in modalità mista per i processi IA64 non è supportato | Microsoft Docs
ms.date: 11/04/2016
ms.topic: error-reference
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
ms.openlocfilehash: 5bc0fe09078493814d1ff12108ccdada36e8da1f
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852628"
---
# <a name="error-mixed-mode-debugging-for-ia64-processes-is-unsupported"></a>Errore: il debug in modalità mista per i processi IA64 non è supportato
Il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] non supporta il debug di codice nativo e gestito misto in un processo basato su Itanium.

### <a name="to-correct-this-error"></a>Per correggere l'errore

- Compilare una versione a 32 bit dell'applicazione per il debug.

## <a name="see-also"></a>Vedere anche
- [Debug remoto](../debugger/remote-debugging.md)