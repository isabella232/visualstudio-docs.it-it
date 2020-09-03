---
title: Apertura di una finestra degli strumenti dinamica | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9a06cea6d9de4271572457dc9fe6473b5c969b66
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903717"
---
# <a name="open-a-dynamic-tool-window"></a>Aprire una finestra degli strumenti dinamica
Le finestre degli strumenti vengono in genere aperte da un comando in un menu o da un tasto di scelta rapida equivalente. In alcuni casi, tuttavia, potrebbe essere necessaria una finestra degli strumenti che si apre ogni volta che viene applicato un contesto dell'interfaccia utente specifico e si chiude quando il contesto dell'interfaccia utente non viene più applicato. Questi tipi di finestre degli strumenti sono denominati *dinamici* o *visibili automaticamente*.

> [!NOTE]
> Per un elenco dei contesti dell'interfaccia utente predefiniti, vedere <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> .

 Se si desidera aprire una finestra degli strumenti dinamica all'avvio ed è possibile che la creazione abbia esito negativo, è necessario implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> interfaccia e testare le condizioni di errore nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> metodo. Affinché la shell sappia di disporre di una finestra degli strumenti dinamica da aprire all'avvio, è necessario aggiungere il `SupportsDynamicToolOwner` valore (impostato su 1) alla registrazione del pacchetto. Questo valore non fa parte dello standard <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> , pertanto è necessario creare un attributo personalizzato per aggiungerlo. Per ulteriori informazioni sugli attributi personalizzati, vedere [utilizzo di un attributo di registrazione personalizzato per registrare un'estensione](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).

 Utilizzare <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> per aprire una finestra degli strumenti. La finestra degli strumenti viene creata in base alle esigenze.

> [!NOTE]
> Una finestra degli strumenti dinamica può essere chiusa dall'utente. Se si desidera creare un comando di menu che consente all'utente di riaprire la finestra degli strumenti, il comando di menu deve essere abilitato nello stesso contesto dell'interfaccia utente che apre la finestra degli strumenti e disabilitato in caso contrario.

## <a name="to-open-a-dynamic-tool-window"></a>Per aprire una finestra degli strumenti dinamica

1. Creare un progetto VSIX denominato **DynamicToolWindow** e aggiungere un modello di elemento della finestra degli strumenti denominato *DynamicWindowPane.cs*. Per altre informazioni, vedere [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

2. Nel file *DynamicWindowPanePackage.cs* trovare la dichiarazione DynamicWindowPanePackage. Aggiungere gli <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> attributi e per registrare la finestra degli strumenti.

    ```vb
    [ProvideToolWindow(typeof(DynamicWindowPane)]
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]
    [PackageRegistration(UseManagedResourcesOnly = true)]
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
    [ProvideMenuResource("Menus.ctmenu", 1)]
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]
    [Guid(DynamicWindowPanePackage.PackageGuidString)]
    public sealed class DynamicWindowPanePackage : Package
    {. . .}
    ```

     Gli attributi precedenti registrano la finestra degli strumenti denominata DynamicWindowPane come finestra temporanea che non viene resa persistente quando Visual Studio viene chiuso e riaperto. DynamicWindowPane viene aperto ogni volta che viene <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> applicato e chiuso in caso contrario.

3. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale. La finestra degli strumenti non dovrebbe essere visualizzata.

4. Aprire un progetto nell'istanza sperimentale. Verrà visualizzata la finestra degli strumenti.
