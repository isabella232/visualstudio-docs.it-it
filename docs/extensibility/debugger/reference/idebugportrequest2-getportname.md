---
title: Proprietà IDebugPortRequest2::GetPortName . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 67121e98f2d506aa16c2b4dc3fff2ad5128fb93b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724820"
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

## <a name="parameters"></a>Parametri
`pbstrPortName`\
[fuori] Restituisce il nome della porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Il [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) interfaccia viene in genere passata da un pacchetto di debug (il client) a un fornitore di porta (il server) per ottenere una connessione a una porta. Sia il pacchetto di debug che il fornitore della porta sono a conoscenza delle possibili scelte per la porta. Se una stringa semplice può descrivere `IDebugPortRequest2::GetPortName` la porta, il metodo dispone di informazioni sufficienti per effettuare la connessione. In caso contrario, il client può fornire interfacce aggiuntive, che possono essere ottenute dal server utilizzando `IDebugPortRequest2::QueryInterface`.

## <a name="see-also"></a>Vedere anche
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
