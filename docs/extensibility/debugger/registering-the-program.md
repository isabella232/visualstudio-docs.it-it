---
title: Registrazione del programma | Microsoft Docs
description: Informazioni su come registrare un programma di cui eseguire il debug con una porta dopo che il motore di debug ha acquisito una porta.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- programs, registration
- debugging [Debugging SDK], program registration
ms.assetid: d726a161-7db3-4ef4-b258-9f6a5be68418
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 01566034b0cfece39367afdc1f86101c5ec553f8612bd469b90615ffc5b99fd9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377041"
---
# <a name="register-the-program"></a>Registrare il programma
Dopo che il motore di debug ha acquisito una porta, rappresentata da [un'interfaccia IDebugPort2,](../../extensibility/debugger/reference/idebugport2.md) il passaggio successivo per abilitare il debug del programma consiste nel registrarlo con la porta. Una volta registrato, il programma è disponibile per il debug in uno dei modi seguenti:

- Processo di connessione, che consente al debugger di ottenere il controllo completo del debug di un'applicazione in esecuzione.

- Debug JIT( Just-In-Time), che consente il debug dopo il fatto di un programma eseguito indipendentemente da un debugger. Quando l'architettura di runtime rileva un errore, il debugger viene avvisato prima che il sistema operativo o l'ambiente di runtime rilasci la memoria e le risorse del programma in errore.

## <a name="registering-procedure"></a>Procedura di registrazione

### <a name="to-register-your-program"></a>Per registrare il programma

1. Chiamare il [metodo AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md) implementato dalla porta.

     `IDebugPortNotify2::AddProgramNode`richiede un puntatore a [un'interfaccia IDebugProgramNode2.](../../extensibility/debugger/reference/idebugprogramnode2.md)

     In genere, quando il sistema operativo o l'ambiente di run-time carica un programma, viene creato il nodo del programma. Se viene richiesto al motore di debug (DE) di caricare il programma, de crea e registra il nodo del programma.

     Nell'esempio seguente viene illustrato il motore di debug che avvia il programma e lo registra con una porta.

    > [!NOTE]
    > Questo esempio di codice non è l'unico modo per avviare e riprendere un processo. Questo codice è principalmente un esempio di registrazione di un programma con una porta.

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
                    hr  = spPortEx->ResumeProcess(pDebugProcess);
                }
            }
        }
        return(hr);
    }

    ```

## <a name="see-also"></a>Vedi anche
- [Recupero di una porta](../../extensibility/debugger/getting-a-port.md)
- [Abilitazione del debug di un programma](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
