---
description: IDebugProcessSecurity viene implementato da un fornitore di porte per avvisare l'utente che la connessione al processo non è sicura.
title: Interfaccia IDebugProcessSecurity | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugProcessSecurity interface
ms.assetid: 8a52ddca-bd99-49c0-9778-469dce7abd44
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: e97d498abbd7cbc650a0438a96570c172e5cf1d48031c92f8bef7b09de8f1860
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121338891"
---
# <a name="idebugprocesssecurity"></a>IDebugProcessSecurity
`IDebugProcessSecurity` viene implementato da un fornitore di porte per avvisare l'utente che il collegamento al processo non è sicuro.

## <a name="syntax"></a>Sintassi

```
IDebugProcessSecurity : IUnknown
```

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IDebugProcessSecurity` .

|Metodo|Descrizione|
|------------|-----------------|
|[GetUserName](../../../extensibility/debugger/reference/idebugprocesssecurity-getusername.md)|Ottiene il nome utente dal fornitore della porta.|
|[QueryCanSafelyAttach](../../../extensibility/debugger/reference/idebugprocesssecurity-querycansafelyattach.md)|Avvisa un utente che la connessione al processo di debug non è sicura.|

## <a name="remarks"></a>Commenti
 Implementare questa interfaccia per visualizzare un avviso e consentire all'utente di annullare se il processo a cui si sta collegando può essere considerato non sicuro.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Ports](../../../extensibility/debugger/ports.md)
- [Fornitori di porte](../../../extensibility/debugger/port-suppliers.md)
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
