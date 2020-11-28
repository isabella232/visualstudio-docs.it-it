---
title: Implementazione del comando | Microsoft Docs
description: Per informazioni sull'implementazione dei comandi in Visual Studio, su come impostare un gruppo di comandi in un pacchetto VSPackage, aggiungere un comando, registrare il comando e implementarlo.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: 76b1f564c883d1ce03748f560b595cfa44a28b37
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96304822"
---
# <a name="command-implementation"></a>Implementazione del comando
Per implementare un comando in un VSPackage, è necessario eseguire le attività seguenti:

1. Nel file con *estensione vsct* impostare un gruppo di comandi e quindi aggiungervi il comando. Per ulteriori informazioni, vedere [file della tabella dei comandi di Visual Studio (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).

2. Registrare il comando con Visual Studio.

3. Implementare il comando.

Le sezioni seguenti illustrano come registrare e implementare i comandi.

## <a name="register-commands-with-visual-studio"></a>Registrare i comandi con Visual Studio
 Se il comando deve essere visualizzato in un menu, è necessario aggiungere al <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> pacchetto VSPackage e usare come valore il nome del menu o il relativo ID risorsa.

```
[ProvideMenuResource("Menus.ctmenu", 1)]
...
    public sealed class MyPackage : Package
    {.. ..}

```

 Inoltre, è necessario registrare il comando con <xref:Microsoft.VisualStudio.Shell.OleMenuCommandService> . È possibile ottenere questo servizio usando il <xref:Microsoft.VisualStudio.Shell.Package.GetService%2A> metodo se il pacchetto VSPackage è derivato da <xref:Microsoft.VisualStudio.Shell.Package> .

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

## <a name="implement-commands"></a>Implementa comandi
 Sono disponibili diversi modi per implementare i comandi. Se si desidera un comando di menu statico, ovvero un comando che viene sempre visualizzato nello stesso modo e nello stesso menu, creare il comando utilizzando <xref:System.ComponentModel.Design.MenuCommand> come illustrato negli esempi della sezione precedente. Per creare un comando statico, è necessario fornire un gestore eventi responsabile dell'esecuzione del comando. Poiché il comando è sempre abilitato e visibile, non è necessario fornire lo stato a Visual Studio. Se si desidera modificare lo stato di un comando in base a determinate condizioni, è possibile creare il comando come istanza della <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe e, nel costruttore, fornire un gestore eventi per eseguire il comando e un `QueryStatus` gestore per notificare a Visual Studio quando lo stato del comando viene modificato. È anche possibile implementare <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> come parte di una classe di comando o, è possibile implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> se si fornisce un comando come parte di un progetto. Le due interfacce e la <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> classe hanno tutti metodi che notificano a Visual Studio una modifica dello stato di un comando e altri metodi che forniscono l'esecuzione del comando.

 Quando un comando viene aggiunto al servizio di comando, diventa una catena di comandi. Quando si implementano i metodi di notifica e esecuzione di stato per il comando, prestare attenzione a fornire solo per quel particolare comando e per passare tutti gli altri casi a tutti gli altri comandi della catena. Se non è possibile passare il comando (in genere restituendo <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> ), Visual Studio potrebbe smettere di funzionare correttamente.

## <a name="querystatus-methods"></a>Metodi QueryStatus
 Se si implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo o il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> metodo, verificare la presenza del GUID del set di comandi a cui appartiene il comando e l'ID del comando. Attenersi alle seguenti indicazioni:

- Se il GUID non è riconosciuto, l'implementazione di uno dei due metodi deve restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP> .

- Se l'implementazione di uno dei metodi riconosce il GUID ma non ha implementato il comando, il metodo deve restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

- Se l'implementazione di entrambi i metodi riconosce sia il GUID che il comando, il metodo deve impostare il campo dei flag di comando di ogni comando (nel `prgCmds` parametro) usando i flag seguenti <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> :

  - `OLECMDF_SUPPORTED`: Il comando è supportato.

  - `OLECMDF_INVISIBLE`: Il comando non deve essere visibile.

  - `OLECMDF_LATCHED`: Il comando è attivato e sembra essere stato selezionato.

  - `OLECMDF_ENABLED`: Il comando è abilitato.

  - `OLECMDF_DEFHIDEONCTXTMENU`: Il comando deve essere nascosto se viene visualizzato in un menu di scelta rapida.

  - `OLECMDF_NINCHED`: Il comando è un controller di menu e non è abilitato, ma l'elenco dei menu a discesa non è vuoto ed è ancora disponibile. Questo flag viene usato raramente.

- Se il comando è stato definito nel file con *estensione vsct* con il `TextChanges` flag, impostare i parametri seguenti:

  - Impostare l' `rgwz` elemento del `pCmdText` parametro sul nuovo testo del comando.

  - Impostare l' `cwActual` elemento del `pCmdText` parametro sulla dimensione della stringa di comando.

Verificare inoltre che il contesto corrente non sia una funzione di automazione, a meno che il comando non venga progettato in modo specifico per gestire le funzioni di automazione.

Per indicare che è supportato un particolare comando, restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Per tutti gli altri comandi, restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

Nell'esempio seguente, il `QueryStatus` metodo verifica prima di tutto che il contesto non sia una funzione di automazione, quindi trova il GUID del set di comandi e l'ID di comando corretti. Il comando stesso è impostato per essere abilitato e supportato. Non sono supportati altri comandi.

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
 L'implementazione del `Exec` metodo è simile all'implementazione del `QueryStatus` metodo. Assicurarsi prima di tutto che il contesto non sia una funzione di automazione. Quindi, testare sia il GUID che l'ID di comando. Se il GUID o l'ID di comando non è riconosciuto, restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

 Per gestire il comando, eseguirlo e restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> se l'esecuzione ha esito positivo. Il comando è responsabile del rilevamento e della notifica degli errori. Pertanto, restituire un codice di errore se l'esecuzione ha esito negativo. Nell'esempio seguente viene illustrato come implementare il metodo di esecuzione.

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

- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
