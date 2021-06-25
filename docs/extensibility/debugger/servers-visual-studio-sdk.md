---
title: Server (Visual Studio SDK) | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un server nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 99f6c634053df9191ac419c8ee450dc99cf62c7c
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902124"
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
Nell'architettura del debugger, *un server*:

- È un contenitore di porte e fornitori di porte e comunica le porte e i fornitori di porte al gestore di debug della sessione (SDM) e ai motori di debug.

- Può identificarsi in base al nome ed enumerare le porte e i fornitori di porte.

- È rappresentato da [un'interfaccia IDebugCoreServer2,](../../extensibility/debugger/reference/idebugcoreserver2.md) implementata solo da Visual Studio (un'istanza di un server per ogni istanza di Visual Studio in esecuzione).

## <a name="see-also"></a>Vedere anche
- [Ports](../../extensibility/debugger/ports.md)
- [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)
