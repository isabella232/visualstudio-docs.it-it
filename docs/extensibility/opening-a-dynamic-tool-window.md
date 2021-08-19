---
title: Apertura di una finestra degli strumenti dinamica | Microsoft Docs
description: Informazioni sulle finestre degli strumenti dinamiche, che si apre ogni volta che un contesto dell'interfaccia utente specifico viene applicato e chiuso quando il contesto dell'interfaccia utente non è più applicabile.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 34435f3427296d9a82291275c2b74438ee60e669
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122158490"
---
# <a name="open-a-dynamic-tool-window"></a>Aprire una finestra degli strumenti dinamica
Le finestre degli strumenti vengono in genere aperte da un comando di un menu o da un tasto di scelta rapida equivalente. A volte, tuttavia, potrebbe essere necessaria una finestra degli strumenti che si apre ogni volta che si applica un contesto dell'interfaccia utente specifico e si chiude quando il contesto dell'interfaccia utente non viene più applicato. Questi tipi di finestre degli strumenti sono denominati *dinamici* *o visibili automaticamente.*

> [!NOTE]
> Per un elenco dei contesti predefiniti dell'interfaccia utente, vedere <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> .

 Se si vuole aprire una finestra degli strumenti dinamica all'avvio ed è possibile che la creazione non riesca, è necessario implementare l'interfaccia e testare le condizioni di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> errore nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> metodo . Perché la shell sappia che è presente una finestra degli strumenti dinamica che deve essere aperta all'avvio, è necessario aggiungere il valore (impostato su 1) alla registrazione `SupportsDynamicToolOwner` del pacchetto. Questo valore non fa parte dello standard , quindi è necessario <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> creare un attributo personalizzato per aggiungerlo. Per altre informazioni sugli attributi personalizzati, vedere [Usare un attributo di registrazione personalizzato per registrare un'estensione](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).

 Usare <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> per aprire una finestra degli strumenti. La finestra degli strumenti viene creata in base alle esigenze.

> [!NOTE]
> Una finestra degli strumenti dinamica può essere chiusa dall'utente. Se si vuole creare un comando di menu in modo che l'utente possa riaprire la finestra degli strumenti, il comando di menu deve essere abilitato nello stesso contesto dell'interfaccia utente che apre la finestra degli strumenti e disabilitato in caso contrario.

## <a name="to-open-a-dynamic-tool-window"></a>Per aprire una finestra degli strumenti dinamica

1. Creare un progetto VSIX denominato **DynamicToolWindow** e aggiungere un modello di elemento della finestra degli strumenti *denominato DynamicWindowPane.cs.* Per altre informazioni, vedere [Creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

2. Nel file *DynamicWindowPanePackage.cs* trovare la dichiarazione DynamicWindowPanePackage. Aggiungere gli <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> attributi <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> e per registrare la finestra degli strumenti.

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

     Gli attributi precedenti registrano la finestra degli strumenti denominata DynamicWindowPane come finestra temporanea che non viene resa persistente quando Visual Studio viene chiuso e riaperto. DynamicWindowPane viene aperto ogni volta che <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> si applica e chiuso in caso contrario.

3. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale. La finestra degli strumenti non dovrebbe essere visualizzata.

4. Aprire un progetto nell'istanza sperimentale. Verrà visualizzata la finestra degli strumenti.
