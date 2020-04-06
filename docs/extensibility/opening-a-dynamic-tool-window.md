---
title: Apertura di una finestra degli strumenti dinamica Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ff971f980b0a9b2fb0e22f56fb0ace752829c2c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702255"
---
# <a name="open-a-dynamic-tool-window"></a>Aprire una finestra degli strumenti dinamica
Le finestre degli strumenti vengono in genere aperte da un comando di un menu o da una scelta rapida da tastiera equivalente. A volte, tuttavia, potrebbe essere necessaria una finestra degli strumenti che si apre ogni volta che si applica un contesto dell'interfaccia utente specifico e si chiude quando il contesto dell'interfaccia utente non è più applicabile. Questi tipi di finestre degli strumenti sono denominati *dinamici* o *visibili automaticamente*.

> [!NOTE]
> Per un elenco di contesti <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>dell'interfaccia utente predefiniti, vedere .

 Se si desidera aprire una finestra degli strumenti dinamica all'avvio <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> ed è possibile che la creazione abbia esito negativo, è necessario implementare l'interfaccia e testare le condizioni di errore nel metodo. Affinché la shell sappia che si dispone di una finestra degli strumenti `SupportsDynamicToolOwner` dinamica che deve essere aperta all'avvio, è necessario aggiungere il valore (impostato su 1) alla registrazione del pacchetto. Questo valore non fa <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>parte dello standard, pertanto è necessario creare un attributo personalizzato per aggiungerlo. Per ulteriori informazioni sugli attributi personalizzati, vedere [Utilizzare un attributo di registrazione personalizzato per registrare un'estensione](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).

 Utilizzare <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> per aprire una finestra degli strumenti. La finestra degli strumenti viene creata in base alle esigenze.

> [!NOTE]
> Una finestra degli strumenti dinamica può essere chiusa dall'utente. Se si desidera creare un comando di menu in modo che l'utente possa riaprire la finestra degli strumenti, il comando di menu deve essere abilitato nello stesso contesto dell'interfaccia utente che apre la finestra degli strumenti e disabilitato in caso contrario.

## <a name="to-open-a-dynamic-tool-window"></a>Per aprire una finestra degli strumenti dinamicaTo open a dynamic tool window

1. Creare un progetto VSIX denominato **DynamicToolWindow** e aggiungere un modello di elemento della finestra degli strumenti denominato *DynamicWindowPane.cs*. Per ulteriori informazioni, consultate [Creare un'estensione con una finestra degli strumenti.](../extensibility/creating-an-extension-with-a-tool-window.md)

2. Nel *file DynamicWindowPanePackage.cs* individuare la dichiarazione DynamicWindowPanePackage.In the DynamicWindowPanePackage.cs file, find the DynamicWindowPanePackage declaration. Aggiungere <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> gli <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> attributi e per registrare la finestra degli strumenti.

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

     Gli attributi precedenti registrano la finestra degli strumenti denominata DynamicWindowPane come finestra temporanea che non viene mantenuta quando Visual Studio viene chiuso e riaperto. DynamicWindowPane viene <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> aperto ogni volta che si applica e chiuso in caso contrario.

3. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale. La finestra degli strumenti non dovrebbe essere visualizzata.

4. Aprire un progetto nell'istanza sperimentale. Verrà visualizzata la finestra degli strumenti.
