---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: cd5033926987ef1a2673380a4f7d76dc1b0cb0c0
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54962732"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
Ottiene il nome della porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```csharp  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pbstrPortName`  
 [out] Restituisce il nome della porta.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Il [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interfaccia viene in genere passata da un pacchetto di debug (client) a un fornitore di porte (server) per ottenere una connessione a una porta. Sia il pacchetto di debug e il fornitore della porta sia consapevoli delle possibili scelte per la porta. Se una stringa semplice può descrivere la porta, quindi il `IDebugPortRequest2::GetPortName` metodo ha informazioni sufficienti per stabilire la connessione. In caso contrario, interfacce aggiuntive possono essere fornite dal client, che può essere ottenuto tramite il server `IDebugPortRequest2::QueryInterface`.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)