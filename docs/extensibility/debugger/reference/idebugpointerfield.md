---
title: Proprietà IDebugPointerField . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a69797cc513b96c364f0357f22788fc9bcd65657
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725602"
---
# <a name="idebugpointerfield"></a>IDebugPointerField
Questa interfaccia rappresenta un tipo di puntatore.

## <a name="syntax"></a>Sintassi

```
IDebugPointerField : IDebugContainerField
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il provider di simboli implementa questa interfaccia per rappresentare un puntatore.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Utilizzare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia dal [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) interfaccia se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce `FIELD_TYPE_POINTER`.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Oltre ai metodi `IDebugField` sulle `IDebugContainerField` interfacce e , questa interfaccia implementa il metodo seguente:In addition to the methods on the and interfaces, this interface implements the following method:

|Metodo|Descrizione|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Restituisce un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) che descrive la destinazione del puntatore.|

## <a name="remarks"></a>Osservazioni
 In C/C, un puntatore può essere un contenitore se viene utilizzato con la notazione di matrice. Ad esempio, `char *pString` `pString` dato , ha `char`un tipo di puntatore a . `pString[3]`ha il tipo di un contenitore che è un puntatore a `char` che fa riferimento al quarto elemento di tale contenitore.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedere anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
