---
description: Questo metodo ottiene le utilità del computer per un server.
title: IDebugCoreServer2::GetMachineUtilities_V7 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 84d966c99267b60f39a8997d8a480ea028032e4abe82f16a15c111b535b278dc
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121323742"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Questo metodo ottiene le utilità del computer per un server.

> [!NOTE]
> Questo metodo è obsoleto: non usare ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] restituisce sempre se viene chiamato questo `E_NOTIMPL` metodo). Viene conservata per motivi cronologici.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetMachineUtilities_V7(
   IDebugMDMUtil2_V7** ppUtil
);
```

```csharp
int GetMachineUtilities_V7(
   out IDebugMDMUtil2_V7 ppUtil
);
```

## <a name="parameters"></a>Parametri
`ppUtil`\
[out] Restituisce `IDebugMDMUtil2_V7` un'interfaccia che rappresenta le informazioni sulle utilità del computer.

## <a name="return-value"></a>Valore restituito
 Restituisce sempre `E_NOTIMPL` , che indica che il metodo non è implementato.

## <a name="remarks"></a>Commenti
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] restituisce sempre `E_NOTIMPL` se viene chiamato questo metodo.

## <a name="see-also"></a>Vedi anche
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
