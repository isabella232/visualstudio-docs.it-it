---
title: Fornitori di porte | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e90871927c30399dea4691381baa749db2b3e8bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153711"
---
# <a name="port-suppliers"></a>Fornitori di porte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

In termini di architettura del debugger, un **Fornitore di porte**:  
  
- È contenuto in un server e fornisce le porte su richiesta al server.  
  
- Consente di aggiungere e rimuovere porte dal server contenitore.  
  
- Consente di enumerare tutte le porte fornite al server.  
  
- È rappresentato da un'interfaccia [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , registrata con Visual Studio tramite il registro di sistema. Questa interfaccia può essere ottenuta chiamando [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
  [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornisce un fornitore di porta predefinito e una porta predefinita. Se è necessario implementare una porta personalizzata, è necessario implementare anche un fornitore di porte personalizzato per fornire tali porte personalizzate.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Porte](../../extensibility/debugger/ports.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
