---
title: Proprietà IDebugGenericFieldDefinition . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugGenericFieldDefinition interface
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 019633b62d46f6a8ac68e6f5f4abc888e6986ab1
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80728198"
---
# <a name="idebuggenericfielddefinition"></a>IDebugGenericFieldDefinition
Rappresenta la definizione di un campo per un tipo generico di codice gestito.

## <a name="syntax"></a>Sintassi

```
IDebugGenericFieldDefinition : IUnknown
```

## <a name="methods"></a>Metodi
 Questa interfaccia implementa i metodi seguenti:This interface implements the following methods:

|Metodo|Descrizione|
|------------|-----------------|
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Costruisce un'istanza di campo data una matrice di argomenti di tipo.|
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Recupera i parametri di tipo in base al numero di parametri.|
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Recupera il numero di parametri di tipo associati al campo generico.|

## <a name="requirements"></a>Requisiti
 Intestazione: Sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
