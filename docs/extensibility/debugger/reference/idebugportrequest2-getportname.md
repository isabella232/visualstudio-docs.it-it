---
title: 'IDebugPortRequest2:: getportaname | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
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
out Restituisce il nome della porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 L'interfaccia [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) viene in genere passata da un pacchetto di debug (il client) a un fornitore di porte (il server) per ottenere una connessione a una porta. Sia il pacchetto di debug che il fornitore della porta sono consapevoli delle possibili scelte per la porta. Se una stringa semplice può descrivere la porta, il `IDebugPortRequest2::GetPortName` metodo dispone di informazioni sufficienti per eseguire la connessione. In caso contrario, le interfacce aggiuntive possono essere fornite dal client, che possono essere ottenute dal server usando `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>Vedere anche
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
