---
title: Server (Visual Studio SDK) | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un server nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b7bb19262d4ce5fd1b3139f05cd9bbc57131db1c
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105070362"
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
Nell'architettura del debugger, un *Server*:

- È un contenitore di porte e fornitori di porte e comunica porte e fornitori di porte al gestore di debug della sessione (SDM) e ai motori di debug.

- Può identificare se stesso in base al nome ed enumerare le porte e i fornitori di porte.

- È rappresentato da un'interfaccia [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) , che viene implementata solo da Visual Studio (un'istanza di un server per ogni istanza di Visual Studio in esecuzione).

## <a name="see-also"></a>Vedi anche
- [Ports](../../extensibility/debugger/ports.md)
- [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
