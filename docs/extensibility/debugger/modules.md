---
title: I moduli | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1f31e3760a0697be8c9fc80eb811c99df79d32b1
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56718911"
---
# <a name="modules"></a>Moduli
In termini di architettura del debugger, un *modulo*:

-   È un contenitore fisico di codice, ad esempio un file eseguibile o una DLL.

-   Può ricaricare i simboli e descrivere se stesso. Descrizioni dei moduli vengono visualizzati nella finestra moduli dell'IDE.

-   È rappresentato da un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfaccia, creato da un motore di debug per descrivere il modulo.

## <a name="see-also"></a>Vedere anche
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)