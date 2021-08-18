---
description: Rappresenta un alias numerico per una variabile e consente a un analizzatore di espressioni (edizione Enterprise) di ottenere il dominio applicazione per l'alias.
title: IDebugAlias2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugAlias2 interface
ms.assetid: 5252dcbb-8bfe-4d8a-a8e5-b022b194df19
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ae66d69153a539c42000914c9df1c275aa3a431c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122072876"
---
# <a name="idebugalias2"></a>IDebugAlias2
> [!IMPORTANT]
> In Visual Studio 2015, questo modo di implementare gli analizzatori di espressioni è deprecato. Per informazioni sull'implementazione di analizzatori di espressioni CLR, vedere [Clr Expression Evaluators](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) and [Managed Expression Evaluator Sample](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Rappresenta un alias numerico per una variabile e consente a un analizzatore di espressioni (edizione Enterprise) di ottenere il dominio applicazione per l'alias.

## <a name="syntax"></a>Sintassi

```
IDebugAlias2 : IDebugAlias
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Questa interfaccia viene implementata dal motore di debug gestito.

## <a name="methods"></a>Metodi
 Oltre ai metodi [nell'interfaccia IDebugAlias,](../../../extensibility/debugger/reference/idebugalias.md) questa interfaccia implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[GetAppDomainId](../../../extensibility/debugger/reference/idebugalias2-getappdomainid.md)|Recupera l'identificatore per il dominio applicazione.|

## <a name="remarks"></a>Commenti
 Un alias è un numero decimale in formato stringa seguito dal carattere #, ad esempio 1001#.

## <a name="requirements"></a>Requisiti
 Intestazione: Ee.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
