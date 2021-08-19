---
title: Creazione di una finestra degli strumenti a istanze | Microsoft Docs
description: Informazioni su come modificare una finestra degli strumenti in modo che più istanze della finestra possano essere aperte contemporaneamente. Per impostazione predefinita, nelle finestre degli strumenti può essere aperta una sola istanza.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- multi
- tool windows
ms.assetid: 4a7872f1-acc9-4f43-8932-5a526b36adea
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 61b9f21163fd9382575aa97693e955a5cf710b6e
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122089732"
---
# <a name="create-a-multi-instance-tool-window"></a>Creare una finestra degli strumenti a istanze multipla
È possibile programmare una finestra degli strumenti in modo che più istanze di essa possano essere aperte contemporaneamente. Per impostazione predefinita, nelle finestre degli strumenti può essere aperta una sola istanza.

Quando si usa una finestra degli strumenti a istanze multipla, è possibile visualizzare contemporaneamente diverse origini di informazioni correlate. Ad esempio, è possibile inserire un controllo su più righe in una finestra degli strumenti a istanze diverse in modo che diversi frammenti di codice siano disponibili contemporaneamente durante <xref:System.Windows.Forms.TextBox> una sessione di programmazione. È anche possibile, ad esempio, inserire un controllo e una casella di riepilogo a discesa in una finestra degli strumenti a istanze diverse in modo che sia possibile tenere traccia di diverse origini dati in tempo <xref:System.Windows.Forms.DataGrid> reale contemporaneamente.

## <a name="create-a-basic-single-instance-tool-window"></a>Creare una finestra degli strumenti di base (a istanza singola)

1. Creare un progetto denominato **MultiInstanceToolWindow** usando il modello VSIX e aggiungere un modello di elemento della finestra degli strumenti personalizzato **denominato MIToolWindow.**

    > [!NOTE]
    > Per altre informazioni sulla creazione di un'estensione con una finestra degli strumenti, vedere [Creare un'estensione con una finestra degli strumenti.](../extensibility/creating-an-extension-with-a-tool-window.md)

## <a name="make-a-tool-window-multi-instance"></a>Creare più istanze di una finestra degli strumenti

1. Aprire il file *MIToolWindowPackage.cs* e trovare `ProvideToolWindow` l'attributo . e il `MultiInstances=true` parametro , come illustrato nell'esempio seguente:

    ```csharp
    [PackageRegistration(UseManagedResourcesOnly = true)]
        [InstalledProductRegistration("#110", "#112", "1.0", IconResourceID = 400)] // Info on this package for Help/About
        [ProvideMenuResource("Menus.ctmenu", 1)]
        [ProvideToolWindow(typeof(MultiInstanceToolWindow.MIToolWindow), MultiInstances = true)]
        [Guid(MIToolWindowPackage.PackageGuidString)]
        public sealed class MIToolWindowPackage : Package
    {. . .}
    ```

2. Nel file *MIToolWindowCommand.cs* trovare il `ShowToolWindos()` metodo . In questo metodo chiamare il metodo e impostarne il flag su in modo che eseererà l'iterazione tra le istanze della finestra degli strumenti esistenti fino a quando non viene trovato <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> `create` un oggetto `false` `id` disponibile.

3. Per creare un'istanza della finestra degli strumenti, chiamare <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> il metodo e impostarne su un valore `id` disponibile e il relativo flag su `create` `true` .

    Per impostazione predefinita, il valore `id` del parametro del metodo è <xref:Microsoft.VisualStudio.Shell.Package.FindToolWindow%2A> `0` . Questo valore crea una finestra degli strumenti a istanza singola. Per ospitare più di un'istanza, ogni istanza deve avere un proprio `id` univoco.

4. Chiamare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.Show%2A> metodo <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame> sull'oggetto restituito dalla proprietà <xref:Microsoft.VisualStudio.Shell.ToolWindowPane.Frame%2A> dell'istanza della finestra degli strumenti.

5. Per impostazione predefinita, il metodo creato dal modello di elemento della finestra `ShowToolWindow` degli strumenti crea una finestra degli strumenti a istanza singola. Nell'esempio seguente viene illustrato come modificare `ShowToolWindow` il metodo per creare più istanze di .

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
