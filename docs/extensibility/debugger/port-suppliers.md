---
title: Port Suppliers | Microsoft Docs
description: Questo articolo descrive la definizione e il ruolo di un fornitore di porte nell'architettura del debugger in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 098e1546dea997f83f0c73b5d337657b1a8d77a8
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710324"
---
# <a name="port-suppliers"></a>Fornitori di porte
Nell'architettura del debugger, un *fornitore di porte:*

- È contenuto da un server e fornisce le porte su richiesta a tale server.

- Può aggiungere e rimuovere porte dal server contenitore.

- Può enumerare tutte le porte fornite al server.

- È rappresentato da [un'interfaccia IDebugPortSupplier2,](../../extensibility/debugger/reference/idebugportsupplier2.md) registrata con Visual Studio tramite il Registro di sistema. Questa interfaccia può essere ottenuta chiamando [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).

  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce un fornitore di porte predefinito e una porta predefinita. Se deve essere implementata una porta personalizzata, deve essere implementato anche un fornitore di porte personalizzato per fornire tali porte personalizzate.

## <a name="see-also"></a>Vedi anche
- [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)
- [Ports](../../extensibility/debugger/ports.md)
- [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)
- [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)
- [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
