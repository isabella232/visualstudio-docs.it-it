---
title: Proprietà IDebugPortPicker::DisplayPortPicker . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- DisplayPortPicker
- IDebugPortPicker::DisplayPortPicker
ms.assetid: 08511ef5-be64-4069-b169-a569cc94bc64
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e0a02169b37bba804034990ed5d972f973244769
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80724897"
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
[fuori] Stringa dell'identificatore di porta.

## <a name="return-value"></a>Valore restituito
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore. Un valore `S_FALSE` restituito di (o `S_OK` un `BSTR` valore `NULL`restituito di con il impostato su ) indica che l'utente ha fatto clic su **Annulla**.

## <a name="see-also"></a>Vedere anche
- [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md)
