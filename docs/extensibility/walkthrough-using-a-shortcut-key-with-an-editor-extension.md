---
title: "Procedura dettagliata: utilizzo di un tasto di scelta rapida con un'estensione dell'editor Documenti Microsoft"
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 651598c0dbe746a9a26a6d60ce72b02853f98d47
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697157"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Procedura dettagliata: Usare un tasto di scelta rapida con un'estensione dell'editorWalkthrough: Use a shortcut key with an editor extension
È possibile rispondere ai tasti di scelta rapida nell'estensione dell'editor. Nella procedura dettagliata seguente viene illustrato come aggiungere un'area di controllo di visualizzazione a una visualizzazione di testo utilizzando un tasto di scelta rapida. Questa procedura dettagliata è basata sul modello dell'editor dell'area di controllo della finestra e consente di aggiungere l'area di controllo utilizzando il carattere .

## <a name="prerequisites"></a>Prerequisiti
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio.It's included as an optional feature in Visual Studio setup. È anche possibile installare l'SDK di VISUAL SMI in un secondo momento. Per ulteriori informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un progetto Managed Extensibility Framework (MEF)

1. Creare un progetto VSIX di C. (Nella finestra di dialogo **Nuovo progetto,** selezionare **Visual Cè / Extensibility**, quindi **Progetto VSIX**. Denominare `KeyBindingTest`la soluzione .

2. Aggiungere un modello di elemento Editor Text `KeyBindingTest`Adornment al progetto e denominarlo . Per ulteriori informazioni, consultate [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Aggiungere i riferimenti seguenti e `false`impostare **CopyLocal** su :

    Microsoft.VisualStudio.Editor

    Microsoft.VisualStudio.OLE.Interop

    Microsoft.VisualStudio.Shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   In the KeyBindingTest class file, change the class name to PurpleCornerBox. Utilizzare la lampadina visualizzata nel margine sinistro per apportare le altre modifiche appropriate. All'interno del costruttore, modificare il nome del livello dell'area di controllo da **KeyBindingTest** a **PurpleCornerBox**:

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

Nel file di classe KeyBindingTestTextViewCreationListener.cs modificare il nome di AdornmentLayer da **KeyBindingTest** a **PurpleCornerBox**:

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Comando TYPECHAR di handle
Prima di Visual Studio 2017 versione 15.6 l'unico modo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> per gestire i comandi in un'estensione dell'editor era l'implementazione di un filtro di comando basato. In Visual Studio 2017 versione 15.6 è stato introdotto un approccio semplificato moderno basato sui gestori dei comandi dell'editor. Le due sezioni successive illustrano come gestire un comando usando sia l'approccio legacy che quello moderno.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definire il filtro dei comandi (precedente a Visual Studio 2017 versione 15.6)Define the command filter (prior to Visual Studio 2017 version 15.6)

 Il filtro di comando <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>è un'implementazione di , che gestisce il comando tramite un'istanza dell'area di controllo.

1. Aggiungere un file di classe e assegnargli il nome `KeyBindingCommandFilter`.

2. Aggiungere le direttive using seguenti.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. La classe denominata KeyBindingCommandFilter deve ereditare da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>.

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Aggiungere campi privati per la visualizzazione di testo, il comando successivo nella catena di comandi e un flag per indicare se il filtro comandi è già stato aggiunto.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Aggiungere un costruttore che imposta la visualizzazione di testo.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. Implementare `QueryStatus()` il metodo come indicato di seguito.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Implementare `Exec()` il metodo in modo che aggiunga una**+** casella viola alla visualizzazione se viene digitato un segno più ( ).

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Aggiungere il filtro di comando (prima di Visual Studio 2017 versione 15.6)Add the command filter (prior to Visual Studio 2017 version 15.6)
 Il provider di aree di controllo deve aggiungere un filtro di comando alla visualizzazione di testo. In questo esempio, <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> il provider implementa per l'ascolto di eventi di creazione della visualizzazione di testo. Questo provider di ornamenti consente inoltre di esportare il livello dell'area di controllo, che definisce l'ordine z dell'area di controllo.

1. Nel file KeyBindingTestTextViewCreationListener aggiungere le direttive using seguenti:In the KeyBindingTestTextViewCreationListener file, add the following using directives:

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

2. Per ottenere l'adattatore di <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService>visualizzazione di testo, è necessario importare il file .

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Modificare <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> il metodo in `KeyBindingCommandFilter`modo che aggiunga l'oggetto .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. Il `AddCommandFilter` gestore ottiene l'adattatore di visualizzazione di testo e aggiunge il filtro di comando.

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementare un gestore di comando (a partire da Visual Studio 2017 versione 15.6)Implement a command handler (starting in Visual Studio 2017 version 15.6)

In primo luogo, aggiornare i riferimenti Nuget del progetto per fare riferimento all'API dell'editor più recente:First, update the project's Nuget references to reference the latest editor API:

1. Fare clic con il pulsante destro del mouse sul progetto e selezionare **Gestisci pacchetti Nuget**.

2. In **Nuget Package Manager**selezionare la scheda **Aggiornamenti** , selezionare la casella di controllo Seleziona tutti **i pacchetti** e quindi selezionare **Aggiorna**.

Il gestore di <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601>comando è un'implementazione di , che gestisce il comando tramite un'istanza dell'area di controllo.

1. Aggiungere un file di classe e assegnargli il nome `KeyBindingCommandHandler`.

2. Aggiungere le direttive using seguenti.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. La classe denominata KeyBindingCommandHandler deve ereditare da `ICommandHandler<TypeCharCommandArgs>`ed esportarla come <xref:Microsoft.VisualStudio.Commanding.ICommandHandler>:

   ```csharp
   [Export(typeof(ICommandHandler))]
   [ContentType("text")]
   [Name("KeyBindingTest")]
   internal class KeyBindingCommandHandler : ICommandHandler<TypeCharCommandArgs>
   ```

4. Aggiungere un nome visualizzato del gestore comandi:

   ```csharp
   public string DisplayName => "KeyBindingTest";
   ```

5. Implementare `GetCommandState()` il metodo come indicato di seguito. Poiché questo gestore di comandi gestisce il comando TYPECHAR dell'editor principale, può delegare l'abilitazione del comando all'editor principale.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Implementare `ExecuteCommand()` il metodo in modo che aggiunga una**+** casella viola alla visualizzazione se viene digitato un segno più ( ).

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

   7. Copiare la definizione del livello dell'area di controllo dal file *KeyBindingTestTextViewCreationListener.cs* al *KeyBindingCommandHandler.cs,* quindi eliminare *KeyBindingTestTextViewCreationListener.cs* file:

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

## <a name="make-the-adornment-appear-on-every-line"></a>Fai apparire l'ornamento su ogni riga

L'ornamento originale è apparso su ogni carattere 'a' in un file di testo. Ora che è stato modificato il codice per **+** aggiungere l'area di controllo in risposta **+** al carattere, aggiunge l'area di controllo solo nella riga in cui viene digitato il carattere. Possiamo cambiare il codice dell'area di controllo in modo che l'area di controllo venga nuovamente visualizzata su ogni 'a'.

Nel file *KeyBindingTest.cs,* `CreateVisuals()` modificare il metodo per scorrere tutte le righe nella visualizzazione per decorare il carattere 'a'.

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

## <a name="build-and-test-the-code"></a>Compilare e testare il codiceBuild and test the code

1. Compilare la soluzione KeyBindingTest ed eseguirla nell'istanza sperimentale.

2. Creare o aprire un file di testo. Digitare alcune parole contenenti il carattere 'a', quindi digitare **+** un punto qualsiasi della visualizzazione di testo.

     Un quadrato viola dovrebbe apparire su ogni carattere 'a' nel file.
