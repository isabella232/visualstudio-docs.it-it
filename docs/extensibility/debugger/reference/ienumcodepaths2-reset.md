---
title: IEnumCodePaths2::Reset | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IEnumCodePaths2::Reset
helpviewer_keywords:
- IEnumCodePaths2::Reset
ms.assetid: 490c0e19-ff4b-4673-bd06-cdee996ac226
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: aa4b17e79a0920388c02889717148fa58e72199f
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49941438"
---
# <a name="ienumcodepaths2reset"></a>IEnumCodePaths2::Reset
Reimposta l'enumerazione sul primo elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Reset(  
   void  
);  
```  
  
```csharp  
int Reset();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Dopo che questo metodo viene chiamato, la chiamata successiva per la [successivo](../../../extensibility/debugger/reference/ienumcodepaths2-next.md) metodo restituisce il primo elemento dell'enumerazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)