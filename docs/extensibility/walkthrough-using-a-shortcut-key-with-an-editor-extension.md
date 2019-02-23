---
title: "Procedura dettagliata: Uso di un tasto di scelta rapida con un'estensione dell'Editor | Microsoft Docs"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0d2abc185d06aa74e47bb2a36bd17df12a9db5c8
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/22/2019
ms.locfileid: "56710305"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Procedura dettagliata: Usare i tasti di scelta rapida con un'estensione dell'editor
È possibile rispondere a tasti di scelta rapida nell'estensione di editor. Procedura dettagliata illustra come aggiungere un'area di controllo di visualizzazione per una visualizzazione di testo tramite un tasto di scelta rapida. Questa procedura dettagliata è basata sul modello di riquadro di visualizzazione dell'area di controllo editor e consente di aggiungere l'area di controllo usando il carattere +.

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, Visual Studio SDK è non installare dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [installare Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un progetto di Managed Extensibility Framework (MEF)

1. Creare un progetto c# VSIX. (Nelle **nuovo progetto** finestra di dialogo, seleziona **Visual c# / Extensibility**, quindi **progetto VSIX**.) Assegnare alla soluzione il nome `KeyBindingTest`.

2. Aggiungere un modello di elemento dell'area di controllo Text Editor per il progetto e denominarlo `KeyBindingTest`. Per altre informazioni, vedere [creare un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).

3. Aggiungere i seguenti riferimenti e impostare **CopyLocal** a `false`:

    Microsoft.VisualStudio.Editor

    Microsoft.VisualStudio.OLE.Interop

    Microsoft.VisualStudio.Shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   Nel file di classe KeyBindingTest, modificare il nome della classe a PurpleCornerBox. Usare la lampadina in cui viene visualizzata nel margine sinistro per apportare altre modifiche appropriate. All'interno del costruttore, modificare il nome del livello di area di controllo da **KeyBindingTest** al **PurpleCornerBox**:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

Nel file di classe KeyBindingTestTextViewCreationListener.cs, modificare il nome del AdornmentLayer dal **KeyBindingTest** al **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Comando TYPECHAR handle
Prima di Visual Studio 2017 versione 15.6, l'unico modo per gestire i comandi in un'estensione dell'editor è stata l'implementazione un <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> basato su filtro di comando. Visual Studio 2017 versione 15.6 è stato introdotto un approccio semplificato moderne basato sui gestori di comando dell'editor. Due sezioni successive illustrano come gestire un comando usando sia l'approccio legacy e moderna.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definisci il filtro di comando (precedente a Visual Studio 2017 versione 15.6)

 Il filtro di comando è un'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>, che gestisce il comando creando un'area di controllo.

1.  Aggiungere un file di classe e assegnargli il nome `KeyBindingCommandFilter`.

2.  Aggiungere le istruzioni using seguenti.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3.  La classe denominata KeyBindingCommandFilter deve ereditare da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4.  Aggiungere campi privati per la visualizzazione di testo, il comando successivo nella catena di comando e un flag che rappresentano se è già stato aggiunto il filtro di comando.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5.  Aggiungere un costruttore che imposta la visualizzazione di testo.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6.  Implementare il `QueryStatus()` metodo come indicato di seguito.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7.  Implementare il `Exec()` metodo in modo che si aggiunge una casella di colore viola alla visualizzazione se un segno più (**+**) carattere viene digitato.

    ```csharp
    int IOleCommandTarget.Exec(ref Guid pguidCmdGroup, uint nCmdID, uint nCmdexecopt, IntPtr pvaIn, IntPtr pvaOut)
    {
        if (m_adorned == false)
        {
            char typedChar = char.MinValue;

            if (pguidCmdGroup == VSConstants.VSStd2K && nCmdID == (uint)VSConstants.VSStd2KCmdID.TYPECHAR)
            {
                typedChar = (char)(ushort)Marshal.GetObjectForNativeVariant(pvaIn);
                if (typedChar.Equals('+'))
                {
                    new PurpleCornerBox(m_textView);
                    m_adorned = true;
                }
            }
        }
        return m_nextTarget.Exec(ref pguidCmdGroup, nCmdID, nCmdexecopt, pvaIn, pvaOut);
    }

    ```

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Aggiungere il filtro di comando (precedente a Visual Studio 2017 versione 15.6)
 Il provider dell'area di controllo è necessario aggiungere un filtro di comando per la visualizzazione di testo. In questo esempio, il provider implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> per ascoltare gli eventi di creazione di visualizzazione di testo. Questo provider dell'area di controllo consente di esportare anche il livello di area di controllo, che definisce l'ordine Z dell'area di controllo.

1.  Nel file KeyBindingTestTextViewCreationListener, aggiungere quanto segue usando istruzioni:

    ```csharp
    using System;
    using System.Collections.Generic;
    using System.ComponentModel.Composition;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio.Utilities;
    using Microsoft.VisualStudio.Editor;
    using Microsoft.VisualStudio.Text.Editor;
    using Microsoft.VisualStudio.TextManager.Interop;

    ```

2.  Per ottenere l'adattatore di visualizzazione di testo, è necessario importare il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>.

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3.  Modifica il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo che si aggiunge il `KeyBindingCommandFilter`.

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4.  Il `AddCommandFilter` gestore ottiene l'adattatore di visualizzazione di testo e aggiunge il filtro di comando.

    ```csharp
    void AddCommandFilter(IWpfTextView textView, KeyBindingCommandFilter commandFilter)
    {
        if (commandFilter.m_added == false)
        {
            //get the view adapter from the editor factory
            IOleCommandTarget next;
            IVsTextView view = editorFactory.GetViewAdapter(textView);

            int hr = view.AddCommandFilter(commandFilter, out next);

            if (hr == VSConstants.S_OK)
            {
                commandFilter.m_added = true;
                 //you'll need the next target for Exec and QueryStatus
                if (next != null)
                commandFilter.m_nextTarget = next;
            }
        }
    }
    ```

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementare un gestore di comando (a partire da Visual Studio 2017 versione 15.6)

In primo luogo, aggiornare i riferimenti Nuget del progetto per fare riferimento l'editor più recente API:

1. Pulsante destro del mouse sul progetto e scegliere **Gestisci pacchetti Nuget**.

2. Nella **Gestione pacchetti Nuget**, selezionare la **aggiornamenti** scheda, seleziona il **selezionare tutti i pacchetti** casella di controllo e quindi selezionare **Update**.

Il gestore del comando è un'implementazione di <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>, che gestisce il comando creando un'area di controllo.

1. Aggiungere un file di classe e assegnargli il nome `KeyBindingCommandHandler`.

2. Aggiungere le istruzioni using seguenti.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. La classe denominata KeyBindingCommandHandler deve ereditare `ICommandHandler<TypeCharCommandArgs>`ed esportarlo come <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Aggiungere un nome visualizzato del gestore comando:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Implementare il `GetCommandState()` metodo come indicato di seguito. Perché questo gestore comando gestisce comando TYPECHAR editor core, è possibile delegare l'abilitazione il comando per l'editor principale.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Implementare il `ExecuteCommand()` metodo in modo che si aggiunge una casella di colore viola alla visualizzazione se un segno più (**+**) carattere viene digitato.

   ```csharp
   public bool ExecuteCommand(TypeCharCommandArgs args, CommandExecutionContext executionContext)
   {
       if (args.TypedChar == '+')
       {
           bool alreadyAdorned = args.TextView.Properties.TryGetProperty(
               "KeyBindingTextAdorned", out bool adorned) && adorned;
           if (!alreadyAdorned)
           {
               new PurpleCornerBox((IWpfTextView)args.TextView);
               args.TextView.Properties.AddProperty("KeyBindingTextAdorned", true);
           }
       }

       return false;
   }
   ```
   7. Definizione del livello di area di controllo da copiare *KeyBindingTestTextViewCreationListener.cs* del file per il *KeyBindingCommandHandler.cs* e quindi eliminare  *KeyBindingTestTextViewCreationListener.cs* file:

   ```csharp
   /// <summary>
   /// Defines the adornment layer for the adornment. This layer is ordered
   /// after the selection layer in the Z-order.
   /// </summary>
   [Export(typeof(AdornmentLayerDefinition))]
   [Name("PurpleCornerBox")]
   [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
   private AdornmentLayerDefinition editorAdornmentLayer;
   ```

## <a name="make-the-adornment-appear-on-every-line"></a>Visualizzare l'area di controllo in tutte le righe

L'area di controllo originale era presente in tutti i caratteri 'a' in un file di testo. Ora che è stato modificato il codice per aggiungere l'area di controllo in risposta al **+** character, aggiunge l'area di controllo per la riga in cui il **+** carattere viene digitato. È possibile modificare il codice dell'area di controllo in modo che l'area di controllo ancora una volta visualizzata in ogni "a".

Nel *KeyBindingTest.cs* file, modificare il `CreateVisuals()` metodo per scorrere tutte le righe nella vista per decorare il carattere "a".

```csharp
private void CreateVisuals(ITextViewLine line)
{
    IWpfTextViewLineCollection textViewLines = this.view.TextViewLines;

    foreach (ITextViewLine textViewLine in textViewLines)
    {
        if (textViewLine.ToString().Contains("a"))
        {
            // Loop through each character, and place a box around any 'a'
            for (int charIndex = textViewLine.Start; charIndex < textViewLine.End; charIndex++)
            {
                if (this.view.TextSnapshot[charIndex] == 'a')
                {
                    SnapshotSpan span = new SnapshotSpan(this.view.TextSnapshot, Span.FromBounds(charIndex, charIndex + 1));
                    Geometry geometry = textViewLines.GetMarkerGeometry(span);
                    if (geometry != null)
                    {
                        var drawing = new GeometryDrawing(this.brush, this.pen, geometry);
                        drawing.Freeze();

                        var drawingImage = new DrawingImage(drawing);
                        drawingImage.Freeze();

                        var image = new Image
                        {
                            Source = drawingImage,
                        };

                        // Align the image with the top of the bounds of the text geometry
                        Canvas.SetLeft(image, geometry.Bounds.Left);
                        Canvas.SetTop(image, geometry.Bounds.Top);

                        this.layer.AddAdornment(AdornmentPositioningBehavior.TextRelative, span, null, image, null);
                    }
                }
            }
        }
    }
}
```

## <a name="build-and-test-the-code"></a>Compilare e testare il codice

1.  Compilare la soluzione KeyBindingTest ed eseguirlo nell'istanza sperimentale.

2.  Creare o aprire un file di testo. Digitare alcune parole contenenti il carattere 'a', quindi digitare **+** ovunque nella visualizzazione di testo.

     Un quadrato di colore viola dovrebbe essere visualizzato ogni carattere "a" nel file.
