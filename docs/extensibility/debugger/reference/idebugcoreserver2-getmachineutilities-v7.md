---
title: IDebugCoreServer2::GetMachineUtilities_V7 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 79eba6889583f1dfa482dab107ad31eaaacdbcc2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80733146"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Questo metodo ottiene le utilità della macchina per un server.

> [!NOTE]
> Questo metodo è obsoleto:[!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] non `E_NOTIMPL` utilizzare ( restituisce sempre se questo metodo viene chiamato). Viene mantenuto per motivi storici.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parametri
`ppUtil`\
[fuori] Restituisce `IDebugMDMUtil2_V7` un'interfaccia che rappresenta le informazioni sulle utilità della macchina.

## <a name="return-value"></a>Valore restituito
 Restituisce `E_NOTIMPL`sempre , a indicare che il metodo non è implementato.

## <a name="remarks"></a>Osservazioni
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]restituisce `E_NOTIMPL` sempre se viene chiamato questo metodo.

## <a name="see-also"></a>Vedere anche
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
