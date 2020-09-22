---
title: Apertura di una finestra degli strumenti dinamica | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- tool windows, dynamic
ms.assetid: 21547ba7-6e81-44df-9277-265bf34f877a
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 09b81294abc708cf7616dad03b5dd7333d6a1719
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839896"
---
# <a name="opening-a-dynamic-tool-window"></a>Apertura di una finestra degli strumenti dinamica
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Le finestre degli strumenti vengono in genere aperte da un comando in un menu o da un tasto di scelta rapida equivalente. In alcuni casi, tuttavia, potrebbe essere necessaria una finestra degli strumenti che si apre ogni volta che viene applicato un contesto dell'interfaccia utente specifico e si chiude quando il contesto dell'interfaccia utente non viene più applicato. Le finestre degli strumenti come queste sono denominate *dinamiche* o *visibili automaticamente*.  
  
> [!NOTE]
> Per un elenco dei contesti dell'interfaccia utente predefiniti, vedere <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT> . In  
  
 Se si desidera aprire una finestra degli strumenti dinamica all'avvio ed è possibile che la creazione abbia esito negativo, è necessario implementare l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx> interfaccia e testare le condizioni di errore nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackageDynamicToolOwnerEx.QueryShowTool%2A> metodo. Affinché la shell sappia di disporre di una finestra degli strumenti dinamica da aprire all'avvio, è necessario aggiungere il `SupportsDynamicToolOwner` valore (impostato su 1) alla registrazione del pacchetto. Questo valore non fa parte dello standard <xref:Microsoft.VisualStudio.Shell.PackageRegistrationAttribute> , pertanto è necessario creare un attributo personalizzato per aggiungerlo. Per ulteriori informazioni sugli attributi personalizzati, vedere [utilizzo di un attributo di registrazione personalizzato per registrare un'estensione](../misc/using-a-custom-registration-attribute-to-register-an-extension.md).  
  
 Utilizzare <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> per aprire una finestra degli strumenti. La finestra degli strumenti viene creata in base alle esigenze.  
  
> [!NOTE]
> Una finestra degli strumenti dinamica può essere chiusa dall'utente. Se si desidera creare un comando di menu che consente all'utente di riaprire la finestra degli strumenti, il comando di menu deve essere abilitato nello stesso contesto dell'interfaccia utente che apre la finestra degli strumenti e disabilitato in caso contrario.  
  
### <a name="to-open-a-dynamic-tool-window"></a>Per aprire una finestra degli strumenti dinamica  
  
1. Creare un progetto VSIX denominato **DynamicToolWindow** e aggiungere un modello di elemento della finestra degli strumenti denominato **DynamicWindowPane.cs**. Per ulteriori informazioni, vedere [creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).  
  
2. Nel file DynamicWindowPanePackage.cs trovare la dichiarazione DynamicWindowPanePackage. Aggiungere gli <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> attributi e T:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute per registrare la finestra degli strumenti.  
  
    ```vb  
    [[ProvideToolWindow(typeof(DynamicWindowPane)]  
    [ProvideToolWindowVisibility(typeof(DynamicWindowPane), VSConstants.UICONTEXT.SolutionExists_string)]  
    [PackageRegistration(UseManagedResourcesOnly = true)]  
    [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About  
    [ProvideMenuResource("Menus.ctmenu", 1)]  
    [ProvideToolWindow(typeof(DynamicToolWindow.DynamicWindowPane))]  
    [Guid(DynamicWindowPanePackageGuids.PackageGuidString)]  
    public sealed class DynamicWindowPanePackage : Package  
    {. . .}  
    ```  
  
     Questa operazione registra la finestra degli strumenti denominata DynamicWindowPane come finestra temporanea che non viene resa persistente quando Visual Studio viene chiuso e riaperto. DynamicWindowPane viene aperto ogni volta che viene <xref:Microsoft.VisualStudio.VSConstants.UICONTEXT.SolutionExists_string> applicato e chiuso in caso contrario.  
  
3. Compilare il progetto e avviare il debug. Verrà visualizzata l'istanza sperimentale. La finestra degli strumenti non dovrebbe essere visualizzata.  
  
4. Aprire un progetto nell'istanza sperimentale. Verrà visualizzata la finestra degli strumenti.
