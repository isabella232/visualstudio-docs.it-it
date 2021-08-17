---
description: Questa interfaccia enumera i contesti di codice associati alla sessione di debug o a un programma o documento specifico.
title: IEnumDebugCodeContexts2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IEnumDebugCodeContexts2
helpviewer_keywords:
- IEnumDebugCodeContexts2
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 8b52be981dbda8bb3b73fc2596dc8988e021765d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122095621"
---
# <a name="ienumdebugcodecontexts2"></a>IEnumDebugCodeContexts2
Questa interfaccia enumera i contesti di codice associati alla sessione di debug o a un programma o documento specifico.

## <a name="syntax"></a>Sintassi

```
IEnumDebugCodeContexts2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
 Il motore di debug implementa questa interfaccia per rappresentare un elenco di contesti di codice per una particolare posizione di testo in un programma o un elenco di contesti di codice per un contesto di documento specifico.

## <a name="notes-for-callers"></a>Note per i chiamanti
 Chiamare [EnumCodeContexts per](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) ottenere questa interfaccia che rappresenta un elenco di contesti di codice per una posizione di testo specifica nel documento di origine di un programma.

 Chiamare [EnumCodeContexts per](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) ottenere questa interfaccia che rappresenta un elenco di tutti i contesti di codice in un documento di origine specifico.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable
 Nella tabella seguente vengono illustrati i metodi di `IEnumDebugCodeContexts2` .

|Metodo|Descrizione|
|------------|-----------------|
|[Avanti](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Recupera un numero specificato di contesti di codice in una sequenza di enumerazione.|
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Ignora un numero specificato di contesti di codice in una sequenza di enumerazione.|
|[Reimpostazione](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Riporta all'inizio la sequenza di enumerazione.|
|[Clone](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Ottiene il numero di contesti di codice in un enumeratore.|

## <a name="remarks"></a>Commenti
 Visual Studio chiama [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) per popolare un elenco di contesti di codice tra cui l'utente può scegliere quando imposta l'istruzione successiva o visualizza il disassembly per un file di origine. Possono verificarsi più contesti di codice, ad esempio quando sono presenti più istanze di un modello di tipo C++.

## <a name="requirements"></a>Requisiti
 Intestazione: msdbg.h

 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)
- [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)
