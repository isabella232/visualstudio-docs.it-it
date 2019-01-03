---
title: IDebugField::Equal | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugField::Equal
helpviewer_keywords:
- IDebugField::Equal method
ms.assetid: 75369fe6-ddd3-497d-80d1-2488e6100e9f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 0157a09390bd6e8380e97cef8e4c4158c75ac3ab
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/02/2019
ms.locfileid: "53918823"
---
# <a name="idebugfieldequal"></a>IDebugField::Equal
Questo metodo confronta questo campo con il campo specificato per verificarne l'uguaglianza.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT Equal(   
   IDebugField* pField  
);  
```  
  
```csharp  
int Equal(  
   IDebugField pField  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pField`  
 [in] Campo da confrontare con questo.  
  
## <a name="return-value"></a>Valore restituito  
 Se i campi sono uguali, restituisce `S_OK`. Se i campi sono diversi, restituisce `S_FALSE.` in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)