---
title: Moduli | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un modulo nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 03a3ad588b0a2e0f3aa6f04ddeb742ab66064bc9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902605"
---
# <a name="modules"></a>Moduli
In termini di architettura del debugger, un *modulo*:

- Contenitore fisico di codice, ad esempio un file eseguibile o una DLL.

- Può ricaricare i simboli e descriversi. Le descrizioni dei moduli vengono visualizzate nella finestra Moduli dell'IDE.

- È rappresentato da [un'interfaccia IDebugModule2,](../../extensibility/debugger/reference/idebugmodule2.md) creata da un motore di debug per descrivere il modulo.

## <a name="see-also"></a>Vedere anche
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
