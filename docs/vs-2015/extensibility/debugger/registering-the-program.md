---
title: Il programma di registrazione | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 484aa854a8e0987bf034e829a3acf02d6d637870
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60042651"
---
# <a name="registering-the-program"></a>Registrazione del programma
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Dopo che il motore di debug ha acquisito una porta, rappresentato da un [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) interfaccia, il passaggio successivo di abilitare il programma da sottoporre a debug è registrarlo con la porta. Una volta registrato, il programma è disponibile per il debug di uno dei seguenti modi:  
  
- Il processo di collegamento, che consente al debugger di ottenere il completo controllo debug di un'applicazione in esecuzione.  
  
- Just-in-time (JIT) esegue il debug, che consente il debug dopo i fatti di un programma che viene eseguito indipendentemente da un debugger. Quando l'architettura runtime rileva un errore, il debugger riceve una notifica prima del sistema operativo o ambiente di runtime Rilascia risorse di memoria e del programma di errore.  
  
## <a name="registering-procedure"></a>La procedura di registrazione  
  
#### <a name="to-register-your-program"></a>Per registrare il programma  
  
1. Chiamare il [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) metodo implementato dalla porta.  
  
     `IDebugPortNotify2::AddProgramNode` richiede un puntatore a un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia.  
  
     In genere, quando il sistema operativo o un ambiente di runtime carica un programma, viene creato il nodo di programma. Se il motore di debug (DE) viene richiesto di caricare il programma per la Germania crea e registra il nodo di programma.  
  
     L'esempio seguente illustra il motore di debug, l'avvio del programma e registrandolo con una porta.  
  
    > [!NOTE]
    >  Ciò non è l'unico modo per avviare e riprendere un processo. si tratta principalmente un esempio di registrazione di un programma con una porta.  
  
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
 [Recupero di una porta](../../extensibility/debugger/getting-a-port.md)   
 [Abilitazione di un programma da sottoporre a debug](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
