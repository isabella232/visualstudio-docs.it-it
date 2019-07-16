---
title: IEnumDebugPorts2::Skip | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IEnumDebugPorts2::Skip
helpviewer_keywords:
- IEnumDebugPorts2::Skip
ms.assetid: a837383f-7b39-4e06-b336-f1715b073dbe
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 96bf6bd5277e6683bf793de17e608802c6c01034
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68155040"
---
# <a name="ienumdebugports2skip"></a>IEnumDebugPorts2::Skip
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ignora il numero specificato di elementi.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Skip(  
   ULONG celt  
);  
```  
  
```csharp  
int Skip(  
   uint celt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `celt`  
 [in] Numero di elementi da ignorare.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'esito è positivo, restituisce `S_OK`. Restituisce `S_FALSE` se `celt` è maggiore del numero di elementi rimanenti; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Se `celt` specifica un valore maggiore del numero di elementi rimanenti, l'enumerazione è impostata su Fine e `S_FALSE` viene restituito.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md)
