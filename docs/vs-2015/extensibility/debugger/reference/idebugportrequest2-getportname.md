---
title: 'IDebugPortRequest2:: getportaname | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: afed0bb700f41f7c39551f1a9bc7779f36b0ae57
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188357"
---
# <a name="idebugportrequest2getportname"></a>IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Ottiene il nome della porta.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
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
 out Restituisce il nome della porta.  
  
## <a name="return-value"></a>Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## <a name="remarks"></a>Osservazioni  
 L'interfaccia [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) viene in genere passata da un pacchetto di debug (il client) a un fornitore di porte (il server) per ottenere una connessione a una porta. Sia il pacchetto di debug che il fornitore della porta sono consapevoli delle possibili scelte per la porta. Se una stringa semplice può descrivere la porta, il `IDebugPortRequest2::GetPortName` metodo dispone di informazioni sufficienti per eseguire la connessione. In caso contrario, le interfacce aggiuntive possono essere fornite dal client, che possono essere ottenute dal server usando `IDebugPortRequest2::QueryInterface` .  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
