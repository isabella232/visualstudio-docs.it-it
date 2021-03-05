---
description: Questo metodo ottiene le utilità del computer per un server.
title: 'IDebugCoreServer2:: GetMachineUtilities_V7 | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: bc58f41d9cca98f6c15c164ed4acb941345627e5
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102154769"
---
# <a name="idebugcoreserver2getmachineutilities_v7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Questo metodo ottiene le utilità del computer per un server.

> [!NOTE]
> Questo metodo è obsoleto: non usare ( [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato). Viene mantenuto per motivi cronologici.

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
out Restituisce un' `IDebugMDMUtil2_V7` interfaccia che rappresenta le informazioni sulle utilità del computer.

## <a name="return-value"></a>Valore restituito
 Restituisce sempre `E_NOTIMPL` , che indica che il metodo non è implementato.

## <a name="remarks"></a>Commenti
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato.

## <a name="see-also"></a>Vedi anche
- [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
