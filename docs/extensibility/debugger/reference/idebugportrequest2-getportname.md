---
description: Ottiene il nome della porta.
title: 'IDebugPortRequest2:: getportaname | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortRequest2::GetPortName
helpviewer_keywords:
- IDebugPortRequest2::GetPortName
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 89bff19026a8bbdab72f1bec84c5feef0b37d8c6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072234"
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

## <a name="remarks"></a>Commenti
 L'interfaccia [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) viene in genere passata da un pacchetto di debug (il client) a un fornitore di porte (il server) per ottenere una connessione a una porta. Sia il pacchetto di debug che il fornitore della porta sono consapevoli delle possibili scelte per la porta. Se una stringa semplice può descrivere la porta, il `IDebugPortRequest2::GetPortName` metodo dispone di informazioni sufficienti per eseguire la connessione. In caso contrario, le interfacce aggiuntive possono essere fornite dal client, che possono essere ottenute dal server usando `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>Vedi anche
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
