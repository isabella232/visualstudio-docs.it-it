---
title: IDebugApplicationNode100 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100 Interface
ms.assetid: 43966d4e-5f89-4a04-a08d-782347d00c2d
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4a6cbe92c6789b702adc69f598a995f84c01ef86
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54347455"
---
# <a name="idebugapplicationnode100-interface"></a>Interfaccia IDebugApplicationNode100
Il `IDebugApplicationNode100` interfaccia estende la funzionalità del [interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md). È possibile ottenere un'istanza di questa interfaccia chiamando QueryInterface sull'implementazione di [interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
>  Questa interfaccia viene implementata da PDM v 10.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IDebugApplicationNode100` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Ottiene i documenti di testo che sono nascoste per il filtro specificato.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Determina se il documento specificato appartiene a uno dei nodi figlio del nodo.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Imposta il filtro in una determinata [interfaccia IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementazione. Consente ai debugger di script di filtrare i nodi di applicazione generati dal compilatore figlio in modo da PDM non invierà più gli eventi quando i nodi vengono creati o rimosse. Per impostazione predefinita, verranno inviati tutti i nodi.|