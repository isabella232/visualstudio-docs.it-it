---
title: IDebugProcessEx2::Detach | Microsoft Docs
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
- IDebugProcessEx2::Detach
helpviewer_keywords:
- IDebugProcessEx2::Detach method
ms.assetid: 66d54c2c-9302-47c8-9975-f30ed988ab29
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: adb466ee030700c938c59781d97b66be5ba5b30d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49921795"
---
# <a name="idebugprocessex2detach"></a>IDebugProcessEx2::Detach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questo metodo indica il processo che una sessione di debug non è più il processo.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT Detach(   
   IDebugSession2* pSession  
);  
```  
  
```csharp  
int Detach(  
   IDebugSession2 pSession  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pSession`  
 [in] Un valore che identifica in modo univoco la sessione per questo processo da scollegare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 L'interfaccia passato `pSession` è deve essere considerato solo un cookie, un valore che identifica in modo univoco il gestore di sessione di debug che originariamente collegato a questo processo, nessuno dei metodi nell'interfaccia specificata sono funzionali.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)

