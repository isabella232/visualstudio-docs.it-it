---
title: IDebugApplicationNode100::SetFilterForEventSink | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::SetFilterForEventSink
ms.assetid: cfb34efe-c6e1-4692-8ffd-3ede3a24cd4b
caps.latest.revision: 5
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b273b770a1d82edbf5bbbe26c0865060234b852
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54346488"
---
# <a name="idebugapplicationnode100setfilterforeventsink"></a>IDebugApplicationNode100::SetFilterForEventSink
Imposta il filtro in una determinata [interfaccia IDebugApplicationNodeEvents](../../winscript/reference/idebugapplicationnodeevents-interface.md) implementazione. Consente ai debugger di script di filtrare i nodi di applicazione generati dal compilatore figlio in modo da PDM non invierà più gli eventi quando questi vengono creati o rimosse. Per impostazione predefinita, verranno inviati tutti i nodi.  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) viene implementata da PDM v 10.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT SetFilterForEventSink(        [in] DWORD dwCookie,        [in] APPLICATION_NODE_EVENT_FILTER filter        );  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwCookie`  
 Il cookie del filtro.  
  
 `filter`  
 Filtro.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)