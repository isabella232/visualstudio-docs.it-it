---
title: IDebugApplicationNode100::QueryIsChildNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugApplicationNode100::QueryIsChildNode
ms.assetid: 4f36f435-0f34-4f9e-bba3-e75285fd7bbb
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f8e3b722952ea2ab219ac513ed46d7753eaeb16
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54349179"
---
# <a name="idebugapplicationnode100queryischildnode"></a>IDebugApplicationNode100::QueryIsChildNode
Determina se il documento specificato appartiene a uno dei nodi figlio del nodo.  
  
> [!IMPORTANT]
>  [Interfaccia IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md) viene implementata da PDM v 10.0 e versioni successive. Rilevata in activdbg100.h.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT QueryIsChildNode(        [in] IDebugDocument* pSearchKey        );  
```  
  
#### <a name="parameters"></a>Parametri  
 `pSearchKey`  
 La chiave di ricerca.  
  
## <a name="see-also"></a>Vedere anche  
 [Interfaccia IDebugApplicationNode100](../../winscript/reference/idebugapplicationnode100-interface.md)