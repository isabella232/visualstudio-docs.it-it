---
title: IDebugAddress::GetAddress | Microsoft Docs
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
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ddb3b6e3d8055dd9a5b6304cf57a355986706b0d
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49186762"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

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

