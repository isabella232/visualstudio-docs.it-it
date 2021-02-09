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
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9aa0aaf7e82287c1dc2e35c524798a3480d2573e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99926321"
---
# <a name="modules"></a>Moduli
In termini di architettura del debugger, un *modulo*:

- È un contenitore fisico di codice, ad esempio un file eseguibile o una DLL.

- Può ricaricare i simboli e descrivere se stesso. Le descrizioni dei moduli vengono visualizzate nella finestra moduli dell'IDE.

- È rappresentato da un'interfaccia [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) creata da un motore di debug per descrivere il modulo.

## <a name="see-also"></a>Vedi anche
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)
