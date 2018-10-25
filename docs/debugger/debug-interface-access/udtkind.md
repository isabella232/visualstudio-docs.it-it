---
title: UdtKind | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 49ea6a46825bbb94d55b0e9f9a4c052a1c12ae5f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49936563"
---
# <a name="udtkind"></a>UdtKind
Descrive la varietà di tipo definito dall'utente (UDT).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
enum UdtKind {   
   UdtStruct,  
   UdtClass,  
   UdtUnion,  
   UdtInterface  
};  
```  
  
## <a name="elements"></a>Elementi  
 UdtStruct  
 Tipo definito dall'utente è una struttura.  
  
 UdtClass  
 Tipo definito dall'utente è una classe.  
  
 UdtUnion  
 Tipo definito dall'utente è un'unione.  
  
 UdtInterface  
 Tipo definito dall'utente è un'interfaccia.  
  
## <a name="remarks"></a>Note  
 I valori di questa enumerazione vengono restituiti per il [Get_udtkind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: cvconst.h  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)