---
title: IDebugCustomAttributeQuery | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ae0640b23ec7e206dac8b0aaeff605e6592b1fc5
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/29/2019
ms.locfileid: "66322240"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
Rappresenta una query per gli attributi personalizzati in un tipo o metodo.

## <a name="syntax"></a>Sintassi

```
IDebugCustomAttributeQuery : IUnknown
```

## <a name="methods"></a>Metodi
 Questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Recupera un attributo personalizzato in base al nome.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Determina nell'oggetto specificato è definito l'attributo personalizzato.|

## <a name="requirements"></a>Requisiti
 Intestazione: Sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll