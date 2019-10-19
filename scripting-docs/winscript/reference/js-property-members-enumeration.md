---
title: Enumerazione JS_PROPERTY_MEMBERS | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- JS_PROPERTY_MEMBERS
apilocation:
- jscript9diag.dll
ms.assetid: 3b870e5c-5518-4073-8384-f0c9c1777d9e
caps.latest.revision: 6
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3645e95859e2c2b785e01c7ee9a3cbee8155138d
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571724"
---
# <a name="js_property_members-enumeration"></a>Enumerazione JS_PROPERTY_MEMBERS
Flag per specificare il tipo di informazioni da restituire in una richiesta per i membri di un oggetto.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp
enum JS_PROPERTY_MEMBERS{   JS_PROPERTY_MEMBERS_ALL = 0,   JS_PROPERTY_MEMBERS_ARGUMENTS = 1} JS_PROPERTY_MEMBERS;  
```  
  
## <a name="members"></a>Members  
  
### <a name="values"></a>Valori  
  
|Name|Descrizione|  
|----------|-----------------|  
|`JS_PROPERTY_MEMBERS_ALL`|Rappresenta una richiesta per l'enumerazione di tutti i membri.|  
|`JS_PROPERTY_MEMBERS_ARGUMENTS`|Rappresenta una richiesta per l'enumerazione dei soli argomenti.|  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** jscript9diag. h  
  
## <a name="see-also"></a>Vedere anche  
 [Riferimenti sulle interfacce Windows Script](../../winscript/reference/windows-script-interfaces-reference.md)