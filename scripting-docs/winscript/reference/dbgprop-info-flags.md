---
title: DBGPROP_INFO_FLAGS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- DBGPROP_INFO_FLAGS
apilocation:
- scrobj.dll
f1_keywords:
- DBGPROP_INFO_FLAGS
helpviewer_keywords:
- DBGPROP_INFO_FLAGS
ms.assetid: e9450a21-a802-4c3e-8b3d-8e202f555de1
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b8131531292e0f88108942648073883050dd609
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72572587"
---
# <a name="dbgprop_info_flags"></a>DBGPROP_INFO_FLAGS
Utilizzato per specificare `DebugPropertyInfo` campi  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
enum {  
   DBGPROP_INFO_NAME  =0x001,  
   DBGPROP_INFO_TYPE  =0x002,  
   DBGPROP_INFO_VALUE  =0x004,  
   DBGPROP_INFO_FULLNAME  =0x020,  
   DBGPROP_INFO_ATTRIBUTES  =0x008,  
   DBGPROP_INFO_DEBUGPROP  =0x010,  
   DBGPROP_INFO_AUTOEXPAND  =0x8000000  
};  
```  
  
## <a name="members"></a>Members  
 DBGPROP_INFO_NAME  
 Inizializza il campo `bstrName`.  
  
 DBGPROP_INFO_TYPE  
 Inizializza il campo `bstrType`.  
  
 DBGPROP_INFO_VALUE  
 Inizializza il campo `bstrValue`.  
  
 DBGPROP_INFO_FULLNAME  
 Inizializza il campo `bstrFullName`.  
  
 DBGPROP_INFO_ATTRIBUTES  
 Inizializza il campo `dwAttrib`.  
  
 DBGPROP_INFO_DEBUGPROP  
 Inizializza il campo `pDebugProp` che contiene un'interfaccia `IDebugProperty`.  
  
 DBGPROP_INFO_AUTOEXPAND  
 Specifica che il campo del valore deve contenere il valore espanso automaticamente, se disponibile, per questo tipo di oggetto.  
  
## <a name="see-also"></a>Vedere anche  
 @No__t_1 della [struttura DebugPropertyInfo](../../winscript/reference/debugpropertyinfo-structure.md)  
 [Interfaccia IDebugProperty](../../winscript/reference/idebugproperty-interface.md)