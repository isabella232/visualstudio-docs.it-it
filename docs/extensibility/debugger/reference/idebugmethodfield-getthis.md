---
description: Ottiene il puntatore this (me in Visual Basic) dell'oggetto che contiene il metodo.
title: 'IDebugMethodField:: getthis | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 3eb303a7e0a4795d3f7ef49f9114cc942bff9b2d
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/05/2021
ms.locfileid: "102164942"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Ottiene il `this` `Me` puntatore (in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] ) dell'oggetto che contiene il metodo.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetThis( 
   IDebugClassField** ppClass
);
```

```csharp
int GetThis(
   out IDebugClassField ppClass
);
```

## <a name="parameters"></a>Parametri
`ppClass`\
out Restituisce un oggetto [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che rappresenta il puntatore "This".

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; in caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Nei linguaggi orientati a oggetti è in genere presente un puntatore implicito alla creazione di un'istanza corrente di una classe. Questa operazione è nota come `this` in C#/c + + e come `Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

## <a name="see-also"></a>Vedi anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
