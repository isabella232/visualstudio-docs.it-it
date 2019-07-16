---
title: IDebugPortRequest2::GetPortName | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: afed0bb700f41f7c39551f1a9bc7779f36b0ae57
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68188357"
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
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)