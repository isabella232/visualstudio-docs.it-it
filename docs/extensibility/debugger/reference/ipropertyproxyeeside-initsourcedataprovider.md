---
description: Inizializza i dati di origine per questo oggetto e restituisce un oggetto contenente i dati iniziali.
title: IPropertyProxyEESide::InitSourceDataProvider | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
helpviewer_keywords:
- IPropertyProxyEESide::InitSourceDataProvider
ms.assetid: 5156f593-5052-4e3a-9d02-081916fb342d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 18af1ffbce8d2e1dc38ecbff82bcf87e5a07160d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122103156"
---
# <a name="ipropertyproxyeesideinitsourcedataprovider"></a>IPropertyProxyEESide::InitSourceDataProvider
Inizializza i dati di origine per questo oggetto e restituisce un oggetto contenente i dati iniziali.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT InitSourceDataProvider(
   IEEDataStorage** dataOut
);
```

```csharp
int InitSourceDataProvider(
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametri
`dataOut`\
[out] Restituisce un [oggetto IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo esegue tutte le operazioni necessarie per inizializzare un oggetto in modo che possa restituire [un'interfaccia IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) sui dati dell'oggetto. In questo modo i dati dell'oggetto possono essere visualizzati e, se consentito, modificati da un visualizzatore di tipi.

## <a name="see-also"></a>Vedi anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
