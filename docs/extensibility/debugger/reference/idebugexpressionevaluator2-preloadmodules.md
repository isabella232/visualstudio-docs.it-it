---
title: IDebugExpressionEvaluator2::PreloadModules . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugExpressionEvaluator2::PreloadModules
- PreloadModules
ms.assetid: bcf9b968-ee14-4a92-88ad-926268a44e03
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: db345fb2936ef7278675407549798ae669487f06
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80729324"
---
# <a name="idebugexpressionevaluator2preloadmodules"></a>IDebugExpressionEvaluator2::PreloadModules
Precarica i moduli designati dal provider di simboli specificato.

## <a name="syntax"></a>Sintassi

```cpp
HRESULT PreloadModules (
    IDebugSymbolProvider* pSym
);
```

```csharp
int PreloadModules (
    IDebugSymbolProvider pSym
);
```

## <a name="parameters"></a>Parametri
`pSym`\
[in] Provider di simboli per il quale verranno precaricati i moduli.

## <a name="return-value"></a>Valore restituito
In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.

## <a name="remarks"></a>Osservazioni
Questo metodo facoltativo viene utilizzato quando si esegue una connessione di processo di hosting. Dà all'EE la possibilità di "riscaldarsi" come parte dell'attacco.

## <a name="example"></a>Esempio
Nell'esempio seguente viene illustrato come implementare questo metodo per un **ExpressionEvaluatorPackage** oggetto che espone il [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md) interfaccia.

```cpp
STDMETHODIMP ExpressionEvaluatorPackage::PreloadModules
(
    IDebugSymbolProvider *pSym
)
{
    HRESULT hr = NOERROR;
    RuntimeMemberDescriptor  * prtMemberDesc;
    RuntimeClassDescriptor *prtClassDesc;
    CComPtr<IDebugClassField> pClassField;
    IfFalseGo(pSym,E_INVALIDARG);

    prtMemberDesc = &(g_rgRTLangMembers[StandardModuleAttributeCtor]);
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);

    pClassField = NULL;
    prtMemberDesc = &(g_rgRTLangMembers[LoadAssembly]);
    prtClassDesc = &(g_rgRTLangClasses[prtMemberDesc->rtParent]);
    pSym->GetClassTypeByName(prtClassDesc->wszClassName, nmCaseSensitive, &pClassField);

Error:
    return hr;
}
```

## <a name="see-also"></a>Vedere anche
- [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)
