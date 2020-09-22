---
title: Recupero di una porta | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f980c9d14bc2d0c9728f87374828cf690737429c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90840040"
---
# <a name="getting-a-port"></a>Recupero di una porta
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Una porta rappresenta una connessione a un computer in cui sono in esecuzione i processi. Il computer potrebbe essere il computer locale o un computer remoto, che potrebbe eseguire un sistema operativo non basato su Windows. per ulteriori informazioni, vedere [porte](../../extensibility/debugger/ports.md) .  
  
 Una porta è rappresentata dall'interfaccia [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) . Viene usato per ottenere informazioni sui processi in esecuzione nel computer a cui è connessa la porta.  
  
 Un motore di debug deve accedere a una porta per registrare i nodi del programma con la porta e per soddisfare le richieste di informazioni sul processo. Se, ad esempio, il motore di debug implementa l'interfaccia [IDebugProgramProvider2](../../extensibility/debugger/reference/idebugprogramprovider2.md) , l'implementazione per il metodo [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) potrebbe chiedere alla porta di restituire le informazioni necessarie sul processo.  
  
 Visual Studio fornisce la porta necessaria al motore di debug e ottiene la porta da un fornitore di porte. Se un programma è associato a (dall'interno del debugger o a causa di un'eccezione generata, che attiva la finestra di dialogo JIT (just-in-Time), l'utente ha la possibilità di scegliere il trasporto (un altro nome per un fornitore di porte) da usare. In caso contrario, se l'utente avvia il programma dall'interno del debugger, il sistema del progetto specifica il fornitore della porta da usare. In entrambi i casi, Visual Studio crea un'istanza del fornitore della porta, rappresentato da un'interfaccia [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) , e chiede una nuova porta chiamando [addport](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) con un'interfaccia [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) . Questa porta viene quindi passata al motore di debug in un form o in un'altra.  
  
## <a name="example"></a>Esempio  
 Questo frammento di codice illustra come usare la porta fornita a [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) per registrare un nodo di programma in [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). I parametri non direttamente correlati a questo concetto sono stati omessi per maggiore chiarezza.  
  
> [!NOTE]
> In questo esempio viene utilizzata la porta per avviare e riprendere il processo e si presuppone che l'interfaccia [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) sia implementata sulla porta. Questo non è l'unico modo per eseguire queste attività ed è possibile che la porta non sia nemmeno implicata come se fosse stata assegnata la [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) del programma.  
  
```cpp#  
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
                hr  = spPortEx->ResumeProcess(pDebugProcess);  
            }  
        }  
    }  
    return(hr);  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Registrazione del programma](../../extensibility/debugger/registering-the-program.md)   
 [Abilitazione di un programma di cui eseguire il debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)   
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)   
 [Ports](../../extensibility/debugger/ports.md)
