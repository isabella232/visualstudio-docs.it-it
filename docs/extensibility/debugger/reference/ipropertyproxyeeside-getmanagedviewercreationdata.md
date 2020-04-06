---
title: Proprietà IPropertyProxyEESide::GetManagedViewerCreationData . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
helpviewer_keywords:
- IPropertyProxyEESide::GetManagedViewerCreationData
ms.assetid: c4eb4d60-8816-4d52-bc8d-dffd4f066499
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2e72922b348c8744f10037e199e93f735ff4be8e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80714955"
---
# <a name="ipropertyproxyeesidegetmanagedviewercreationdata"></a>IPropertyProxyEESide::GetManagedViewerCreationData
Recupera informazioni sul visualizzatore per questo tipo di proprietà per creare un'istanza di tale visualizzatore.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetManagedViewerCreationData(
   BSTR*                  assemName,
   IEEDataStorage**       assemBytes,
   IEEDataStorage**       assemPdb,
   BSTR*                  className,
   ASSEMBLYLOCRESOLUTION* alr,
   BOOL*                  replacementOk
);
```

```csharp
int GetManagedViewerCreationData(
   out string                     assemName,
   out IEEDataStorage             assemBytes,
   out IEEDataStorage             assemPdb,
   out string                     className,
   out enum_ASSEMBLYLOCRESOLUTION alr,
   out int                        replacementOk
);
```

## <a name="parameters"></a>Parametri
`assemName`\
[fuori] Restituisce il nome dell'assembly che contiene questo oggetto.

`assemBytes`\
[fuori] Restituisce un oggetto [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md) contenente i byte dell'assembly di questo oggetto (si tratta di un valore null se non sono disponibili byte).

`assemPdb`\
[fuori] Restituisce `IEEDataStorage` un oggetto contenente le informazioni sull'archivio simboli per questo oggetto (si tratta di un valore null se non è disponibile alcun archivio simboli).

`className`\
[fuori] Restituisce il nome della classe contenente questo oggetto.

`alr`\
[fuori] Restituisce un valore dall'enumerazione [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md) che indica il percorso dell'assembly.

`replacementOk`\
[fuori] Restituisce diverso`TRUE`da zero ( ) se il valore di questo oggetto può essere modificato; zero`FALSE`( ) se l'oggetto è di sola lettura.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
 Questo metodo viene utilizzato dai visualizzatori di tipo per creare un'istanza di un visualizzatore gestito.

## <a name="see-also"></a>Vedere anche
- [IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)
- [ASSEMBLYLOCRESOLUTION](../../../extensibility/debugger/reference/assemblylocresolution.md)
- [IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)
