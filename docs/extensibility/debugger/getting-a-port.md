---
title: Recupero di una porta | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f44ffa801ba9b76010466ca8884a36217f843b55
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231568"
---
# <a name="get-a-port"></a>Ottenere una porta
Una porta rappresenta una connessione a un computer in cui i processi in esecuzione. Tale computer potrebbe essere il computer locale o in un computer remoto (che potrebbe eventualmente essere con sistema operativo non basate su Windows, vedere [porte](../../extensibility/debugger/ports.md) per altre informazioni).  
  
 Una porta è rappresentata dal [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia. Viene utilizzato per ottenere informazioni sui processi in esecuzione nel computer che la porta è connesso.  
  
 Un motore di debug deve avere accesso a una porta per poter registrare i nodi di programma con la porta e per soddisfare le richieste di informazioni sul processo. Ad esempio, se il motore di debug implementa il [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) dell'interfaccia, l'implementazione per il [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) metodo può chiedere la porta per il processo necessario informazioni da restituire.  
  
 Visual Studio fornisce la porta necessaria per il motore di debug e ottiene questa porta da un fornitore di porte. Se un programma è collegato a (all'interno del debugger o a causa di un'eccezione viene generata, che attiva la finestra di dialogo [JIT] Just-in-Time), l'utente ha la scelta dei trasporti (un altro nome per un fornitore di porte) da usare. In caso contrario, se l'utente avvia il programma all'interno del debugger, il sistema di progetto specifica il fornitore della porta da usare. In entrambi i casi Visual Studio crea il fornitore della porta, rappresentato da un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) dell'interfaccia e richiede una nuova porta chiamando [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) con un [ IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) interfaccia. Questa porta viene quindi passata al motore di debug in un form o in un altro.  
  
## <a name="example"></a>Esempio  
 Questo frammento di codice viene illustrato come utilizzare la porta fornita da [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) per registrare un nodo programma [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parametri non direttamente correlati a questo concetto sono stati omessi per maggiore chiarezza.  
  
> [!NOTE]
>  Questo esempio Usa la porta per avviare e riprendere il processo e si presuppone che il [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) interfaccia è implementata sulla porta. Si tratta in alcun modo l'unico modo per eseguire queste attività ed è possibile che la porta non ancora coinvolto diverso da disporre del programma [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) assegnato a esso.  
  
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
                hr = spPortEx->LaunchSuspended(/* omitted paramters */,ppDebugProcess)  
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
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Registrazione del programma](../../extensibility/debugger/registering-the-program.md)   
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)   
 [Porte](../../extensibility/debugger/ports.md)