---
title: Implementazione dei comandi | Microsoft Docs
description: Informazioni sull'implementazione dei comandi in Visual Studio, su come configurare un gruppo di comandi in un VSPackage, aggiungere un comando, registrare il comando e implementarlo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- commands, implementation
ms.assetid: c782175c-cce4-4bd0-8374-4a897ceb1b3d
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2e9ba7dcaf1f9e2f0e98e7cbb773256d117fcb47edf49d9b8f9815c985156b38
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414662"
---
# <a name="command-implementation"></a>Implementazione del comando
Per implementare un comando in un VSPackage, è necessario eseguire le attività seguenti:

1. Nel file *con estensione vsct* configurare un gruppo di comandi e quindi aggiungerlo. Per altre informazioni, vedere Visual Studio file di tabella dei comandi [(con estensione vsct).](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)

2. Registrare il comando con Visual Studio.

3. Implementare il comando .

Le sezioni seguenti illustrano come registrare e implementare i comandi.

## <a name="register-commands-with-visual-studio"></a>Registrare i comandi con Visual Studio
 Se il comando deve essere visualizzato in un menu, è necessario aggiungere al pacchetto VSPackage e usare come valore il nome del menu o il relativo <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> ID risorsa.

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

## <a name="implement-commands"></a>Implementare i comandi
 Esistono diversi modi per implementare i comandi. Se si vuole un comando di menu statico, che è un comando che viene sempre visualizzato nello stesso modo e nello stesso menu, creare il comando usando come illustrato negli esempi nella <xref:System.ComponentModel.Design.MenuCommand> sezione precedente. Per creare un comando statico, è necessario fornire un gestore eventi responsabile dell'esecuzione del comando. Poiché il comando è sempre abilitato e visibile, non è necessario specificarne lo stato Visual Studio. Se si vuole modificare lo stato di un comando a seconda di determinate condizioni, è possibile creare il comando come istanza della classe e, nel costruttore, fornire un gestore eventi per eseguire il comando e un gestore per notificare Visual Studio quando lo stato del comando <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> `QueryStatus` cambia. È anche possibile implementare come parte di una classe di comando oppure, se si fornisce un comando come <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> parte di un progetto. Le due interfacce e la classe hanno tutti metodi che notificano Visual Studio una modifica dello stato di un comando e altri metodi che forniscono l'esecuzione <xref:Microsoft.VisualStudio.Shell.OleMenuCommand> del comando.

 Quando un comando viene aggiunto al servizio comandi, diventa una catena di comandi. Quando si implementano la notifica di stato e i metodi di esecuzione per il comando, è necessario fornire solo per il comando specifico e passare tutti gli altri casi agli altri comandi nella catena. Se non si riesce a passare il comando su (in genere restituisce ), Visual Studio <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> potrebbe smettere di funzionare correttamente.

## <a name="querystatus-methods"></a>Metodi di QueryStatus
 Se si implementa il metodo o , verificare il GUID del set di comandi a cui appartiene il comando e <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> l'ID del comando. Attenersi alle seguenti indicazioni:

- Se il GUID non viene riconosciuto, l'implementazione di uno dei due metodi deve restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_UNKNOWNGROUP> .

- Se l'implementazione di uno dei due metodi riconosce il GUID ma non ha implementato il comando, il metodo deve restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

- Se l'implementazione di uno dei due metodi riconosce sia il GUID che il comando, il metodo deve impostare il campo command-flags di ogni comando (nel parametro ) usando i `prgCmds` flag <xref:Microsoft.VisualStudio.OLE.Interop.OLECMDF> seguenti:

  - `OLECMDF_SUPPORTED`: il comando è supportato.

  - `OLECMDF_INVISIBLE`: il comando non deve essere visibile.

  - `OLECMDF_LATCHED`: il comando è attivato e sembra essere stato selezionato.

  - `OLECMDF_ENABLED`: il comando è abilitato.

  - `OLECMDF_DEFHIDEONCTXTMENU`: il comando deve essere nascosto se viene visualizzato in un menu di scelta rapida.

  - `OLECMDF_NINCHED`: il comando è un controller di menu e non è abilitato, ma l'elenco a discesa non è vuoto ed è ancora disponibile. Questo flag viene usato raramente.

- Se il comando è stato definito nel file *con estensione vsct* con `TextChanges` il flag , impostare i parametri seguenti:

  - Impostare `rgwz` l'elemento `pCmdText` del parametro sul nuovo testo del comando.

  - Impostare `cwActual` l'elemento `pCmdText` del parametro sulla dimensione della stringa di comando.

Assicurarsi inoltre che il contesto corrente non sia una funzione di automazione, a meno che il comando non sia specificamente progettato per gestire le funzioni di automazione.

Per indicare che si supporta un comando specifico, restituire <xref:Microsoft.VisualStudio.VSConstants.S_OK> . Per tutti gli altri comandi, restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

Nell'esempio seguente il metodo verifica innanzitutto che il contesto non sia una funzione di automazione, quindi trova il GUID del set di comandi e `QueryStatus` l'ID comando corretti. Il comando stesso è impostato per essere abilitato e supportato. Non sono supportati altri comandi.

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
 L'implementazione `Exec` del metodo è simile all'implementazione del metodo `QueryStatus` . Assicurarsi innanzitutto che il contesto non sia una funzione di automazione. Testare quindi sia il GUID che l'ID comando. Se il GUID o l'ID comando non viene riconosciuto, restituire <xref:Microsoft.VisualStudio.OLE.Interop.Constants.OLECMDERR_E_NOTSUPPORTED> .

 Per gestire il comando, eseguirlo e restituire se <xref:Microsoft.VisualStudio.VSConstants.S_OK> l'esecuzione ha esito positivo. Il comando è responsabile del rilevamento degli errori e della notifica. Pertanto, restituire un codice di errore se l'esecuzione ha esito negativo. L'esempio seguente illustra come deve essere implementato il metodo di esecuzione.

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

## <a name="see-also"></a>Vedi anche

- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
