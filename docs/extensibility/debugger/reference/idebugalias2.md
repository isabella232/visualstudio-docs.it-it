---
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2c59d89771436db6ba1bbde4fc1a01e132e7e210
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56689954"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione di analizzatori di espressioni di Common Language Runtime, vedi [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestito esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Rappresenta un alias per una variabile numerico e consente un analizzatore di espressioni (EE) per ottenere il dominio dell'applicazione per l'alias.

## <a name="syntax"></a>Sintassi

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dal motore di debug gestito (DE).

## <a name="methods"></a>Metodi
 Oltre ai metodi nel [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) interfaccia, questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Recupera l'identificatore per il dominio applicazione.|

## <a name="remarks"></a>Note
 Un alias è un numero decimale in formato stringa seguita dal carattere #, ad esempio, & 1001.

## <a name="requirements"></a>Requisiti
 Intestazione: EE.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll