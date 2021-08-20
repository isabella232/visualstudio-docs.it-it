---
title: INTERCEPT_EXCEPTION_ACTION | Microsoft Docs
description: L INTERCEPT_EXCEPTION_ACTION enumere specifica l'azione da intraprendere quando si intercettano le eccezioni Visual Studio debug.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- INTERCEPT_EXCEPTION_ACTION
helpviewer_keywords:
- INTERCEPT_EXCEPTION_ACTION enumeration
ms.assetid: e647f1eb-2932-4447-8c78-3b0d706fb972
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0fddfa37457a4783066a2319b081bf4372e7e06d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122125387"
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
Consente l'intercettazione dell'eccezione corrente. Questo è l'unico valore attualmente supportato e deve essere specificato.

## <a name="remarks"></a>Commenti
Questi valori vengono passati nel [metodo InterceptCurrentException.](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [InterceptCurrentException](../../../extensibility/debugger/reference/idebugstackframe3-interceptcurrentexception.md)
