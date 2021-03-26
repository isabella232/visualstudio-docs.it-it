---
description: Visualizza la finestra di dialogo specificata che consente all'utente di selezionare una porta.
title: IDebugPortPicker::D isplayPortPicker | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: a49c1379d2bb3946f75eddd9d80bdccdb370d3ab
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105072312"
---
# <a name="idebugportpickerdisplayportpicker"></a>IDebugPortPicker::DisplayPortPicker
Visualizza la finestra di dialogo specificata che consente all'utente di selezionare una porta.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT DisplayPortPicker(
   HWND hwndParentDialog,
   BSTR* pbstrPortId
);
```

```csharp
public int DisplayPortPicker(
   int hwndParentDialog,
   out string pbstrPortId
);
```

## <a name="parameters"></a>Parametri
`hwndParentDialog`\
in Handle per la finestra di dialogo padre.

`pbstrPortId`\
out Stringa dell'identificatore di porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Un valore restituito di `S_FALSE` (o un valore restituito `S_OK` con `BSTR` impostato su `NULL` ) indica che l'utente ha fatto clic su **Annulla**.

## <a name="see-also"></a>Vedi anche
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
