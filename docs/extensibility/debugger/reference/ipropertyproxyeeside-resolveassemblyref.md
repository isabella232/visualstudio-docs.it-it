---
title: Proprietà IPropertyProxyEESide::ResolveAssemblyRef . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
helpviewer_keywords:
- IPropertyProxyEESide::ResolveAssemblyRef
ms.assetid: 662ca0a6-dad0-4c00-a718-bb3bbc5bd9da
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: c54945b0c89fb9608fab6aa70dcc63a7c6ae42df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714880"
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
[fuori] Restituisce un oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenente i byte dell'assembly associati al riferimento.

`assemPdb`\
[fuori] Restituisce `IEEDataStorage` un oggetto contenente i dati dell'archivio simboli associati a questo riferimento.

`assemLocation`\
[fuori] Restituisce il percorso del percorso di questo riferimento.

`alr`\
[fuori] Restituisce un valore dall'enumerazione [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) che indica la posizione dell'assembly di questo riferimento.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo non viene in genere implementato da un analizzatore di espressioni personalizzate.

## <a name="see-also"></a>Vedere anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
