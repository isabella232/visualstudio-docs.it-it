---
description: Rappresenta un alias numerico per una variabile e consente a un analizzatore di espressioni (EE) di ottenere il dominio applicazione per l'alias.
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f6ca97fbe23e9b0c84c39e591c0fd9cfb997fca5
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105059041"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> In Visual Studio 2015, questo metodo di implementazione degli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione degli analizzatori di espressioni CLR, vedere l'esempio degli [analizzatori](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) di espressioni CLR e dell' [analizzatore di espressioni gestite](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Rappresenta un alias numerico per una variabile e consente a un analizzatore di espressioni (EE) di ottenere il dominio applicazione per l'alias.

## <a name="syntax"></a>Sintassi

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dal motore di debug gestito (DE).

## <a name="methods"></a>Metodi
 Oltre ai metodi sull'interfaccia [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md) , questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Recupera l'identificatore per il dominio dell'applicazione.|

## <a name="remarks"></a>Commenti
 Un alias è un numero decimale in formato stringa seguito dal carattere #, ad esempio 1001 #.

## <a name="requirements"></a>Requisiti
 Intestazione: EE. h

 Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
