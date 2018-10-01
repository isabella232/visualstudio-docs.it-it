---
title: IDebugAddress2::GetProcessID | Microsoft Docs
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
- IDebugAddress2::GetProcessID
helpviewer_keywords:
- IDebugAddress2::GetProcessID method
ms.assetid: 2c18889d-074a-4b95-87b4-bf1a067f44ed
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 31c935db12a3cbac5bf4e85800e826e1972be4f5
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47528279"
---
# <a name="idebugaddress2getprocessid"></a>IDebugAddress2::GetProcessID
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugAddress2::GetProcessID](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugaddress2-getprocessid).  
  
Recupera l'ID del processo a cui appartiene l'oggetto rappresentato da questo [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md) interfaccia.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetProcessID (  
   DWORD* pProcID  
);  
```  
  
```csharp  
int GetProcessID (  
   out uint pProcID  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pProcID`  
 [out] L'ID del processo.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugAddress2](../../../extensibility/debugger/reference/idebugaddress2.md)

