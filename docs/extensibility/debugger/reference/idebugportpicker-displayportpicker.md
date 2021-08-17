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
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f1acd8565c65e522d75652701fdf8333c70faa40
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126843"
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
[in] Handle per la finestra di dialogo padre.

`pbstrPortId`\
[out] Stringa dell'identificatore di porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Un valore restituito di (o un valore restituito di con impostato su ) indica che l'utente ha fatto clic `S_FALSE` `S_OK` su `BSTR` `NULL` **Annulla.**

## <a name="see-also"></a>Vedi anche
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
