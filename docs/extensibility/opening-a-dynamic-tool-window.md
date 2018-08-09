---
title: Aprire una finestra degli strumenti dinamica | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 9d37a72629dfb7c10eeb51bcd2317151447e9edd
ms.sourcegitcommit: 06db1892fff22572f0b0a11994dc547c2b7e2a48
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2018
ms.locfileid: "39636646"
---
# <a name="open-a-dynamic-tool-window"></a>Aprire una finestra degli strumenti dinamica
Finestre degli strumenti sono in genere aperte da un comando in un menu o un equivalente tasti di scelta rapida. In alcuni casi, tuttavia, potrebbe essere necessario una finestra degli strumenti visualizzata ogni volta che si applica un contesto dell'interfaccia utente specifico e si chiude quando il contesto dell'interfaccia utente non è più applicabile. Questi tipi di finestre degli strumenti sono chiamati *dinamici* oppure *visibili automaticamente*.  
  
> [!NOTE]
>  Per un elenco di contesti dell'interfaccia utente predefiniti, vedere <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT>.  
  
 Se si desidera aprire una finestra degli strumenti dinamici all'avvio ed è possibile che la creazione di esito negativo, è necessario implementare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> dell'interfaccia e testare le condizioni di errore nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> (metodo). Affinché la shell di sapere che si dispone di una finestra degli strumenti dinamica che deve essere aperta all'avvio, è necessario aggiungere il `SupportsDynamicToolOwner` valore (impostato su 1) per la registrazione del pacchetto. Questo valore non fa parte dello standard <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute>, pertanto è necessario creare un attributo personalizzato per aggiungerlo. Per altre informazioni sugli attributi personalizzati, vedere [usare un attributo di registrazione personalizzato per registrare un'estensione](../extensibility/registering-and-unregistering-vspackages.md#using-a-custom-registration-attribute-to-register-an-extension).  
  
 Usare <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> per aprire una finestra degli strumenti. La finestra degli strumenti viene creata in base alle esigenze.  
  
> [!NOTE]
>  Una finestra degli strumenti dinamica può essere chiusa dall'utente. Se si desidera creare un comando di menu in modo che l'utente è possibile riaprire la finestra degli strumenti, il comando di menu deve essere abilitato nello stesso contesto dell'interfaccia utente che apre la finestra degli strumenti e disabilitati in caso contrario.  
  
## <a name="to-open-a-dynamic-tool-window"></a>Per aprire una finestra degli strumenti dinamica  
  
1.  Creare un progetto VSIX denominato **DynamicToolWindow** e aggiungere un modello di elemento di finestra degli strumenti denominato *DynamicWindowPane.cs*. Per altre informazioni, vedere [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2.  Nel *DynamicWindowPanePackage.cs* file, individuare la dichiarazione DynamicWindowPanePackage. Aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> e <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute> attributi per registrare la finestra degli strumenti.  
  
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
  
     Gli attributi indicati registrare la finestra degli strumenti denominata DynamicWindowPane come finestra temporanea che non viene mantenuta quando viene chiuso e riaperto Visual Studio. Viene aperto DynamicWindowPane ogni volta che <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> applica e chiusi in caso contrario.  
  
3.  Compilare il progetto e avviare il debug. L'istanza sperimentale dovrebbe essere visualizzato. È non verrà visualizzata la finestra degli strumenti.  
  
4.  Aprire un progetto nell'istanza sperimentale. Apparirà la finestra degli strumenti.