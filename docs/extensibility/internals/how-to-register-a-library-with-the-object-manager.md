---
title: 'Procedura: Registrare una libreria con Gestione oggetti Documenti Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- libraries, registering with object manager
- IVsLibrary2 interface, registering library with object manager
- IVsSimpleLibrary2 interface, registering library with object manager
- IVsObjectManager2 interface, registering library with object manager
- libraries, symbol-browsing tools
ms.assetid: f124dd05-cb0f-44ad-bb2a-7c0b34ef4038
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4bd1032d2ba67a0c0f3338560a80038ed3215531
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707937"
---
# <a name="how-to-register-a-library-with-the-object-manager"></a>Procedura: registrare una libreria con il gestore di oggettiHow to: Register a library with the object manager
Gli strumenti di esplorazione dei simboli, ad esempio **Visualizzazione classi**, **Visualizzatore oggetti**, **Visualizzatore chiamate** e Trova risultati **simbolo**, consentono di visualizzare i simboli nel progetto o in componenti esterni. I simboli includono spazi dei nomi, classi, interfacce, metodi e altri elementi del linguaggio. Le librerie tengono traccia di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] questi simboli e li espongono al gestore di oggetti che popola gli strumenti con i dati.

 Il gestore di oggetti tiene traccia di tutte le librerie disponibili. Ogni libreria deve registrarsi con il gestore di oggetti prima di fornire i simboli per gli strumenti di esplorazione dei simboli.

 In genere, si registra una libreria quando viene caricato un pacchetto VSPackage. Tuttavia, può essere fatto in un altro momento in base alle esigenze. Annullare la registrazione della libreria quando il pacchetto VSPackage viene arrestato.

 Per registrare una <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterLibrary%2A> libreria, utilizzare il metodo . Per una libreria di <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> codice gestito, utilizzare il metodo .

 Per annullare la registrazione <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> di una libreria, utilizzare il metodo .

 Per ottenere un riferimento al <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2>gestore <xref:Microsoft.VisualStudio.Shell.Interop.SVsObjectManager> di `GetService` oggetti, passare l'ID del servizio al metodo .

## <a name="register-and-unregister-a-library-with-the-object-manager"></a>Registrare e annullare la registrazione di una libreria con il gestore di oggettiRegister and unregister a library with the object manager

### <a name="to-register-a-library-with-the-object-manager"></a>Per registrare una libreria con il gestore di oggetti

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

2. Ottenere un riferimento a <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> un oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.RegisterSimpleLibrary%2A> del tipo e chiamare il metodo .

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

### <a name="to-unregister-a-library-with-the-object-manager"></a>Per annullare la registrazione di una libreria con il gestore di oggetti

1. Ottenere un riferimento a <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2> un oggetto <xref:Microsoft.VisualStudio.Shell.Interop.IVsObjectManager2.UnregisterLibrary%2A> del tipo e chiamare il metodo .

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

## <a name="see-also"></a>Vedere anche
- [Estendibilità del servizio di linguaggio legacyLegacy language service extensibility](../../extensibility/internals/legacy-language-service-extensibility.md)
- [Supporta gli strumenti di esplorazione dei simboli](../../extensibility/internals/supporting-symbol-browsing-tools.md)
- [Procedura: esporre elenchi di simboli forniti dalla libreria al gestore di oggettiHow to: Expose lists of symbols provided by the library to the object manager](../../extensibility/internals/how-to-expose-lists-of-symbols-provided-by-the-library-to-the-object-manager.md)
