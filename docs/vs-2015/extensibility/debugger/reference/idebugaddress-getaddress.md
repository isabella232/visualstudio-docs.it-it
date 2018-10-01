---
title: IDebugAddress::GetAddress | Microsoft Docs
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
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: e4a469ba1e6f85a1ac83ba06efa45ba2b6c4fcbc
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47530030"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [IDebugAddress::GetAddress](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/idebugaddress-getaddress).  
  
Restituisce una struttura che descrive un oggetto e il relativo percorso nel relativo ambito o di un contenitore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pAddress`  
 [in, out] Oggetto [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struttura che viene compilato da questo metodo.  
  
## <a name="return-value"></a>Valore restituito  
 Se l'operazione riesce, restituisce S_OK; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) struttura viene passata a questo metodo, che quindi viene riempita con le informazioni appropriate. Modalità di interpretazione di queste informazioni dipende dal tipo di informazioni restituite e il gestore di simboli se stesso. Visualizzare [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) per altri dettagli.  
  
## <a name="see-also"></a>Vedere anche  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)

