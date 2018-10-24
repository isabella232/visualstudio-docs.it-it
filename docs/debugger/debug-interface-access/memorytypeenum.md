---
title: MemoryTypeEnum | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MemoryTypeEnum enumeration
ms.assetid: 8778c047-edeb-4495-8f9f-3f8bbb297099
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 4a8dcf657933cf62f3f2173bb89dadd1366b0cec
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49822943"
---
# <a name="memorytypeenum"></a>MemoryTypeEnum
Specifica il tipo di memoria per accedere.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
enum MemoryTypeEnum {  
   MemTypeCode,  
   MemTypeData,  
   MemTypeStack,  
   MemTypeAny = -1  
};  
```  
  
#### <a name="parameters"></a>Parametri  
 `MemTypeCode`  
 Gli accessi alla memoria del codice solo.  
  
 `MemTypeData`  
 Accede a dati o dello stack di memoria.  
  
 `MemTypeStack`  
 Gli accessi solo la memoria dello stack.  
  
 `MemTypeAny`  
 Accede a qualsiasi tipo di memoria.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione vengono passati per il [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md) metodo per limitare l'accesso a diversi tipi di memoria.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaStackWalkHelper::readMemory](../../debugger/debug-interface-access/idiastackwalkhelper-readmemory.md)