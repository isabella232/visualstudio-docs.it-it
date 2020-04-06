---
title: Proprietà IDebugPointerObject3 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugPointerObject3 interface
ms.assetid: 11d26af4-1079-435e-96fa-d5269cbea8eb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8605f1cdd50b6e98d6e30a7b550cce1d22543ff9
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725459"
---
# <a name="idebugpointerobject3"></a>IDebugPointerObject3
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere [Analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e Esempio di [analizzatore di](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)espressioni gestite .

 Rappresenta un puntatore in un albero di analisi ed estende il **IDebugPointerObject** interfaccia.

## <a name="syntax"></a>Sintassi

```
IDebugPointerObject3 : IDebugPointerObject
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata da un analizzatore di espressioni (EE).

## <a name="methods"></a>Metodi
 Oltre ai metodi sul IDebugPointerObject interfaccia, questa interfaccia implementa i metodi seguenti:In addition to the methods on the [IDebugPointerObject](../../../extensibility/debugger/reference/idebugpointerobject.md) interface, this interface implements the following methods:

|Metodo|Descrizione|
|------------|-----------------|
|[GetPointerAddress](../../../extensibility/debugger/reference/idebugpointerobject3-getpointeraddress.md)|Recupera l'indirizzo del puntatore.|

## <a name="requirements"></a>Requisiti
 Intestazione: Ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
