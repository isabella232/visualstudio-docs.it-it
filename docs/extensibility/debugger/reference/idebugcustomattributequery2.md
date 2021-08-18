---
description: Determina l'esistenza di un attributo personalizzato per questo campo e, se esistente, restituisce le informazioni sull'attributo.
title: IDebugCustomAttributeQuery2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
- IDebugCustomAttributeQuery2 interface
ms.assetid: 7cfa23e4-a05a-47a3-af6c-bd40c655014b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 13f07dc42327f90fc9bc816562c2b4e2117ee113
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079389"
---
# <a name="idebugcustomattributequery2"></a>IDebugCustomAttributeQuery2
Determina l'esistenza di un attributo personalizzato per questo campo e, se esistente, restituisce le informazioni sull'attributo.

## <a name="syntax"></a>Sintassi

```
IDebugCustomAttributeQuery2 : IDebugCustomAttributeQuery
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) per supportare gli attributi personalizzati.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Usare [QueryInterface](/cpp/atl/queryinterface) per ottenere questa interfaccia [dall'interfaccia IDebugField.](../../../extensibility/debugger/reference/idebugfield.md)

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 La tabella seguente illustra i metodi **dell'interfaccia IDebugCustomAttributeQuery.**

|Metodo|Descrizione|
|------------|-----------------|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)|Determina se un attributo personalizzato esiste in base al nome.|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery2-getcustomattributebyname.md)|Ottiene le informazioni sull'attributo per l'attributo personalizzato specificato.|

 Oltre ai metodi **IDebugCustomAttributeQuery,** `IDebugCustomAttributeQuery2` implementa il metodo seguente:

|Metodo|Descrizione|
|------------|-----------------|
|[EnumCustomAttributes](../../../extensibility/debugger/reference/idebugcustomattributequery2-enumcustomattributes.md)|Ottiene un enumeratore per tutti gli attributi personalizzati associati a questo campo.|

## <a name="remarks"></a>Commenti
 Il [metodo IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md) può restituire un enumeratore per tutti gli attributi personalizzati definiti per questo campo.

## <a name="requirements"></a>Requisiti
 Intestazione: sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce del provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)
- [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)
- [IEnumDebugCustomAttributes](../../../extensibility/debugger/reference/ienumdebugcustomattributes.md)
