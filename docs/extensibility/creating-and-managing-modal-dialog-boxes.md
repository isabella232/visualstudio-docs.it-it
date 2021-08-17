---
title: Creazione e gestione di finestre di dialogo modali | Microsoft Docs
description: Informazioni su come creare una finestra di dialogo modale all'interno Visual Studio, sia usando DialogWindow che senza usare DialogWindow.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- dialog boxes, managing in Visual Studio
ms.assetid: 491bc0de-7dba-478c-a76b-923440e090f3
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 88c1f943fd7c8579673047acbc533ca4577992bc7e13258276496a2499129e5c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121293456"
---
# <a name="create-and-manage-modal-dialog-boxes"></a>Creare e gestire finestre di dialogo modali
Quando si crea una finestra di dialogo modale all'interno di Visual Studio, è necessario assicurarsi che la finestra padre della finestra di dialogo sia disabilitata mentre viene visualizzata la finestra di dialogo, quindi ri abilitare nuovamente la finestra padre dopo la chiusura della finestra di dialogo. In caso contrario, è possibile che venga visualizzato l'errore Microsoft Visual Studio arrestarsi perché è attiva una finestra *di dialogo modale. Chiudere il dialogo attivo e riprovare.*

Esistono due modi per eseguire questa operazione. Se si dispone di una finestra di dialogo WPF, è consigliabile derivarla da e quindi chiamare per <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> visualizzare la finestra di <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow.ShowModal%2A> dialogo. In questo caso, non è necessario gestire lo stato modale della finestra padre.

Se la finestra di dialogo non è WPF o per qualche altro motivo non è possibile derivare la classe della finestra di dialogo da , è necessario ottenere l'elemento padre della finestra di dialogo chiamando e gestire manualmente lo stato modale, chiamando il metodo con un parametro 0 (false) prima di visualizzare la finestra di dialogo e chiamando di nuovo il metodo con un parametro <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.GetDialogOwnerHwnd%2A> di 1 (true) dopo aver chiuso la finestra di <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.EnableModeless%2A> dialogo.

## <a name="create-a-dialog-box-derived-from-dialogwindow"></a>Creare una finestra di dialogo derivata da DialogWindow

1. Creare un progetto VSIX denominato **OpenDialogTest** e aggiungere un comando di menu denominato **OpenDialog.** Per altre informazioni su come eseguire questa operazione, vedere [Creare un'estensione con un comando di menu.](../extensibility/creating-an-extension-with-a-menu-command.md)

2. Per usare la classe , è necessario aggiungere riferimenti agli assembly seguenti (nella scheda <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> Framework della finestra di **dialogo** Aggiungi riferimento):

    - *PresentationCore*

    - *PresentationFramework*

    - *WindowsBase*

    - *System.Xaml*

3. In *OpenDialog.cs* aggiungere l'istruzione `using` seguente:

    ```csharp
    using Microsoft.VisualStudio.PlatformUI;
    ```

4. Dichiarare una classe denominata `TestDialogWindow` che deriva da <xref:Microsoft.VisualStudio.PlatformUI.DialogWindow> :

    ```csharp
    class TestDialogWindow : DialogWindow
    {. . .}
    ```

5. Per poter ridurre a icona e ingrandire la finestra di dialogo, <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMaximizeButton%2A> impostare e <xref:Microsoft.VisualStudio.PlatformUI.DialogWindowBase.HasMinimizeButton%2A> su true:

    ```csharp
    internal TestDialogWindow()
    {
        this.HasMaximizeButton = true;
        this.HasMinimizeButton = true;
    }
    ```

6. Nel metodo `OpenDialog.ShowMessageBox` sostituire il codice esistente con il codice seguente:

    ```csharp
    TestDialogWindow testDialog = new TestDialogWindow();
    testDialog.ShowModal();
    ```

7. Compilare ed eseguire l'applicazione. Verrà visualizzata l'istanza Visual Studio sperimentale. Nel menu **Strumenti** dell'istanza sperimentale dovrebbe essere visualizzato un comando denominato **Invoke OpenDialog**. Quando si fa clic su questo comando, viene visualizzata la finestra di dialogo. Dovrebbe essere possibile ridurre a icona e ingrandire la finestra.

## <a name="create-and-manage-a-dialog-box-not-derived-from-dialogwindow"></a>Creare e gestire una finestra di dialogo non derivata da DialogWindow

1. Per questa procedura, è possibile usare la **soluzione OpenDialogTest** creata nella procedura precedente, con gli stessi riferimenti all'assembly.

2. Aggiungere le `using` dichiarazioni seguenti:

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

5. Aggiungere un costruttore che imposta il riferimento su <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell> :

    ```csharp
    public TestDialogWindow2(IVsUIShell uiShell)
    {
        shell = uiShell;
    }
    ```

6. Nel metodo `OpenDialog.ShowMessageBox` sostituire il codice esistente con il codice seguente:

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

7. Compilare ed eseguire l'applicazione. Nel menu **Strumenti** dovrebbe essere visualizzato un comando denominato **Invoke OpenDialog**. Quando si fa clic su questo comando, viene visualizzata la finestra di dialogo.
