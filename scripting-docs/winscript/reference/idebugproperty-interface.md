---
title: Interfaccia IDebugProperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- IDebugProperty interface
ms.assetid: 7e8f5341-23ef-4029-814d-f5c2307b9203
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2e5e5274e8a3d1c81ce010afc3893b27510a0fad
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/16/2019
ms.locfileid: "54348360"
---
# <a name="idebugproperty-interface"></a>Interfaccia IDebugProperty
Utilizzato per descrivere qualsiasi proprietà gerarchico dell'entità in fase di debug che ha un nome, tipo e valore. In genere, `IDebugProperty` viene usato per descrivere il risultato della valutazione dell'espressione, la valutazione di istruzione o register evaluation.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Nella tabella seguente sono illustrati i metodi del `IDebugProperty` interfaccia.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugProperty::GetPropertyInfo](../../winscript/reference/idebugproperty-getpropertyinfo.md)|Ottenere il `DebugPropertyInfo` che descrive il `IDebugProperty``.`|  
|[IDebugProperty::GetExtendedInfo](../../winscript/reference/idebugproperty-getextendedinfo.md)|Ottiene le informazioni su una proprietà estese.|  
|[IDebugProperty::SetValueAsString](../../winscript/reference/idebugproperty-setvalueasstring.md)|Imposta il valore di una proprietà da una stringa.|  
|[IDebugProperty::EnumMembers](../../winscript/reference/idebugproperty-enummembers.md)|Enumera i membri di una proprietà.|  
|[IDebugProperty::GetParent](../../winscript/reference/idebugproperty-getparent.md)|Ottiene l'elemento padre di una proprietà.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: dbgprop.h