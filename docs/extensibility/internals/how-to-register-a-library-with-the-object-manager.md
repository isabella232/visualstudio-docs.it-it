---
title: 'Procedura: registrare una libreria con il gestore oggetti | Microsoft Docs'
description: Informazioni su come registrare una libreria con gestione oggetti di Visual Studio in modo che sia possibile visualizzare i simboli negli strumenti di esplorazione, ad esempio Visualizzazione classi e Visualizzatore oggetti.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a5f4e9805eec8fd5d0089f1b8348253523d9056f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99925013"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Procedura: registrare una libreria con gestione oggetti
Gli strumenti di esplorazione dei simboli, ad esempio **Visualizzazione classi**, **Visualizzatore oggetti**, **Visualizzatore chiamate** e **trovare i risultati dei** simboli, consentono di visualizzare i simboli nel progetto o in componenti esterni. I simboli includono spazi dei nomi, classi, interfacce, metodi e altri elementi del linguaggio. Le librerie consentono di tenere traccia di questi simboli ed esporli al [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestore oggetti che popola gli strumenti con i dati.

 Il gestore oggetti tiene traccia di tutte le librerie disponibili. Ogni libreria deve eseguire la registrazione con gestione oggetti prima di fornire simboli per gli strumenti di esplorazione dei simboli.

 In genere, si registra una libreria quando si carica un pacchetto VSPackage. Tuttavia, è possibile eseguire questa operazione in un altro momento in base alle esigenze. Si annulla la registrazione della libreria quando il pacchetto VSPackage viene arrestato.

 Per registrare una libreria, usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> metodo. Per una libreria di codice gestito, usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodo.

 Per annullare la registrazione di una libreria, utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> metodo.

 Per ottenere un riferimento a gestione oggetti, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> passare l'ID del <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> servizio al `GetService` metodo.

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Registrare e annullare la registrazione di una libreria con gestione oggetti

### <a name="to-register-a-library-with-the-object-manager"></a>Per registrare una libreria con gestione oggetti

1. Creare una libreria.

    ```vb
    Private m_CallBrowserLibrary As CallBrowser.Library = Nothing
    Private m_nLibraryCookie As UInteger = 0
    ' Create Library.
    m_CallBrowserLibrary = New CallBrowser.Library()
    ```

    ```csharp
    private CallBrowser.Library m_CallBrowserLibrary = null;
    private uint m_nLibraryCookie = 0;
    // Create Library.
    m_CallBrowserLibrary = new CallBrowser.Library();

    ```

2. Ottenere un riferimento a un oggetto del <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> tipo e chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodo.

    ```vb
    Private Sub RegisterLibrary()
        If m_nLibraryCookie <> 0 Then
            Throw New Exception("Library already registered with Object Manager")
        End If

        ' Obtain a reference to IVsObjectManager2 type object.
        Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
        If objManager Is Nothing Then
            Throw New NullReferenceException("GetService failed for SVsObjectManager")
        End If

        Try
            Dim hr As Integer = objManager.RegisterSimpleLibrary(m_CallBrowserLibrary, m_nLibraryCookie)
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr)
        Catch e As Exception
            ' Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message)
            Throw
        End Try
    End Sub
    ```

    ```csharp
    private void RegisterLibrary()
    {
        if (m_nLibraryCookie != 0)
            throw new Exception("Library already registered with Object Manager");

        // Obtain a reference to IVsObjectManager2 type object.
        IVsObjectManager2 objManager =
                          GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
        if (objManager == null)
            throw new NullReferenceException("GetService failed for SVsObjectManager");

        try
        {
            int hr =
                objManager.RegisterSimpleLibrary(m_CallBrowserLibrary,
                                                 out m_nLibraryCookie);
                Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(hr);
        }
        catch (Exception e)
        {
            // Code to handle any CLS-compliant exception.
            Trace.WriteLine(e.Message);
            throw;
        }
    }

    ```

### <a name="to-unregister-a-library-with-the-object-manager"></a>Per annullare la registrazione di una libreria con gestione oggetti

1. Ottenere un riferimento a un oggetto del <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> tipo e chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> metodo.

    ```vb
    Private Sub UnregisterLibrary()
        If m_nLibraryCookie <> 0 Then
            ' Obtain a reference to IVsObjectManager2 type object.
            Dim objManager As IVsObjectManager2 = TryCast(GetService(GetType(SVsObjectManager)), IVsObjectManager2)
            If objManager Is Nothing Then
                Throw New NullReferenceException("GetService failed for SVsObjectManager")
            End If

            Try
                objManager.UnregisterLibrary(m_nLibraryCookie)
            Catch e As Exception
                ' Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message)
                Throw
            Finally
                m_nLibraryCookie = 0
            End Try
        End If
    End Sub
    ```

    ```csharp
    private void UnregisterLibrary()
    {
        if (m_nLibraryCookie != 0)
        {
            // Obtain a reference to IVsObjectManager2 type object.
            IVsObjectManager2 objManager = GetService(typeof(SVsObjectManager)) as IVsObjectManager2;
            if (objManager == null)
                throw new NullReferenceException("GetService failed for SVsObjectManager");

            try
            {
                objManager.UnregisterLibrary(m_nLibraryCookie);
            }
            catch (Exception e)
            {
                // Code to handle any CLS-compliant exception.
                Trace.WriteLine(e.Message);
                throw;
            }
            finally
            {
                m_nLibraryCookie = 0;
            }
        }
    }

    ```

## <a name="see-also"></a>Vedi anche
- [Estendibilità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Supporto degli strumenti per l'esplorazione di simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Procedura: esporre elenchi di simboli forniti dalla libreria al gestore oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
