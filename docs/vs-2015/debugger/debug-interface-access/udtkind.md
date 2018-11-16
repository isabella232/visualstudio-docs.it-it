---
title: UdtKind | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d81fd7d9a6828e50af10667716ed8f5fd2e1a2cd
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51805996"
---
# <a name="udtkind"></a>UdtKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Descrive la varietà di tipo definito dall'utente (UDT).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum UdtKind {   
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



