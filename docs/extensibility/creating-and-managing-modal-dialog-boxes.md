---
title: Creazione e gestione di finestre di dialogo modali | Microsoft Docs
description: Informazioni su come creare una finestra di dialogo modale in Visual Studio, usando DialogWindow e senza usare DialogWindow.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c95f03ee71a827380539404a90cd79d50232e488
ms.sourcegitcommit: 5027eb5c95e1d2da6d08d208fd6883819ef52d05
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/20/2020
ms.locfileid: "94973620"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Creare e gestire finestre di dialogo modali
Quando si crea una finestra di dialogo modale in Visual Studio, è necessario assicurarsi che la finestra padre della finestra di dialogo sia disabilitata mentre viene visualizzata la finestra di dialogo, quindi abilitare nuovamente la finestra padre dopo la chiusura della finestra di dialogo. In caso contrario, è possibile che venga visualizzato l'errore: *Impossibile arrestare Microsoft Visual Studio perché è attiva una finestra di dialogo modale. Chiudere la finestra di dialogo attiva e riprovare.*

Esistono due modi per eseguire questa operazione. Il metodo consigliato, se si dispone di una finestra di dialogo WPF, consiste nel derivarlo da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> e quindi chiamare <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> per visualizzare la finestra di dialogo. In tal caso, non è necessario gestire lo stato modale della finestra padre.

Se la finestra di dialogo non è WPF o per qualche altro motivo non è possibile derivare la classe della finestra di dialogo da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> , è necessario ottenere l'elemento padre della finestra di dialogo chiamando <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> e gestire lo stato modale, chiamando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> metodo con un parametro 0 (false) prima di visualizzare la finestra di dialogo e richiamando il metodo con un parametro 1 (true) dopo aver chiuso la finestra di

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Creare una finestra di dialogo derivata da DialogWindow

1. Creare un progetto VSIX denominato **OpenDialogTest** e aggiungere un comando di menu denominato **OpenDialog**. Per altre informazioni su come eseguire questa operazione, vedere [creare un'estensione con un comando di menu](../extensibility/creating-an-extension-with-a-menu-command.md).

2. Per utilizzare la <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> classe, è necessario aggiungere riferimenti agli assembly seguenti (nella scheda Framework della finestra di dialogo **Aggiungi riferimento** ):

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. In *OpenDialog.cs* aggiungere l'istruzione seguente `using` :

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Dichiarare una classe denominata `TestDialogWindow` che deriva da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> :

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Per poter ridurre a icona e ingrandire la finestra di dialogo, impostare <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> e <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> su true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. Nel `OpenDialog.ShowMessageBox` Metodo sostituire il codice esistente con il codice seguente:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Compilare ed eseguire l'applicazione. Verrà visualizzata l'istanza sperimentale di Visual Studio. Nel menu **strumenti** dell'istanza sperimentale dovrebbe essere visualizzato un comando denominato **Invoke OpenDialog**. Quando si fa clic su questo comando, verrà visualizzata la finestra di dialogo. Dovrebbe essere possibile ridurre al minimo e ingrandire la finestra.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Creare e gestire una finestra di dialogo non derivata da DialogWindow

1. Per questa procedura, è possibile usare la soluzione **OpenDialogTest** creata nella procedura precedente, con gli stessi riferimenti ad assembly.

2. Aggiungere le seguenti `using` dichiarazioni:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Creare una classe denominata `TestDialogWindow2` che deriva da <xref:System.Windows.Window> :

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Aggiungere un riferimento privato a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :

    ```
    private IVsUIShell shell;
    ```

5. Aggiungere un costruttore che imposta il riferimento a <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. Nel `OpenDialog.ShowMessageBox` Metodo sostituire il codice esistente con il codice seguente:

    ```csharp
    IVsUIShell uiShell = (IVsUIShell)ServiceProvider.GetService(typeof(SVsUIShell));

    TestDialogWindow2 testDialog2 = new TestDialogWindow2(uiShell);
    //get the owner of this dialog
    IntPtr hwnd;
    uiShell.GetDialogOwnerHwnd(out hwnd);
    testDialog2.WindowStartupLocation = System.Windows.WindowStartupLocation.CenterOwner;
    uiShell.EnableModeless(0);
    try
    {
        WindowHelper.ShowModal(testDialog2, hwnd);
    }
    finally
    {
        // This will take place after the window is closed.
        uiShell.EnableModeless(1);
    }
    ```

7. Compilare ed eseguire l'applicazione. Nel menu **strumenti** dovrebbe essere visualizzato un comando denominato **Invoke OpenDialog**. Quando si fa clic su questo comando, verrà visualizzata la finestra di dialogo.
