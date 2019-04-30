---
title: IDebugObject2::IsEncOutdated | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugObject2::IsEncOutdated
helpviewer_keywords:
- IDebugObject2::IsEncOutdated method
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 70c1af4a67c55189531c2826e9eb22f0482eb520
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "63413766"
---
# <a name="idebugobject2isencoutdated"></a>IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo determina se lo stato di modifica e continuazione di questo oggetto o del contenitore padre non è aggiornato. Un analizzatore di espressioni personalizzato non implementa questo metodo e restituisce sempre `E_NOTIMPL`.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```csharp  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pfEncOutdated`  
 [out] Diverso da zero (`TRUE`) se lo stato di modifica e continuazione non è aggiornato, zero (`FALSE`) in caso contrario.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
> [!NOTE]
> Un analizzatore di espressioni personalizzato deve sempre restituire `E_NOTIMPL`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
