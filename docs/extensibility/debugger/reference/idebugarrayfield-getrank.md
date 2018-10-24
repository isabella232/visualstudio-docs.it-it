---
title: IDebugArrayField::GetRank | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- IDebugArrayField::GetRank
helpviewer_keywords:
- IDebugArrayField::GetRank method
ms.assetid: 2364b876-5be1-4bab-9b8f-3b6121da35c6
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 6921da02b2df62509dd820795581e3ce6dae92d6
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49846239"
---
# <a name="idebugarrayfieldgetrank"></a>IDebugArrayField::GetRank
Ottiene il numero di dimensioni o il numero di dimensioni della matrice.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetRank(   
   DWORD* pdwRank  
);  
```  
  
```csharp  
int GetRank(  
   out uint pdwRank  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pdwRank`  
 [out] Restituisce il rango.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il rango della matrice corrisponde al numero di dimensioni. In C++ e c#, le matrici multidimensionali sono in realtà le matrici di matrici e pertanto può essere considerate solo una matrice unidimensionale (e `GetRank` metodo restituirà sempre 1). Nelle [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)], d'altra parte, le matrici multidimensionali sono gestite in modo diverso e il numero di dimensioni di una matrice di questo tipo riflette il numero di dimensioni (e `GetRank` metodo restituisce sempre il numero di dimensioni).  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md)