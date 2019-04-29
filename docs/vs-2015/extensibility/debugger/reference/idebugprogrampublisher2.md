---
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 3cad86071904b2af4c22a2cb1a0ef67d7de95d84
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431459"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Questa interfaccia consente a un motore di debug (DE) o fornitori di porte personalizzato per registrare i programmi per il debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugProgramPublisher2 : IUnknown  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Visual Studio implementa questa interfaccia per registrare i programmi in fase di debug per renderle visibili per il debug tra più processi.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Chiamare COM `CoCreateInstance` utilizzabile con `CLSID_ProgramPublisher` per ottenere questa interfaccia (vedere l'esempio). Un CRI o un fornitore di porte personalizzato Usa questa interfaccia per registrare automaticamente i nodi che rappresentano i programmi in fase di debug.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Rende un nodo di programma disponibile per DEs e la sessione di debug manager (SDM).|  
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Rimuove un nodo di programma in modo che non è più disponibile.|  
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Rende disponibile un programma per DEs e il modello SDM.|  
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Rimuove un programma in modo che non è più disponibile.|  
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Imposta un flag che indica che è presente un debugger.|  
  
## <a name="remarks"></a>Note  
 Questa interfaccia sono disponibili i programmi e i nodi di programma (vale a dire, "pubblica" li) da usare per DEs e gestore di sessione di debug (SDM). Per accedere a programmi pubblicati e nodi di programma, usare il [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaccia. Questo è l'unico modo che Visual Studio è in grado di riconoscere che un programma viene eseguito il debug.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="example"></a>Esempio  
 In questo esempio viene illustrato come creare un'istanza server di pubblicazione programma e registrare un nodo di programma. Ciò è tratto dall'esercitazione [nodo il programma di pubblicazione](http://msdn.microsoft.com/d0100e02-4e2b-4e72-9e90-f7bc11777bae).  
  
```cpp#  
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
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)
