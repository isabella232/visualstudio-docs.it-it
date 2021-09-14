---
title: "Procedura: Registrare una libreria con l'istanza di Object Manager | Microsoft Docs"
description: Informazioni su come registrare una libreria con Visual Studio object manager per poter visualizzare i simboli negli strumenti di esplorazione, ad esempio Visualizzazione classi e Visualizzatore oggetti.
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
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c70a59cd6510b761ce1cf44bc3d6d66d5766efe5
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709552"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Procedura: Registrare una libreria con gestione oggetti
Gli strumenti di esplorazione dei simboli, ad esempio **Visualizzazione classi** **,** Visualizzatore oggetti , **Visualizzatore chiamate** e Risultati ricerca **simboli**, consentono di visualizzare i simboli nel progetto o nei componenti esterni. I simboli includono spazi dei nomi, classi, interfacce, metodi e altri elementi del linguaggio. Le librerie rilevano questi simboli ed esporli al gestore oggetti che [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] popola gli strumenti con i dati.

 Gestione oggetti tiene traccia di tutte le librerie disponibili. Ogni libreria deve registrarsi con object manager prima di fornire simboli per gli strumenti di esplorazione dei simboli.

 In genere, si registra una libreria quando viene caricato un vspackage. Tuttavia, può essere eseguita in un altro momento in base alle esigenze. La registrazione della libreria viene annullata all'arresto del pacchetto VSPackage.

 Per registrare una libreria, usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> metodo . Per una libreria di codice gestito, usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> metodo .

 Per annullare la registrazione di una libreria, usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> metodo .

 Per ottenere un riferimento al gestore oggetti, <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> passare <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> l'ID servizio al metodo `GetService` .

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Registrare e annullare la registrazione di una libreria con object manager

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

2. Ottenere un riferimento a un oggetto del <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> tipo e chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> .

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

1. Ottenere un riferimento a un oggetto del <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> tipo e chiamare il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> .

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
- [Supporto degli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Procedura: Esporre gli elenchi di simboli forniti dalla libreria al gestore oggetti](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
