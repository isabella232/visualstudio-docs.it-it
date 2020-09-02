---
title: Creazione di una finestra degli strumenti a istanze diverse | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1bb84ed9961cac5159e15bc0c45fada5426d2f2c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85904067"
---
# <a name="create-a-multi-instance-tool-window"></a>Creazione di una finestra degli strumenti a più istanze
È possibile programmare una finestra degli strumenti in modo che più istanze possano essere aperte contemporaneamente. Per impostazione predefinita, le finestre degli strumenti possono avere una sola istanza aperta.

Quando si utilizza una finestra degli strumenti a più istanze, è possibile visualizzare contemporaneamente diverse origini correlate di informazioni. Ad esempio, è possibile inserire un <xref:System.Windows.Forms.TextBox> controllo a più righe in una finestra degli strumenti a più istanze in modo che diversi frammenti di codice siano disponibili simultaneamente durante una sessione di programmazione. È possibile, ad esempio, inserire un <xref:System.Windows.Forms.DataGrid> controllo e una casella di riepilogo a discesa in una finestra degli strumenti a più istanze, in modo che sia possibile tenere traccia simultaneamente di diverse origini dati in tempo reale.

## <a name="create-a-basic-single-instance-tool-window"></a>Creare una finestra degli strumenti di base (a istanza singola)

1. Creare un progetto denominato **MultiInstanceToolWindow** usando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato denominato **MIToolWindow**.

    > [!NOTE]
    > Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [creare un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md).

## <a name="make-a-tool-window-multi-instance"></a>Creare una finestra degli strumenti a istanze diverse

1. Aprire il file *MIToolWindowPackage.cs* e trovare l' `ProvideToolWindow` attributo. e il `MultiInstances=true` parametro, come illustrato nell'esempio seguente:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. Nel file *MIToolWindowCommand.cs* trovare il `ShowToolWindos()` metodo. In questo metodo chiamare il <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodo e impostare il relativo `create` flag su in `false` modo da scorrere le istanze della finestra degli strumenti esistenti fino a quando non viene trovato un oggetto disponibile `id` .

3. Per creare un'istanza della finestra degli strumenti, chiamare il <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodo e impostare la proprietà `id` su un valore disponibile e il relativo `create` flag su `true` .

    Per impostazione predefinita, il valore del `id` parametro del <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> metodo è `0` . Questo valore rende una finestra degli strumenti a istanza singola. Per ospitare più istanze, ogni istanza deve disporre di un proprio oggetto univoco `id` .

4. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodo sull' <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> oggetto restituito dalla <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> proprietà dell'istanza della finestra degli strumenti.

5. Per impostazione predefinita, il `ShowToolWindow` metodo creato dal modello di elemento della finestra degli strumenti crea una finestra degli strumenti a istanza singola. Nell'esempio seguente viene illustrato come modificare il `ShowToolWindow` metodo per creare più istanze.

    ```csharp
    private void ShowToolWindow(object sender, EventArgs e)
    {
        for (int i = 0; i < 10; i++)
        {
            ToolWindowPane window = this.package.FindToolWindow(typeof(MIToolWindow), i, false);
            if (window == null)
            {
                // Create the window with the first free ID.
                window = (ToolWindowPane)this.package.FindToolWindow(typeof(MIToolWindow), i, true);
                if ((null == window) || (null == window.Frame))
                {
                    throw new NotSupportedException("Cannot create tool window");
                }

            IVsWindowFrame windowFrame = (IVsWindowFrame)window.Frame;
            Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure(windowFrame.Show());
            break;
            }
        }
    }
    ```
