---
title: Creazione e gestione delle finestre di dialogo modali Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 786a2fbe2b75c51420668eb1ab6f596213d3da9b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739489"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Creare e gestire finestre di dialogo modali
Quando si crea una finestra di dialogo modale all'interno di Visual Studio, è necessario assicurarsi che la finestra padre della finestra di dialogo sia disabilitata mentre viene visualizzata la finestra di dialogo, quindi riattivare la finestra padre dopo la chiusura della finestra di dialogo. In caso contrario, è che venga visualizzato l'errore: *Impossibile arrestare Microsoft Visual Studio perché è attiva una finestra di dialogo modale. Chiudere la finestra di dialogo attiva e riprovare.*

Ci sono due modi per farlo. Il modo consigliato, se si dispone di una <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>finestra di <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> dialogo WPFWPF, consiste nel derivarla da , quindi chiamare per visualizzare la finestra di dialogo. In questo caso, non è necessario gestire lo stato modale della finestra padre.

Se la finestra di dialogo non è WPFWPF o per <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>altri motivi non è possibile derivare <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> la classe della finestra di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> dialogo da , è necessario ottenere manualmente l'elemento padre della finestra di dialogo chiamando e gestire lo stato modale, chiamando il metodo con un parametro pari a 0 (false) prima di visualizzare la finestra di dialogo e chiamando nuovamente il metodo con un parametro 1 (true) dopo la chiusura della finestra di dialogo.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Creare una finestra di dialogo derivata da DialogWindowCreate a dialog box derived from DialogWindow

1. Creare un progetto VSIX denominato **OpenDialogTest** e aggiungere un comando di menu denominato **OpenDialog**. Per ulteriori informazioni su come eseguire questa operazione, vedere [Creare un'estensione con un comando](../extensibility/creating-an-extension-with-a-menu-command.md)di menu .

2. Per utilizzare <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> la classe, è necessario aggiungere riferimenti agli assembly seguenti (nella scheda Framework della finestra di dialogo **Aggiungi riferimento):**

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. In *OpenDialog.cs*aggiungere `using` l'istruzione seguente:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Dichiarare una `TestDialogWindow` classe denominata <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow>che deriva da :

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Per poter ridurre a icona e <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> ingrandire <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> la finestra di dialogo, impostare e su true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. Nel `OpenDialog.ShowMessageBox` metodo sostituire il codice esistente con quanto segue:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Compilare ed eseguire l'applicazione. Verrà visualizzata l'istanza sperimentale di Visual Studio.The experimental instance of Visual Studio should appear. Nel menu **Strumenti** dell'istanza sperimentale verrà visualizzato un comando denominato **Invoke OpenDialog**. Quando si fa clic su questo comando, verrà visualizzata la finestra di dialogo. Dovresti essere in grado di ridurre a icona e ingrandire la finestra.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Creare e gestire una finestra di dialogo non derivata da DialogWindowCreate and manage a dialog box not derived from DialogWindow

1. Per questa procedura, è possibile utilizzare la soluzione **OpenDialogTest** creata nella procedura precedente, con lo stesso riferimento all'assembly.

2. Aggiungere le `using` seguenti dichiarazioni:

    ```csharp
    using System.Windows;
    using Microsoft.Internal.VisualStudio.PlatformUI;
    ```

3. Creare una `TestDialogWindow2` classe denominata <xref:System.Windows.Window>che deriva da :

    ```csharp
    class TestDialogWindow2 : Window
    {. . .}
    ```

4. Aggiungi un riferimento <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>privato a :

    ```
    private IVsUIShell shell;
    ```

5. Aggiungere un costruttore che <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell>imposta il riferimento a :

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. Nel `OpenDialog.ShowMessageBox` metodo sostituire il codice esistente con quanto segue:

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

7. Compilare ed eseguire l'applicazione. Nel menu **Strumenti** verrà visualizzato un comando denominato **Richiama OpenDialog**. Quando si fa clic su questo comando, verrà visualizzata la finestra di dialogo.
