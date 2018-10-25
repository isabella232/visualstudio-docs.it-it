---
title: Implementazione di comando | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
caps.latest.revision: 25
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: ee10719fa8f0c5c45d9b45f3b1d686f454d808a4
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925912"
---
# <a name="command-implementation"></a>Implementazione dei comandi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Per implementare un comando in un pacchetto VSPackage, è necessario eseguire le attività seguenti:  
  
1. Nel file vsct, configurare un gruppo di comandi e quindi aggiungervi il comando. Per altre informazioni, vedere [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)'  
  
2. Registrare il comando con Visual Studio.  
  
3. Implementare il comando.  
  
   Le sezioni seguenti illustrano come registrare e implementare i comandi.  
  
## <a name="registering-commands-with-visual-studio"></a>La registrazione di comandi di Visual Studio  
 Se il comando deve comparire in un menu, è necessario aggiungere il <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> nel pacchetto VSPackage, e usarlo come valore il nome del menu di scelta o al relativo ID di risorsa.  
  
```  
[ProvideMenuResource("Menus.ctmenu", 1)]  
...  
    public sealed class MyPackage : Package  
    {.. ..}  
  
```  
  
 Inoltre, è necessario registrare il comando con il <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>. È possibile ottenere questo servizio utilizzando il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo se il pacchetto VSPackage è derivato da <xref:Microsoft.VisualStudio.Shell.Package>.  
  
```  
OleMenuCommandService mcs = GetService(typeof(IMenuCommandService)) as OleMenuCommandService;  
if ( null != mcs )  
{  
    // Create the command for the menu item.  
    CommandID menuCommandID = new CommandID(guidCommandGroup, myCommandID);  
    MenuCommand menuItem = new MenuCommand(MenuItemCallback, menuCommandID );  
    mcs.AddCommand( menuItem );  
}  
  
```  
  
## <a name="implementing-commands"></a>Implementazione di comandi  
 Esistono diversi modi per implementare i comandi. Se si desidera che un comando di menu statico, che è un comando che appare sempre lo stesso modo e nello stesso menu, creare il comando usando <xref:System.ComponentModel.Design.MenuCommand> come illustrato negli esempi nella sezione precedente. Per creare un comando statico, è necessario fornire un gestore eventi che è responsabile per l'esecuzione del comando. Poiché il comando è sempre abilitato e visibile, non è necessario fornire il relativo stato di Visual Studio. Se si desidera modificare lo stato di un comando in base a determinate condizioni, è possibile creare il comando come un'istanza di <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe e, nel relativo costruttore, fornire un gestore eventi per eseguire il comando e un gestore di stato di query per notificare all'oggetto visivo Studio quando viene modificato lo stato del comando. È anche possibile implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> come parte di una classe di comando o, è possibile implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> se si fornisce un comando come parte di un progetto. Le due interfacce e <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> tutte le classi dispongono di metodi che inviano una notifica di Visual Studio di una modifica nello stato di un comando e altri metodi che forniscono l'esecuzione del comando.  
  
 Quando si aggiunge un comando per il servizio dei comandi, diventa uno di una catena di comandi. Quando si implementano i metodi di notifica e l'esecuzione di stato per il comando, prestare attenzione per fornire solo per quel comando specifico e per passare tutti gli altri casi con gli altri comandi della catena. Se non si riesce a passare il comando (in genere restituendo <xref:Microsoft.VisualStudio.OLE.Interop.Constants>), Visual Studio potrebbero smettere di funzionare correttamente.  
  
## <a name="query-status-methods"></a>Metodi di query dello stato  
 Se si implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo o il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> (metodo), cercare il GUID del comando set a cui appartiene il comando e l'ID del comando. Attenersi alle seguenti indicazioni:  
  
- Se non viene riconosciuto il GUID, deve restituire l'implementazione di uno dei due metodi <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Se l'implementazione di uno dei due metodi riconosce il GUID, ma non ha implementato effettivamente il comando, quindi il metodo deve restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
- Se l'implementazione di uno dei due metodi riconosce il GUID e il comando, quindi il metodo deve impostare il campo flag dei comandi di ogni comando (nel `prgCmds` parametro) tramite i flag seguenti:  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Se il comando è supportato.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Se il comando non deve essere visibile.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Se il comando viene attivato e viene visualizzato per sono state controllate.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Se il comando è abilitato.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Se il comando deve essere nascosto quando viene visualizzato un menu di scelta rapida.  
  
  -   <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> Se il comando è un controller di menu e non è abilitato, ma l'elenco di menu a discesa non è vuoto e è ancora disponibile. (Questo flag viene raramente utilizzato).  
  
- Se il comando è stato definito nel file con estensione vsct con il `TextChanges` flag, impostare i parametri seguenti:  
  
  -   Impostare il `rgwz` elemento del `pCmdText` parametro per il nuovo testo del comando.  
  
  -   Impostare il `cwActual` elemento del `pCmdText` parametro per la dimensione della stringa di comando.  
  
  Inoltre assicurarsi che il contesto corrente non è una funzione di automazione, a meno che il comando è concepito appositamente per la gestione delle funzioni di automazione.  
  
  Per indicare che si supporta un particolare comando, restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK>. Per tutti gli altri comandi, restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
  Nell'esempio seguente, il metodo di query-status innanzitutto assicura che il contesto non è una funzione di automazione, quindi consente di trovare il GUID di set di comandi corretti e l'ID del comando. Comando stesso è impostato per essere attivata e supportata. Nessun altro comando è supportato.  
  
```  
public int QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.VSStd2K && cCmds > 0)  
        {  
            // make the Right command visible   
            if ((uint)prgCmds[0].cmdID == (uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                prgCmds[0].cmdf = (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_ENABLED | (int)Microsoft.VisualStudio.OLE.Interop.Constants.MSOCMDF_SUPPORTED;  
                return VSConstants.S_OK;  
            }  
        }  
        return Constants.OLECMDERR_E_NOTSUPPORTED;  
    }  
}  
  
```  
  
## <a name="execution-methods"></a>Metodi di esecuzione  
 Implementazione del metodo query-status è simile a implementazione del metodo di esecuzione. In primo luogo, assicurarsi che il contesto non è una funzione di automazione. Verificare quindi del GUID e ID del comando. Se il GUID o l'ID di comando non è riconosciuto, restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants>.  
  
 Per gestire il comando, eseguirlo e restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> se l'esecuzione ha esito positivo. Il comando è responsabile del rilevamento degli errori e notifica; di conseguenza, restituiscono un codice di errore se l'esecuzione ha esito negativo. L'esempio seguente illustra come deve essere implementato il metodo di esecuzione.  
  
```  
public int Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)  
{  
    if (!VsShellUtilities.IsInAutomationFunction(m_provider.ServiceProvider))  
    {  
        if (pguidCmdGroup == VSConstants.GUID_VSStandardCommandSet97)  
        {  
             if (nCmdID ==(uint) uint)VSConstants.VSStd2KCmdID.RIGHT)  
            {  
                //execute the command  
                return VSConstants.S_OK;  
            }  
        }  
    }  
    return Constants.OLECMDERR_E_NOTSUPPORTED;  
}  
  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

