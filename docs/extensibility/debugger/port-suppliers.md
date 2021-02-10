---
title: Fornitori di porte | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un fornitore di porte nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: b543770e5fcc920b05e5d19a15e312174ddad3dd
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99934390"
---
# <a name="port-suppliers"></a>Fornitori di porte
Nell'architettura del debugger, un *Fornitore di porte*:

- È contenuto in un server e fornisce le porte su richiesta al server.

- Consente di aggiungere e rimuovere porte dal server contenitore.

- Consente di enumerare tutte le porte fornite al server.

- È rappresentato da un'interfaccia [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , registrata con Visual Studio tramite il registro di sistema. Questa interfaccia può essere ottenuta chiamando [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce un fornitore di porta predefinito e una porta predefinita. Se è necessario implementare una porta personalizzata, è necessario implementare anche un fornitore di porte personalizzato per fornire tali porte personalizzate.

## <a name="see-also"></a>Vedi anche
- [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Ports](../../extensibility/debugger/ports.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
