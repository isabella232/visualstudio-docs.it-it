---
description: Questa interfaccia rappresenta un tipo di puntatore.
title: IDebugPointerField | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPointerField
helpviewer_keywords:
- IDebugPointerField interface
ms.assetid: d51bd5b2-f18e-4e27-b4fb-e6f652fbf635
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: eba0654d97d37633ca1b2afce45b83de1a96bc1b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133081"
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
 Usare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia [dall'interfaccia IDebugField](../../../extensibility/debugger/reference/idebugfield.md) se [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) restituisce `FIELD_TYPE_POINTER` .

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
 Oltre ai metodi sulle interfacce e , questa interfaccia `IDebugField` `IDebugContainerField` implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetDereferencedField](../../../extensibility/debugger/reference/idebugpointerfield-getdereferencedfield.md)|Restituisce un [oggetto IDebugField che](../../../extensibility/debugger/reference/idebugfield.md) descrive la destinazione del puntatore.|

## <a name="remarks"></a>Commenti
 In C/C++ un puntatore può essere un contenitore se viene usato con la notazione di matrice. Ad esempio, dato `char *pString` , ha un tipo di `pString` puntatore a `char` . `pString[3]` ha il tipo di un contenitore che è un puntatore a `char` che fa riferimento al quarto elemento di tale contenitore.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)
