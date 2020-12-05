---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft Docs
description: L'enumerazione INTERCEPT_EXCEPTION_ACTION specifica l'azione da intraprendere durante l'intercettazione delle eccezioni nel debug di Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e80ed1b17f98326701b0ca0aacb8e114c9b49db4
ms.sourcegitcommit: 42981ace63c0f2b087de5703ca76b8dcdd93a719
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/04/2020
ms.locfileid: "96606443"
---
# <a name="intercept_exception_action"></a>INTERCEPT_EXCEPTION_ACTION
Specifica le azioni da intraprendere durante l'intercettazione delle eccezioni.

## <a name="syntax"></a>Sintassi

```cpp
enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
typedef DWORD INTERCEPT_EXCEPTION_ACTION;
```

```csharp
public enum enum_INTERCEPT_EXCEPTION_ACTION
{
    IEA_INTERCEPT = 0x0001
}
```

## <a name="parameters"></a>Parametri

`IEA_INTERCEPT`\
Consente di intercettare l'eccezione corrente. Questo è l'unico valore attualmente supportato e deve essere specificato.

## <a name="remarks"></a>Commenti
Questi valori vengono passati nel metodo [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md) .

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
