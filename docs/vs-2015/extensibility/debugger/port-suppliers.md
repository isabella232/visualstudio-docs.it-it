---
title: Porta Suppliers | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3be95dfdb84f373730d087e9d6da1096891770af
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528743"
---
# <a name="port-suppliers"></a>Fornitori di porte
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [fornitori di porte](https://docs.microsoft.com/visualstudio/extensibility/debugger/port-suppliers).  
  
In termini di architettura del debugger, un **fornitore della porta**:  
  
-   È contenuta da un server e fornisce le porte su richiesta a tale server.  
  
-   Puoi aggiungere e rimuovere le porte dal server che lo contiene.  
  
-   Possibile enumerare tutte le porte che è fornito per il server.  
  
-   È rappresentato da un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaccia, che è stato registrato con Visual Studio tramite il Registro di sistema. Questa interfaccia può essere ottenuta chiamando [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] fornisce un fornitore di porte predefinita e una porta predefinita. Se una porta personalizzata deve essere implementata, un fornitore di porte personalizzato deve inoltre essere implementati per fornire tali porte personalizzate.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Porte](../../extensibility/debugger/ports.md)   
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)

