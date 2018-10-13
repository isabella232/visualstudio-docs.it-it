---
title: IEnumDebugModules2::GetCount | Microsoft Docs
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
- IEnumDebugModules2::GetCount
helpviewer_keywords:
- IEnumDebugModules2::GetCount
ms.assetid: f4def3d2-7cc9-4cd2-9649-3b7e00a76220
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d5a501df87adc4312e4644e2c763407f83652ac8
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49220909"
---
# <a name="ienumdebugmodules2getcount"></a>IEnumDebugModules2::GetCount
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Restituisce il numero di elementi nell'enumerazione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetCount(  
   ULONG* pcelt  
);  
```  
  
```csharp  
int GetCount(  
   out uint pcelt  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pcelt`  
 [out] Restituisce il numero di elementi nell'enumerazione.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Questo metodo non fa parte dell'interfaccia di enumerazione COM facoltativa che specifica che solo le `Next`, `Clone`, `Skip`, e `Reset` devono essere implementati i metodi.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)

