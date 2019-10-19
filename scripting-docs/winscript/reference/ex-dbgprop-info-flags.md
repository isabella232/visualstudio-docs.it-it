---
title: EX_DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- EX_DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
helpviewer_keywords:
- EX_DBGPROP_INFO_FLAGS
ms.assetid: ee309dfe-9432-4dff-8756-7a8d677f9dcc
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0094d49a7e528d312dc8206b02599651f192c6fb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575849"
---
# <a name="ex_dbgprop_info_flags"></a>EX_DBGPROP_INFO_FLAGS
Utilizzato per specificare i campi `ExtendedDebugPropertyInfo`.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
enum {  
   EX_DBGPROP_INFO_ID  =0x0100,  
   EX_DBGPROP_INFO_NTYPE  =0x0200,  
   EX_DBGPROP_INFO_NVALUE  =0x0400,  
   EX_DBGPROP_INFO_LOCKBYTES  =0x0800,  
   EX_DBGPROP_INFO_DEBUGEXTPROP  =0x1000  
};  
```  
  
## <a name="members"></a>Members  
 EX_DBGPROP_INFO_ID  
 Inizializza l'identificatore per la proprietà.  
  
 EX_DBGPROP_INFO_NTYPE  
 Inizializza il tipo della proprietà.  
  
 EX_DBGPROP_INFO_NVALUE  
 Inizializza il valore della proprietà.  
  
 EX_DBGPROP_INFO_LOCKBYTES  
 Inizializza il campo `plb`.  
  
 EX_DBGPROP_INFO_DEBUGEXTPROP  
 Inizializza il campo `pDebugExtProp` che contiene un'interfaccia `IDebugExtendedProperty`.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 della [struttura ExtendedDebugPropertyInfo](../../winscript/reference/extendeddebugpropertyinfo-structure.md)  
 [Interfaccia IDebugExtendedProperty](../../winscript/reference/idebugextendedproperty-interface.md)