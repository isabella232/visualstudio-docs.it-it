---
description: Recupera i flag per questo parametro generico.
title: IDebugGenericParamField::GetFlags | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- GetFlags
- IDebugGenericParamField::GetFlags
ms.assetid: adcbbca1-8960-4c88-86b0-8b9467056c97
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: f77a97c3c558055bb2f92f7c98112c0e8b483a17
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127103"
---
# <a name="idebuggenericparamfieldgetflags"></a>IDebugGenericParamField::GetFlags
Recupera i flag per questo parametro generico.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT GetFlags(
    DWORD* pdwFlags
);
```

```csharp
int GetFlags(
    ref uint pdwFlags
);
```

## <a name="parameters"></a>Parametri
`pdwFlags`\
[out] Restituisce i flag per questo parametro generico.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Commenti
Questi flag contengono informazioni sui vari vincoli speciali.

## <a name="example"></a>Esempio
L'esempio seguente illustra come implementare questo metodo per un **oggetto CDebugGenericParamFieldType** che espone [l'interfaccia IDebugGenericParamField.](../../../extensibility/debugger/reference/idebuggenericparamfield.md)

```cpp
HRESULT CDebugGenericParamFieldType::GetFlags(DWORD *pdwFlags)
{
    HRESULT hr = S_OK;

    METHOD_ENTRY( CDebugGenericParamFieldType::GetFlags );

    IfFalseGo( pdwFlags, E_INVALIDARG );
    IfFailGo( this->LoadProps() );
    *pdwFlags = m_dwFlags;

Error:

    METHOD_EXIT( CDebugGenericParamFieldType::GetFlags, hr );
    return hr;
}
```

## <a name="see-also"></a>Vedi anche
- [IDebugGenericParamField](../../../extensibility/debugger/reference/idebuggenericparamfield.md)
