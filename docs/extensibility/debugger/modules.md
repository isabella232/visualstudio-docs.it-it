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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 91011c021c429c5f09556f749e305572097a8de6
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710333"
---
# <a name="modules"></a>Moduli
In termini di architettura del debugger, un *modulo*:

- Contenitore fisico di codice, ad esempio un file eseguibile o una DLL.

- Può ricaricare i simboli e descriversi. Le descrizioni dei moduli vengono visualizzate nella finestra Moduli dell'IDE.

- È rappresentato da [un'interfaccia IDebugModule2,](../../extensibility/debugger/reference/idebugmodule2.md) creata da un motore di debug per descrivere il modulo.

## <a name="see-also"></a>Vedi anche
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
