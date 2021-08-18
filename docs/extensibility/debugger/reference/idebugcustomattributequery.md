---
description: Rappresenta una query per gli attributi personalizzati in un metodo o un tipo.
title: Interfaccia IDebugCustomAttributeQuery | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugCustomAttributeQuery interface
ms.assetid: b804b619-70eb-4c38-80d9-c8b32b65ed3e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: ea6f8b4355f702998a18a0b40911fd58fb1afb74
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079428"
---
# <a name="idebugcustomattributequery"></a>IDebugCustomAttributeQuery
Rappresenta una query per gli attributi personalizzati in un metodo o un tipo.

## <a name="syntax"></a>Sintassi

```
IDebugCustomAttributeQuery : IUnknown
```

## <a name="methods"></a>Metodi
 Questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[GetCustomAttributeByName](../../../extensibility/debugger/reference/idebugcustomattributequery-getcustomattributebyname.md)|Recupera un attributo personalizzato in base al nome.|
|[IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery-iscustomattributedefined.md)|Determina se l'attributo personalizzato specificato è definito.|

## <a name="requirements"></a>Requisiti
 Intestazione: Sh.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll
