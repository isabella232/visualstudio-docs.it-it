---
title: Gestione delle distribuzioni specializzate | Microsoft Docs
description: Informazioni su come gestire la distribuzione specializzata di un progetto di applicazione in Visual Studio. Ad esempio, una distribuzione in un server Web o in un dispositivo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- deploying applications [Visual Studio SDK]
- specialized deployment
ms.assetid: de068b6a-e806-45f0-9dec-2458fbb486f7
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 88cb63133cbe3dbe8c41c64cdae1f0bdc64ff5f9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122069913"
---
# <a name="handle-specialized-deployment"></a>Gestire la distribuzione specializzata
Una distribuzione è un'operazione facoltativa per i progetti. Un progetto Web, ad esempio, supporta una distribuzione per consentire a un progetto di aggiornare un server Web. Analogamente, un progetto **smart device** supporta una distribuzione per copiare un'applicazione compilata nel dispositivo di destinazione. Project sottotipi possono fornire un comportamento di distribuzione specializzato implementando <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> l'interfaccia . Questa interfaccia definisce un set completo di operazioni di distribuzione:

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A>

- <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A>

  L'operazione di distribuzione effettiva deve essere eseguita nel thread separato per rendere ancora [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] più reattiva l'interazione dell'utente. I metodi forniti da vengono chiamati in modo asincrono da e operano in background, consentendo all'ambiente di eseguire query sullo stato di un'operazione di distribuzione in qualsiasi momento o di arrestare l'operazione, <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] se necessario. Le <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg> operazioni di distribuzione dell'interfaccia vengono chiamate dall'ambiente quando l'utente seleziona il comando deploy.

  Per notificare all'ambiente che un'operazione di distribuzione è iniziata o terminata, il sottotipo di progetto deve chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnStartDeploy%2A> i metodi e <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployStatusCallback.OnEndDeploy%2A> .

## <a name="to-handle-a-specialized-deployment-by-a-subtype-project"></a>Per gestire una distribuzione specializzata da un progetto di sottotipo

- Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.AdviseDeployStatusCallback%2A> metodo per registrare l'ambiente per ricevere notifiche degli eventi di stato della distribuzione.

    ```vb
    Private adviseSink As Microsoft.VisualStudio.Shell.EventSinkCollection = New Microsoft.VisualStudio.Shell.EventSinkCollection()
    Public Function AdviseDeployStatusCallback(ByVal pIVsDeployStatusCallback As IVsDeployStatusCallback, _
                                               ByRef pdwCookie As UInteger) As Integer

        If pIVsDeployStatusCallback Is Nothing Then
            Throw New ArgumentNullException("pIVsDeployStatusCallback")
        End If

        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback)
        Return VSConstants.S_OK

    End Function
    ```

    ```csharp
    private Microsoft.VisualStudio.Shell.EventSinkCollection adviseSink = new Microsoft.VisualStudio.Shell.EventSinkCollection();
    public int AdviseDeployStatusCallback(IVsDeployStatusCallback pIVsDeployStatusCallback,
                                          out uint pdwCookie)
    {
        if (pIVsDeployStatusCallback == null)
            throw new ArgumentNullException("pIVsDeployStatusCallback");

        pdwCookie = adviseSink.Add(pIVsDeployStatusCallback);
        return VSConstants.S_OK;
    }

    ```

- Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.UnadviseDeployStatusCallback%2A> il metodo per annullare la registrazione dell'ambiente per ricevere notifiche degli eventi di stato della distribuzione.

    ```vb
    Public Function UnadviseDeployStatusCallback(ByVal dwCookie As UInteger) As Integer
        adviseSink.RemoveAt(dwCookie)
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int UnadviseDeployStatusCallback(uint dwCookie)
    {
        adviseSink.RemoveAt(dwCookie);
        return VSConstants.S_OK;
    }

    ```

- Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Commit%2A> il metodo per eseguire l'operazione di commit specifica dell'applicazione.  Questo metodo viene usato principalmente per la distribuzione del database.

    ```vb
    Public Function Commit(ByVal dwReserved As UInteger) As Integer
        'Implement commit operation here.
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int Commit(uint dwReserved)
    {
         //Implement commit operation here.
         return VSConstants.S_OK;
    }

    ```

- Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.Rollback%2A> metodo per eseguire un'operazione di rollback. Quando viene chiamato questo metodo, il progetto di distribuzione deve eseguire le operazioni appropriate per eseguire il rollback delle modifiche e ripristinare lo stato del progetto. Questo metodo viene usato principalmente per la distribuzione del database.

    ```vb
    Public Function Commit(ByVal dwReserved As UInteger) As Integer
        'Implement commit operation here.
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int Rollback(uint dwReserved)
    {
        //Implement Rollback operation here.
        return VSConstants.S_OK;
    }

    ```

- Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStartDeploy%2A> il metodo per determinare se un progetto è in grado di avviare o meno un'operazione di distribuzione.

    ```vb
    Public Function QueryStartDeploy(ByVal dwOptions As UInteger, ByVal pfSupported As Integer(), ByVal pfReady As Integer()) As Integer
        If Not pfSupported Is Nothing AndAlso pfSupported.Length > 0 Then
            pfSupported(0) = 1
        End If
        If Not pfReady Is Nothing AndAlso pfReady.Length > 0 Then
            pfReady(0) = 0
            If Not deploymentThread Is Nothing AndAlso (Not deploymentThread.IsAlive) Then
                pfReady(0) = 1
            End If
        End If
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int QueryStartDeploy(uint dwOptions, int[] pfSupported, int[] pfReady)
    {
        if (pfSupported != null && pfSupported.Length >0)
            pfSupported[0] = 1;
        if (pfReady != null && pfReady.Length >0)
        {
            pfReady[0] = 0;
            if (deploymentThread != null && !deploymentThread.IsAlive)
                pfReady[0] = 1;
        }
        return VSConstants.S_OK;
    }

    ```

- Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.QueryStatusDeploy%2A> il metodo per determinare se un'operazione di distribuzione è stata completata correttamente.

    ```vb
    Public Function QueryStatusDeploy(ByRef pfDeployDone As Integer) As Integer
        pfDeployDone = 1
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then
            pfDeployDone = 0
        End If
        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int QueryStatusDeploy(out int pfDeployDone)
    {
        pfDeployDone = 1;
        if (deploymentThread != null && deploymentThread.IsAlive)
            pfDeployDone = 0;
        return VSConstants.S_OK;
    }

    ```

- Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StartDeploy%2A> il metodo per avviare un'operazione di distribuzione in un thread separato. Inserire il codice specifico per la distribuzione dell'applicazione all'interno del `Deploy` metodo .

    ```vb
    Public Function StartDeploy(ByVal pIVsOutputWindowPane As IVsOutputWindowPane, ByVal dwOptions As UInteger) As Integer
        If pIVsOutputWindowPane Is Nothing Then
            Throw New ArgumentNullException("pIVsOutputWindowPane")
        End If

        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then
            Throw New NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first")
        End If

        outputWindow = pIVsOutputWindowPane

        ' Notify that deployment is about to begin and see if any user wants to cancel.
        If (Not NotifyStart()) Then
            Return VSConstants.E_ABORT
        End If

        operationCanceled = False

        ' Create and start our thread
        deploymentThread = New Thread(AddressOf Me.Deploy)
        deploymentThread.Name = "Deployment Thread"
        deploymentThread.Start()

        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int StartDeploy(IVsOutputWindowPane pIVsOutputWindowPane, uint dwOptions)
    {
        if (pIVsOutputWindowPane == null)
            throw new ArgumentNullException("pIVsOutputWindowPane");

        if (deploymentThread != null && deploymentThread.IsAlive)
            throw new NotSupportedException("Cannot start deployment operation when it is already started; Call QueryStartDeploy first");

        outputWindow = pIVsOutputWindowPane;

        // Notify that deployment is about to begin and see if any user wants to cancel.
        if (!NotifyStart())
            return VSConstants.E_ABORT;

        operationCanceled = false;

        // Create and start our thread
        deploymentThread = new Thread(new ThreadStart(this.Deploy));
        deploymentThread.Name = "Deployment Thread";
        deploymentThread.Start();

        return VSConstants.S_OK;
    }

    ```

- Implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsDeployableProjectCfg.StopDeploy%2A> metodo per arrestare un'operazione di distribuzione. Questo metodo viene chiamato quando un utente preme il **pulsante Annulla** durante il processo di distribuzione.

    ```vb
    Public Function StopDeploy(ByVal fSync As Integer) As Integer
        If Not deploymentThread Is Nothing AndAlso deploymentThread.IsAlive Then
            Return VSConstants.S_OK
        End If

        outputWindow.OutputStringThreadSafe("Canceling deployment")
        operationCanceled = True
        If fSync <> 0 Then
            ' Synchronous request, wait for the thread to terminate.
            If (Not deploymentThread.Join(10000)) Then
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread")
                deploymentThread.Abort()
            End If
        End If

        Return VSConstants.S_OK
    End Function
    ```

    ```csharp
    public int StopDeploy(int fSync)
    {
        if (deploymentThread != null && deploymentThread.IsAlive)
            return VSConstants.S_OK;

        outputWindow.OutputStringThreadSafe("Canceling deployment");
        operationCanceled = true;
        if (fSync != 0)
        {
            // Synchronous request, wait for the thread to terminate.
            if (!deploymentThread.Join(10000))
            {
                Debug.Fail("Deployment thread did not terminate before the timeout, Aborting thread");
                deploymentThread.Abort();
            }
        }

        return VSConstants.S_OK;
    }

    ```

> [!NOTE]
> Tutti gli esempi di codice forniti in questo argomento sono parti di un esempio più ampio negli [esempi di VSSDK](https://github.com/Microsoft/VSSDK-Extensibility-Samples).

## <a name="see-also"></a>Vedi anche
- [Project sottotipi](../../extensibility/internals/project-subtypes.md)
