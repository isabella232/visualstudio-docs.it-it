---
title: Servers (Visual Studio SDK) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f2e5b50a3f2969f8f22ce938522526a6010c640a
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56691384"
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
Nell'architettura di debugger, un *server*:

-   È un contenitore delle porte e fornitori di porte e comunica le porte e fornitori di porte per la gestione del debug sessione (SDM) e motori di debug.

-   Può identificarsi in base al nome ed enumerare le porte e i fornitori di porte.

-   È rappresentato da un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia, che viene implementato solo da Visual Studio (un'istanza di un server per ogni istanza di esecuzione di Visual Studio).

## <a name="see-also"></a>Vedere anche
- [Porte](../../extensibility/debugger/ports.md)
- [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)