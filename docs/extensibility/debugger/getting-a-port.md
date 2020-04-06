---
title: Ottenere una porta Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf4948e7cb2590136774eab76fbafec91dbfa40
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738639"
---
# <a name="get-a-port"></a>Ottenere una portaGet a port
Una porta rappresenta una connessione a un computer in cui sono in esecuzione processi. Tale computer potrebbe essere il computer locale o un computer remoto (che potrebbe essere in esecuzione un sistema operativo non basato su Windows; vedere [Porte](../../extensibility/debugger/ports.md) per ulteriori informazioni).

Una porta è rappresentata dal [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia. Viene utilizzato per ottenere informazioni sui processi in esecuzione sulla macchina a cui è collegata la porta.

Un motore di debug deve accedere a una porta per registrare i nodi di programma con la porta e soddisfare le richieste di informazioni sul processo. Ad esempio, se il motore di debug implementa il [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) interfaccia, l'implementazione per il [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metodo potrebbe richiedere la porta per le informazioni sul processo necessarie da restituire.

Visual Studio fornisce la porta necessaria al motore di debug e ottiene questa porta da un fornitore di porta. Se un programma è collegato (dall'interno del debugger o a causa di un'eccezione è stata generata, che attiva la finestra di dialogo Just-in-Time [JIT]), all'utente viene data la scelta del trasporto (un altro nome per un fornitore di porta) da utilizzare. In caso contrario, se l'utente avvia il programma dall'interno del debugger, il sistema del progetto specifica il fornitore della porta da utilizzare. In entrambi gli eventi, Visual Studio crea un'istanza del fornitore della porta, rappresentato da un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaccia e richiede una nuova porta chiamando [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) con un [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) interfaccia. Questa porta viene quindi passata al motore di debug in un form o in un altro.

## <a name="example"></a>Esempio
In questo frammento di codice viene illustrato come utilizzare la porta fornita a [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) per registrare un nodo di programma in [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). I parametri non direttamente correlati a questo concetto sono stati omessi per chiarezza.

> [!NOTE]
> In questo esempio viene utilizzata la porta per avviare e riprendere il processo e si presuppone che il [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) interfaccia viene implementata sulla porta. Questo non è affatto l'unico modo per eseguire queste attività ed è possibile che la porta non sia nemmeno coinvolta se non avere [il programma IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) dato ad esso.

```cpp
// This is an IDebugEngineLaunch2 method.
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,
                                      IDebugPort2 *pPort,
                                      /* omitted parameters */,
                                      IDebugProcess2**ppDebugProcess)
{
    // do stuff here to set up for a launch (such as handling the other parameters)
    ...

    // Now get the IPortNotify2 interface so we can register a program node
    // in CDebugEngine::ResumeProcess.
    CComPtr<IDebugDefaultPort2> spDefaultPort;
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);
    if (SUCCEEDED(hr))
    {
        CComPtr<IDebugPortNotify2> spPortNotify;
        hr = spDefaultPort->GetPortNotify(&spPortNotify);
        if (SUCCEEDED(hr))
        {
            // Remember the port notify so we can use it in ResumeProcess.
            m_spPortNotify = spPortNotify;

            // Now launch the process in a suspended state and return the
            // IDebugProcess2 interface
            CComPtr<IDebugPortEx2> spPortEx;
            hr = pPort->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                // pass on the parameters we were given (omitted here)
                hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)
            }
        }
    }
    return(hr);
}

HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)
{
    // Make a program node for this process
    HRESULT hr;
    CComPtr<IDebugProgramNode2> spProgramNode;
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);
    if (SUCCEEDED(hr))
    {
        hr = m_spPortNotify->AddProgramNode(spProgramNode);
        if (SUCCEEDED(hr))
        {
            // resume execution of the process using the port given to us earlier.
            // (Querying for the IDebugPortEx2 interface is valid here since
            // that's how we got the IDebugPortNotify2 interface in the first place.)
            CComPtr<IDebugPortEx2> spPortEx;
            hr = m_spPortNotify->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>Vedere anche
- [Registrazione del programma](../../extensibility/debugger/registering-the-program.md)
- [Abilitazione del debug di un programma](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Fornitori portuali](../../extensibility/debugger/port-suppliers.md)
- [Ports](../../extensibility/debugger/ports.md)
