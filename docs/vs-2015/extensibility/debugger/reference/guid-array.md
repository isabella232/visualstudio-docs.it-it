---
title: GUID_ARRAY | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- GUID_ARRAY structure
ms.assetid: 9e12500c-2c1c-49b1-a0ba-e08366c97eb8
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 990e15dfee18c4158ca145e89ec3137b72ae6454
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/16/2018
ms.locfileid: "51788758"
---
# <a name="guidarray"></a>GUID_ARRAY
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Descrive una matrice di identificatori univoci per i motori di debug disponibili.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
typedef struct tagGUID_ARRAY  
{  
   DWORD dwCount;  
   GUID *Members;  
} GUID_ARRAY;  
```  
  
```csharp  
public struct GUID_ARRAY  
{  
   public uint dwCount;  
   public Guid Members;  
}  
```  
  
## <a name="terms"></a>Termini  
 dwCount  
 Numero di identificatori univoci nella matrice.  
  
 Membri  
 Matrice che contiene gli identificatori univoci.  
  
## <a name="remarks"></a>Note  
 Questa struttura viene restituita per le [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md) (metodo).  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)

