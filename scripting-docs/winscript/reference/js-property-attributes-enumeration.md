---
title: Enumerazione JS_PROPERTY_ATTRIBUTES | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_ATTRIBUTES
apilocation:
- jscript9diag.dll
ms.assetid: e83b9b6c-5b21-48d1-92b6-22bed926b18b
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 94a72228e1ad6ab49568f3291ad9add7209ef3da
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571741"
---
# <a name="js_property_attributes-enumeration"></a>Enumerazione JS_PROPERTY_ATTRIBUTES
Indica gli attributi di una proprietà.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
enum JS_PROPERTY_ATTRIBUTES{   JS_PROPERTY_ATTRIBUTE_NONE = 0,   JS_PROPERTY_HAS_CHILDREN = 0x1,   JS_PROPERTY_FAKE = 0x2,   JS_PROPERTY_METHOD = 0x4,   JS_PROPERTY_READONLY = 0x8,   JS_PROPERTY_NATIVE_WINRT_POINTER = 0x10} JS_PROPERTY_ATTRIBUTES;  
```  
  
## <a name="members"></a>Members  
  
|Name|Descrizione|  
|----------|-----------------|  
|`JS_PROPERTY_ATTRIBUTE_NONE`|La proprietà non contiene attributi.|  
|`JS_PROPERTY_HAS_CHILDREN`|La proprietà contiene figli.|  
|`JS_PROPERTY_FAKE`|La proprietà rappresenta un nodo fittizio, ad esempio "[Methods]".|  
|`JS_PROPERTY_METHOD`|La proprietà è un metodo.|  
|`JS_PROPERTY_READONLY`|La proprietà è in sola lettura.|  
|`JS_PROPERTY_NATIVE_WINRT_POINTER`|La proprietà è un puntatore a un oggetto WinRT nativo.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)