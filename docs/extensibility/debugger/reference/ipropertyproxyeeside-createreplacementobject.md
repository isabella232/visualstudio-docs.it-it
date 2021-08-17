---
description: Crea una copia di un oggetto dati specifico dell'analizzatore di espressioni (edizione Enterprise).
title: IPropertyProxyEESide::CreateReplacementObject | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::CreateReplacementObject
helpviewer_keywords:
- IPropertyProxyEESide::CreateReplacementObject
ms.assetid: 0cfe79b8-c3f1-48b0-a225-e39dee2c92fe
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1d147e07fb87b016582373c46dd672f57daf1369
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122029242"
---
# <a name="ipropertyproxyeesidecreatereplacementobject"></a>IPropertyProxyEESide::CreateReplacementObject
Crea una copia di un oggetto dati specifico dell'analizzatore di espressioni (edizione Enterprise).

## <a name="syntax"></a>Sintassi

```cpp
HRESULT CreateReplacementObject(
   IEEDataStorage*  dataIn,
   IEEDataStorage** dataOut
);
```

```csharp
int CreateReplacementObject(
   IEEDataStorage     dataIn,
   out IEEDataStorage dataOut
);
```

## <a name="parameters"></a>Parametri
`dataIn`\
[in] Oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenente i dati da copiare.

`dataOut`\
[out] Restituisce un nuovo oggetto `IEEDataStorage`.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 A questo metodo viene assegnato [un oggetto IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) che rappresenta una matrice di byte. Questo oggetto dati in ingresso non viene in genere implementato dal edizione Enterprise. Tuttavia, l'oggetto restituito da questo metodo viene sempre implementato dal edizione Enterprise, che consente al edizione Enterprise di implementare l'interfaccia su qualsiasi `IEEDataStorage` classe desiderata.

 Si noti che i dati forniti dall'oggetto `IEEDataStorage` in ingresso devono essere gli stessi nell'oggetto in `IEEDataStorage` uscita.

## <a name="see-also"></a>Vedi anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
