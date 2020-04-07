---
title: Creazione di una finestra degli strumenti a più istanze Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 33585f623f846e16200d430ad2c886fe0874b537
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739618"
---
# <a name="create-a-multi-instance-tool-window"></a>Creare una finestra degli strumenti a più istanzeCreate a multi-instance tool window
È possibile programmare una finestra degli strumenti in modo che più istanze di essa possano essere aperte contemporaneamente. Per impostazione predefinita, le finestre degli strumenti possono avere una sola istanza aperta.

Quando si utilizza una finestra degli strumenti a più istanze, è possibile visualizzare più origini di informazioni correlate contemporaneamente. Ad esempio, è possibile inserire <xref:System.Windows.Forms.TextBox> un controllo multilinea in una finestra degli strumenti a più istanze in modo che diversi frammenti di codice siano disponibili contemporaneamente durante una sessione di programmazione. Inoltre, ad esempio, è <xref:System.Windows.Forms.DataGrid> possibile inserire un controllo e una casella di riepilogo a discesa in una finestra degli strumenti a più istanze in modo che diverse origini dati in tempo reale possono essere registrate contemporaneamente.

## <a name="create-a-basic-single-instance-tool-window"></a>Creare una finestra degli strumenti di base (istanza singola)Create a basic (single-instance) tool window

1. Creare un progetto denominato **MultiInstanceToolWindow** utilizzando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato denominato **MIToolWindow**.

    > [!NOTE]
    > Per ulteriori informazioni sulla creazione di un'estensione con una finestra degli strumenti, consultate [Creare un'estensione con una finestra degli strumenti.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="make-a-tool-window-multi-instance"></a>Rendere multiistanza una finestra degli strumenti

1. Aprire *MIToolWindowPackage.cs* il file MIToolWindowPackage.cs `ProvideToolWindow` e trovare l'attributo. e `MultiInstances=true` il parametro, come illustrato nell'esempio seguente:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. Nel file *MIToolWindowCommand.cs* individuare `ShowToolWindos()` il metodo. In questo metodo, <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> chiamare il `create` metodo `false` e impostarne il flag su in `id` modo che scorrerà le istanze della finestra degli strumenti esistenti fino a quando non viene trovato un oggetto disponibile.

3. Per creare un'istanza della <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> finestra degli `id` strumenti, chiamare `create` il `true`metodo e impostarne un valore disponibile e il relativo flag su .

    Per impostazione predefinita, `id` il <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> valore `0`del parametro del metodo è . Questo valore crea una finestra degli strumenti a istanza singola. Affinché più di un'istanza sia ospitata, `id`ogni istanza deve avere un proprio oggetto .

4. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> il metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> sull'oggetto restituito <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> dalla proprietà dell'istanza della finestra degli strumenti.

5. Per impostazione `ShowToolWindow` predefinita, il metodo creato dal modello di elemento della finestra degli strumenti crea una finestra degli strumenti a istanza singola. Nell'esempio seguente viene `ShowToolWindow` illustrato come modificare il metodo per creare più istanze.

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
