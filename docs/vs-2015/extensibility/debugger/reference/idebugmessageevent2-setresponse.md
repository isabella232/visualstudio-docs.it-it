---
title: 'IDebugMessageEvent2:: seresponse | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugMessageEvent2::SetResponse
helpviewer_keywords:
- IDebugMessageEvent2::SetResponse method
- SetResponse method
ms.assetid: 2a5e318d-3225-4abd-83f1-28323baff6c0
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cac96c0f5476694b18884fd8d7713a2bec877aef
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685904"
---
# <a name="idebugmessageevent2setresponse"></a>IDebugMessageEvent2::SetResponse
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Imposta la risposta, se presente, dalla finestra di messaggio.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT SetResponse(   
   DWORD dwResponse  
);  
```  
  
```csharp  
int SetResponse(   
   uint dwResponse  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `dwResponse`  
 in Specifica la risposta, usando le convenzioni della `MessageBox` funzione Win32. Per informazioni dettagliate, vedere la funzione [AfxMessageBox](https://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8) .  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md)   
 [AfxMessageBox](https://msdn.microsoft.com/library/d66d0328-cdcc-48f6-96a4-badf089099c8)
