---
description: Questa interfaccia consente a un motore di debug (DE) o a fornitori di porte personalizzati di registrare i programmi per il debug.
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 2a3ba004fdce8b82fedf7dc2e2205b56ba52ff29
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122126336"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Questa interfaccia consente a un motore di debug (DE) o a fornitori di porte personalizzati di registrare i programmi per il debug.

## <a name="syntax"></a>Sintassi

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Visual Studio questa interfaccia per registrare i programmi di cui viene eseguito il debug per renderli visibili per il debug in più processi.

## <a name="notes-for-callers"></a>Note per i chiamanti
Chiamare la funzione di COM `CoCreateInstance` con per ottenere questa interfaccia `CLSID_ProgramPublisher` (vedere l'esempio). Un de o un fornitore di porte personalizzato usa questa interfaccia per registrare i nodi del programma che rappresentano i programmi in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
Questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Rende disponibile un nodo di programma per le DE e la gestione del debug di sessione (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Rimuove un nodo di programma in modo che non sia più disponibile.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Rende disponibile un programma per DE e SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Rimuove un programma in modo che non sia più disponibile.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Imposta un flag che indica che è presente un debugger.|

## <a name="remarks"></a>Commenti
Questa interfaccia rende i programmi e i nodi di programma disponibili (ovvero li "pubblica") per l'uso da parte di DE e gestione del debug di sessione (SDM). Per accedere ai programmi pubblicati e ai nodi di programma, usare [l'interfaccia IDebugProgramProvider2.](../../../extensibility/debugger/reference/idebugprogramprovider2.md) Questo è l'unico modo Visual Studio riconoscere che è in corso il debug di un programma.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio
Questo esempio illustra come creare un'istanza dell'autore del programma e registrare un nodo di programma. Questo è tratto dall'esercitazione Pubblicazione [del nodo del programma](/previous-versions/bb161795(v=vs.90)).

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>Vedi anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
