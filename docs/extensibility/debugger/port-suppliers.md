---
title: Porta Suppliers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 5385e006bcd2f79ab7b1c2e723e696b833991f36
ms.sourcegitcommit: 71b307ce86c4079cc7ad686d8d5f96a6a123aadd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/25/2018
ms.locfileid: "39252349"
---
# <a name="port-suppliers"></a>Fornitori di porte
Nell'architettura di debugger, un *fornitore della porta*:  
  
-   È contenuta da un server e fornisce le porte su richiesta a tale server.  
  
-   Puoi aggiungere e rimuovere le porte dal server che lo contiene.  
  
-   Possibile enumerare tutte le porte che è fornito per il server.  
  
-   È rappresentato da un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaccia, che è stato registrato con Visual Studio tramite il Registro di sistema. Questa interfaccia può essere ottenuta chiamando [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce un fornitore di porte predefinita e una porta predefinita. Se una porta personalizzata deve essere implementata, un fornitore di porte personalizzato deve inoltre essere implementati per fornire tali porte personalizzate.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Porte](../../extensibility/debugger/ports.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)