---
title: Proprietà IDebugProgramPublisher2 . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b17f5bab02e49951eb1647af95641af807c44863
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721532"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Questa interfaccia consente a un motore di debug (DE) o ai fornitori di porte personalizzate di registrare i programmi per il debug.

## <a name="syntax"></a>Sintassi

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Note per gli implementatori
Visual Studio implementa questa interfaccia per registrare i programmi in fase di debug per renderli visibili per il debug tra più processi.

## <a name="notes-for-callers"></a>Note per i chiamanti
Chiamare la `CoCreateInstance` funzione `CLSID_ProgramPublisher` di COM con per ottenere questa interfaccia (vedere l'esempio). Un DE o un fornitore di porta personalizzato utilizza questa interfaccia per registrare i nodi di programma che rappresentano i programmi in fase di debug.

## <a name="methods-in-vtable-order"></a>Metodi in ordine Vtable
Questa interfaccia implementa i metodi seguenti:This interface implements the following methods:

|Metodo|Descrizione|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Rende un nodo di programma disponibile per i DE e il gestore di sessione di debug (SDM).|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Rimuove un nodo di programma in modo che non sia più disponibile.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Rende disponibile un programma per i DOS e il Sistema SDM.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Rimuove un programma in modo che non sia più disponibile.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Imposta un flag che indica che è presente un debugger.|

## <a name="remarks"></a>Osservazioni
Questa interfaccia rende disponibili programmi e nodi di programma (ovvero, "pubblica") per l'utilizzo da parte di DE e del gestore di debug della sessione (SDM). Per accedere ai programmi pubblicati e ai nodi di programma, utilizzare il [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaccia. Questo è l'unico modo in cui Visual Studio è in grado di riconoscere che è in corso il debug di un programma.

## <a name="requirements"></a>Requisiti
Intestazione: msdbg.h

Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop

Assembly: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Esempio
In questo esempio viene illustrato come creare un'istanza dell'autore del programma e registrare un nodo di programma. Questa operazione è tratta dall'Esercitazione, [Pubblicazione del nodo del programma](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

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

## <a name="see-also"></a>Vedere anche
- [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
