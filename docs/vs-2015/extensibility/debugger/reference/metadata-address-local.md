---
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ba0259cae82ff1fba4fa93d2f81432e84ba426dd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49911616"
---
# <a name="metadataaddresslocal"></a>METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa struttura rappresenta l'indirizzo di una variabile locale all'interno di un ambito (in genere una funzione o metodo).  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## <a name="terms"></a>Termini  
 tokMethod  
 L'ID del metodo o funzione la variabile locale fa parte di.  
  
 [C++] `_mdToken` è un `typedef` un 32-bit `int`.  
  
 pLocal  
 Token il cui indirizzo di questa struttura rappresenta.  
  
 dwIndex  
 Può essere l'indice della variabile locale nel metodo o funzione o un altro valore (specifica del linguaggio).  
  
## <a name="remarks"></a>Note  
 Questa struttura è parte dell'unione nel [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) struttura quando il `dwKind` campo il `DEBUG_ADDRESS_UNION` struttura è impostata su `ADDRESS_KIND_LOCAL` (un valore compreso il [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumerazione).  
  
 `Warning:` [Solo C++]  Se `pLocal` non è null, sarà necessario chiamare `Release` sul puntatore token (`addr` è un campo il [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struttura):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)

