---
description: Ottiene il puntatore this (Me in Visual Basic) dell'oggetto contenente il metodo.
title: IDebugMethodField::GetThis | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugMethodField::GetThis
helpviewer_keywords:
- IDebugMethodField::GetThis method
ms.assetid: cc235bea-e909-4d8c-ab54-936736c803fc
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 382b230e580ac09f81a3c23a3308c5b6c844fbcf04bb89dcb240001f7759b98f
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121433723"
---
# <a name="idebugmethodfieldgetthis"></a>IDebugMethodField::GetThis
Ottiene il `this` puntatore ( `Me` in ) [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] dell'oggetto contenente il metodo.

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
[out] Restituisce un [oggetto IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) che rappresenta il puntatore "this".

## <a name="return-value"></a>Valore restituito
 Se ha esito positivo, restituisce S_OK; In caso contrario, restituisce un codice di errore.

## <a name="remarks"></a>Commenti
 Nei linguaggi orientati a oggetti è in genere presente un puntatore implicito alla creazione di un'istanza corrente di una classe. Questa operazione è nota `this` come in C#/C++ e come `Me` in [!INCLUDE[vbprvb](../../../code-quality/includes/vbprvb_md.md)] .

## <a name="see-also"></a>Vedi anche
- [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)
- [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)
