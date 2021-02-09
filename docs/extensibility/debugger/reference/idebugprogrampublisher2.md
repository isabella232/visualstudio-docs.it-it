---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 430cd05c66311971ad3cdbf60e170478810899ac
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99916191"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Questa interfaccia consente a un motore di debug (DE) o a un fornitore di porta personalizzato di registrare i programmi per il debug.

## <a name="syntax"></a>Sintassi

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Visual Studio implementa questa interfaccia per registrare i programmi di cui è in corso il debug, in modo da renderli visibili per il debug in più processi.

## <a name="notes-for-callers"></a>Note per i chiamanti
Chiamare `CoCreateInstance` la funzione com con `CLSID_ProgramPublisher` per ottenere questa interfaccia (vedere l'esempio). Un fornitore di porte o personalizzato usa questa interfaccia per registrare i nodi del programma che rappresentano i programmi di cui è in corso il debug.

## <a name="methods-in-vtable-order"></a>Metodi nell'ordine vtable
Questa interfaccia implementa i metodi seguenti:

|Metodo|Descrizione|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Rende disponibile un nodo di programma a DEs e a gestione debug sessione (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Rimuove un nodo di programma in modo che non sia più disponibile.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Rende disponibile un programma per DEs e SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Rimuove un programma in modo che non sia più disponibile.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Imposta un flag che indica che è presente un debugger.|

## <a name="remarks"></a>Commenti
Questa interfaccia rende disponibili i programmi e i nodi del programma (ovvero li pubblica) per l'uso da parte di DEs e gestione debug della sessione (SDM). Per accedere ai programmi e ai nodi del programma pubblicati, usare l'interfaccia [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) . Questo è l'unico modo in cui Visual Studio è in grado di riconoscere che è in corso il debug di un programma.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg. h

Spazio dei nomi: Microsoft. VisualStudio. Debugger. Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio
Questo esempio illustra come creare un'istanza dell'autore del programma e registrare un nodo del programma. Questa operazione viene eseguita nell'esercitazione [pubblicazione del nodo del programma](/previous-versions/bb161795(v=vs.90)).

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