---
title: IDebugApplicationNode100 Interface | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: d8de6f57cabe808df1506870fe65da31ef74e644
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63436027"
---
# <a name="idebugapplicationnode100-interface"></a>Interfaccia IDebugApplicationNode100
Il `IDebugApplicationNode100` interfaccia estende la funzionalità del [interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md). È possibile ottenere un'istanza di questa interfaccia chiamando QueryInterface sull'implementazione di [interfaccia IDebugApplicationNode](../../winscript/reference/idebugapplicationnode-interface.md).  
  
> [!IMPORTANT]
> Questa interfaccia viene implementata da PDM v 10.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="methods"></a>Metodi  
 L'interfaccia `IDebugApplicationNode100` espone i metodi riportati di seguito.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugApplicationNode100::GetExcludedDocuments](../../winscript/reference/idebugapplicationnode100-getexcludeddocuments.md)|Ottiene i documenti di testo che sono nascoste per il filtro specificato.|  
|[IDebugApplicationNode100::QueryIsChildNode](../../winscript/reference/idebugapplicationnode100-queryischildnode.md)|Determina se il documento specificato appartiene a uno dei nodi figlio del nodo.|  
|[IDebugApplicationNode100::SetFilterForEventSink](../../winscript/reference/idebugapplicationnode100-setfilterforeventsink.md)|Imposta il filtro in una determinata [interfaccia IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementazione. Consente ai debugger di script di filtrare i nodi di applicazione generati dal compilatore figlio in modo da PDM non invierà più gli eventi quando i nodi vengono creati o rimosse. Per impostazione predefinita, verranno inviati tutti i nodi.|