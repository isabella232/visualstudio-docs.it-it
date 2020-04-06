---
title: Implementazione di Command . Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c7a536120c81c154cf894717a2af6a4e048d56e2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709585"
---
# <a name="command-implementation"></a>Implementazione dei comandi
Per implementare un comando in un pacchetto VSPackage, è necessario eseguire le attività seguenti:To implement a command in a VSPackage, you must perform the following tasks:

1. Nel file *vsct* impostare un gruppo di comandi e quindi aggiungervi il comando. Per ulteriori informazioni, vedere File della tabella dei comandi di [Visual Studio (con estensione vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

2. Registrare il comando con Visual Studio.Register the command with Visual Studio.

3. Implementare il comando.

Nelle sezioni seguenti viene illustrato come registrare e implementare i comandi.

## <a name="register-commands-with-visual-studio"></a>Registrare i comandi con Visual StudioRegister commands with Visual Studio
 Se il comando deve essere visualizzato in <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> un menu, è necessario aggiungere il al pacchetto VSPackage e usare come valore il nome del menu o il relativo ID di risorsa.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Inoltre, è necessario registrare <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService>il comando con il file . È possibile ottenere questo <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> servizio utilizzando il metodo <xref:Microsoft.VisualStudio.Shell.Package>se il pacchetto VSPackage è derivato da .

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

## <a name="implement-commands"></a>Implementare i comandi
 Esistono diversi modi per implementare i comandi. Se si desidera un comando di menu statico, ovvero un comando che viene sempre <xref:System.ComponentModel.Design.MenuCommand> visualizzato nello stesso modo e nello stesso menu, creare il comando utilizzando come illustrato negli esempi della sezione precedente. Per creare un comando statico, è necessario fornire un gestore eventi responsabile dell'esecuzione del comando. Poiché il comando è sempre abilitato e visibile, non è necessario fornire il relativo stato a Visual Studio.Because the command is always enabled and visible, you do not have to provide its status to Visual Studio. Se si desidera modificare lo stato di un comando in base a determinate <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> condizioni, è possibile creare il comando come `QueryStatus` istanza della classe e, nel costruttore, fornire un gestore eventi per eseguire il comando e un gestore per notificare a Visual Studio quando lo stato del comando viene modificato. È inoltre <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> possibile implementare come parte di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> una classe di comando o, è possibile implementare se si fornisce un comando come parte di un progetto. Le due interfacce <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> e la classe dispongono tutte di metodi che notificano a Visual Studio una modifica dello stato di un comando e di altri metodi che forniscono l'esecuzione del comando.

 Quando un comando viene aggiunto al servizio di comando, diventa uno di una catena di comandi. Quando si implementano i metodi di notifica dello stato e di esecuzione per il comando, prestare attenzione a fornire solo per quel particolare comando e passare tutti gli altri casi agli altri comandi nella catena. Se non si riesce a passare <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>il comando (in genere restituendo ), Visual Studio potrebbe smettere di funzionare correttamente.

## <a name="querystatus-methods"></a>Metodi QueryStatus
 Se si implementa <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> o il metodo, verificare il GUID del set di comandi a cui appartiene il comando e l'ID del comando. Attenersi alle seguenti indicazioni:

- Se il GUID non viene riconosciuto, <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP>l'implementazione di uno dei due metodi deve restituire .

- Se l'implementazione di uno dei due metodi riconosce il GUID <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>ma non ha implementato il comando, il metodo deve restituire .

- Se l'implementazione di uno dei due metodi riconosce sia il GUID che il comando, `prgCmds` il metodo deve <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> impostare il campo command-flags di ogni comando (nel parametro) utilizzando i seguenti flag:

  - `OLECMDF_SUPPORTED`: il comando è supportato.

  - `OLECMDF_INVISIBLE`: il comando non deve essere visibile.

  - `OLECMDF_LATCHED`: il comando è attivato e sembra essere stato selezionato.

  - `OLECMDF_ENABLED`: il comando è abilitato.

  - `OLECMDF_DEFHIDEONCTXTMENU`: il comando deve essere nascosto se viene visualizzato in un menu di scelta rapida.

  - `OLECMDF_NINCHED`: il comando è un controller di menu e non è abilitato, ma l'elenco a discesa non è vuoto ed è ancora disponibile. (Questo flag viene utilizzato raramente.)

- Se il comando è stato definito nel `TextChanges` file *vsct* con il flag, impostare i seguenti parametri:

  - Impostare `rgwz` l'elemento del `pCmdText` parametro sul nuovo testo del comando.

  - Impostare `cwActual` l'elemento del `pCmdText` parametro sulla dimensione della stringa di comando.

Assicurarsi inoltre che il contesto corrente non sia una funzione di automazione, a meno che il comando non sia specificamente destinato a gestire le funzioni di automazione.

Per indicare che si supporta <xref:Microsoft.VisualStudio.VSConstants.S_OK>un comando specifico, restituire . Per tutti gli <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>altri comandi, restituire .

Nell'esempio seguente, `QueryStatus` il metodo verifica innanzitutto che il contesto non sia una funzione di automazione, quindi trova il GUID del set di comandi e l'ID di comando corretti. Il comando stesso è impostato per essere abilitato e supportato. Non sono supportati altri comandi.

```csharp
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
 L'implementazione del `Exec` metodo `QueryStatus` è simile all'implementazione del metodo. In primo luogo, assicurarsi che il contesto non è una funzione di automazione. Quindi, verificare sia il GUID che l'ID di comando. Se il GUID o l'ID <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED>di comando non viene riconosciuto, restituire .

 Per gestire il comando, <xref:Microsoft.VisualStudio.VSConstants.S_OK> eseguirlo e restituire se l'esecuzione ha esito positivo. Il comando è responsabile del rilevamento e della notifica degli errori; pertanto, restituire un codice di errore se l'esecuzione non riesce. Nell'esempio seguente viene illustrato come il metodo di esecuzione deve essere implementato.

```csharp
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

- [Come VSPackage aggiungere elementi dell'interfaccia utenteHow VSPackages add user interface elements](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
