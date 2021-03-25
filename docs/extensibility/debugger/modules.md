---
title: Moduli | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un modulo nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f40cb7d0c65822fcb6ba4d4ca0132147f62d9286
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105054764"
---
# <a name="modules"></a>Moduli
In termini di architettura del debugger, un *modulo*:

- È un contenitore fisico di codice, ad esempio un file eseguibile o una DLL.

- Può ricaricare i simboli e descrivere se stesso. Le descrizioni dei moduli vengono visualizzate nella finestra moduli dell'IDE.

- È rappresentato da un'interfaccia [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) creata da un motore di debug per descrivere il modulo.

## <a name="see-also"></a>Vedi anche
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
