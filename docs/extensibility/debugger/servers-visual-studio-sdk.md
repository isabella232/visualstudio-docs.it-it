---
title: Server (Visual Studio SDK) Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 32fdbb5afca40c3b4fced468d2f9ef0ea5226c00
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712889"
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
Nell'architettura del debugger, un *server*:

- È un contenitore di porte e fornitori di porte e comunica porte e fornitori di porte al gestore di sessione di debug (SDM) e ai motori di debug.

- Può identificarsi in base al nome ed enumerare le porte e i fornitori di porte.

- È rappresentato da un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia, che viene implementata solo da Visual Studio (un'istanza di un server per ogni istanza di Visual Studio in esecuzione).

## <a name="see-also"></a>Vedere anche
- [Ports](../../extensibility/debugger/ports.md)
- [Fornitori portuali](../../extensibility/debugger/port-suppliers.md)
- [Concetti del debuggerDebugger concepts](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
