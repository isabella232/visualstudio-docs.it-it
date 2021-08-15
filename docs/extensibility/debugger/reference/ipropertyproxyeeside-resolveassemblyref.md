---
description: Determina il percorso del riferimento all'assembly gestito specificato.
title: IPropertyProxyEESide::ResolveAssemblyRef | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 1533572f67f681cac394ff5d4fba2558fbaf9c66e3aa42de5f12fff5bdc2676d
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321376"
---
# <a name="ipropertyproxyeesideresolveassemblyref"></a>IPropertyProxyEESide::ResolveAssemblyRef
Determina il percorso del riferimento all'assembly gestito specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT ResolveAssemblyRef(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  assemLocation,
   ASSEMBLYLOCRESOLUTION* alr
);
```

```csharp
int ResolveAssemblyRef(
   ref string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     assemLocation,
   out enum_ASSEMBLYLOCRESOLUTION alr
);
```

## <a name="parameters"></a>Parametri
`assemName`\
[in] Nome dell'assembly da risolvere.

`assemBytes`\
[out] Restituisce un [oggetto IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenente i byte dell'assembly associati al riferimento.

`assemPdb`\
[out] Restituisce un `IEEDataStorage` oggetto contenente i dati dell'archivio simboli associati a questo riferimento.

`assemLocation`\
[out] Restituisce il percorso di questo riferimento.

`alr`\
[out] Restituisce un valore [dall'enumerazione ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) che indica il percorso dell'assembly di questo riferimento.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
 Questo metodo non viene in genere implementato da un analizzatore di espressioni personalizzato.

## <a name="see-also"></a>Vedi anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
