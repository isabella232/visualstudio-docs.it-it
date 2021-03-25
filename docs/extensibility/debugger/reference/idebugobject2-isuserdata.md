---
description: Determina se l'oggetto rappresenta i dati utente.
title: 'IDebugObject2:: IsUserData | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2::IsUserData
helpviewer_keywords:
- IDebugObject2::IsUserData method
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 485583c0d6ef8ac42b78612e68995462ef900795
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105053724"
---
# <a name="idebugobject2isuserdata"></a>IDebugObject2::IsUserData
Determina se l'oggetto rappresenta i dati utente.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT IsUserData(
   BOOL* pfUser
);
```

```csharp
int IsUserData(
   out int pfUser
);
```

## <a name="parameters"></a>Parametri
`pfUser`\
out Restituisce un valore diverso da zero ( `TRUE` ) se l'oggetto rappresenta i dati utente; in caso contrario, zero ( `FALSE` ).

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 I dati utente sono oggetti che fanno parte di un modulo designato come JustMyCode (opzione configurabile dall'utente che contrassegna un modulo come codice utente e quindi visibile in una traccia dello stack).

## <a name="see-also"></a>Vedi anche
- [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)
