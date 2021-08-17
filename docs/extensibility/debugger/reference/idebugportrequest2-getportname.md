---
description: Ottiene il nome della porta.
title: IDebugPortRequest2::GetPortName | Microsoft Docs
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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e5eceb34e8d82853289663a6b6795a266444d8635e34f33c490fe2a53307c1f2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121339060"
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
[out] Restituisce il nome della porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 [L'interfaccia IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) viene in genere passata da un pacchetto di debug (client) a un fornitore di porte (server) per ottenere una connessione a una porta. Sia il pacchetto di debug che il fornitore della porta sono a conoscenza delle possibili scelte per la porta. Se una stringa semplice può descrivere la porta, il `IDebugPortRequest2::GetPortName` metodo dispone di informazioni sufficienti per stabilire la connessione. In caso contrario, il client può fornire interfacce aggiuntive, che possono essere ottenute dal server usando `IDebugPortRequest2::QueryInterface` .

## <a name="see-also"></a>Vedi anche
- [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)
