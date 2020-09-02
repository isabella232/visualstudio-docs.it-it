---
title: MemoryTypeEnum | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ded136da4d601fd7c11a10c21aac0c90864bc0bc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68158123"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Specifica il tipo di memoria a cui accedere.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 `MemTypeCode`  
 Accede solo alla memoria del codice.  
  
 `MemTypeData`  
 Accede ai dati o alla memoria dello stack.  
  
 `MemTypeStack`  
 Accede solo alla memoria dello stack.  
  
 `MemTypeAny`  
 Accede a qualsiasi tipo di memoria.  
  
## <a name="remarks"></a>Osservazioni  
 I valori di questa enumerazione vengono passati al metodo [IDiaStackWalkHelper:: ReadMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) per limitare l'accesso a diversi tipi di memoria.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst. h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)
