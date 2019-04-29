---
title: IDebugIDECallback::DisplayMessage | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback::DisplayMessage
ms.assetid: c19b48ee-b370-4fce-91fe-f82bf1e63179
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1477ec9bd9bbd56d10d2ccd58251fd014056b5dd
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62919066"
---
# <a name="idebugidecallbackdisplaymessage"></a>IDebugIDECallback::DisplayMessage
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Invia la stringa di messaggio specificato alla finestra di output del debugger.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT DisplayMessage (  
   LPCOLESTR szMessage  
);  
```  
  
```csharp  
int DisplayMessage (  
   string szMessage  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `szMessage`  
 [in] Stringa di messaggio da visualizzare nella finestra di output del debugger.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugIDECallback](../../../extensibility/debugger/reference/idebugidecallback.md)
