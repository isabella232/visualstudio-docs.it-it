---
title: IEnumDebugFields::Reset | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- IEnumDebugFields::Reset
helpviewer_keywords:
- IEnumDebugFields::Reset method
ms.assetid: 38ff61e4-0120-42e8-971a-16be6050b425
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: fab8459f1cb279fd514730e7c3319bba951d04a6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47525302"
---
# <a name="ienumdebugfieldsreset"></a>IEnumDebugFields::Reset
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IEnumDebugFields::Reset](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ienumdebugfields-reset).  
  
Questo metodo reimposta l'enumerazione sul primo elemento.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Reset(void);  
```  
  
```csharp  
int Reset();  
```  
  
#### <a name="parameters"></a>Parametri  
 nessuno  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Dopo che questo metodo viene chiamato, la chiamata successiva a [successivo](../../../extensibility/debugger/reference/ienumdebugfields-next.md) restituisce il primo elemento dell'enumerazione.  
  
## <a name="see-also"></a>Vedere anche  
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [avanti](../../../extensibility/debugger/reference/ienumdebugfields-next.md)

