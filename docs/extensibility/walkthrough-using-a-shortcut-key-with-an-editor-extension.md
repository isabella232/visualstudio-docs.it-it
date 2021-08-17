---
title: Usare un tasto di scelta rapida con un'estensione dell'editor
description: Informazioni su come aggiungere un'area di controllo della visualizzazione a una visualizzazione di testo usando un tasto di scelta rapida. Questa procedura dettagliata si basa sul modello dell'editor dell'area di controllo del viewport.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: e07ed59b6415cc826bc6dc6d5c1e9947b51ec606
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122041516"
---
# <a name="walkthrough-use-a-shortcut-key-with-an-editor-extension"></a>Procedura dettagliata: Usare un tasto di scelta rapida con un'estensione dell'editor
È possibile rispondere ai tasti di scelta rapida nell'estensione dell'editor. La procedura dettagliata seguente illustra come aggiungere un'area di controllo della visualizzazione a una visualizzazione di testo usando un tasto di scelta rapida. Questa procedura dettagliata si basa sul modello dell'editor dell'area di controllo del viewport e consente di aggiungere l'area di controllo usando il carattere +.

## <a name="prerequisites"></a>Prerequisiti
 A partire Visual Studio 2015, non si installa Visual Studio SDK dall'Area download. È incluso come funzionalità facoltativa nella configurazione Visual Studio configurazione. È anche possibile installare VS SDK in un secondo momento. Per altre informazioni, vedere [Installare Visual Studio SDK.](../extensibility/installing-the-visual-studio-sdk.md)

## <a name="create-a-managed-extensibility-framework-mef-project"></a>Creare un Managed Extensibility Framework (MEF) Project

1. Creare un progetto VSIX C#. Nella finestra **di dialogo Project** nuova versione selezionare Visual **C# /Extensibility**, quindi **VSIX Project**. Assegnare alla soluzione il nome `KeyBindingTest` .

2. Aggiungere un modello di elemento Area di controllo testo dell'editor al progetto e assegnare al progetto il nome `KeyBindingTest` . Per altre informazioni, vedere [Creare un'estensione con un modello di elemento dell'editor.](../extensibility/creating-an-extension-with-an-editor-item-template.md)

3. Aggiungere i riferimenti seguenti e impostare **CopyLocal** su `false` :

    Microsoft.VisualStudio.Editor

    Microsoft.VisualStudio.OLE.Interop

    Microsoft.VisualStudio.Shell.14.0

    Microsoft.VisualStudio.TextManager.Interop

   Nel file di classe KeyBindingTest modificare il nome della classe in ViolaCornerBox. Usare la lampadina visualizzata nel margine sinistro per apportare le altre modifiche appropriate. All'interno del costruttore modificare il nome del livello dell'area di controllo da **KeyBindingTest** a **PurpleCornerBox:**

```csharp
this.layer = view.GetAdornmentLayer("PurpleCornerBox");
```

Nel file di classe KeyBindingTestTextViewCreationListener.cs modificare il nome di AdornmentLayer da **KeyBindingTest** a **PurpleCornerBox:**

```csharp
[Export(typeof(AdornmentLayerDefinition))]
[Name("PurpleCornerBox")]
[Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]
public AdornmentLayerDefinition editorAdornmentLayer;
```

## <a name="handle-typechar-command"></a>Gestire il comando TYPECHAR
Prima di Visual Studio 2017 versione 15.6 l'unico modo per gestire i comandi in un'estensione dell'editor era l'implementazione di un filtro <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> comandi basato su . Visual Studio 2017 versione 15.6 ha introdotto un approccio semplificato moderno basato sui gestori dei comandi dell'editor. Le due sezioni successive illustrano come gestire un comando usando sia l'approccio legacy che quello moderno.

## <a name="define-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Definire il filtro dei comandi (prima Visual Studio 2017 versione 15.6)

 Il filtro dei comandi è un'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> , che gestisce il comando creando un'istanza dell'area di controllo.

1. Aggiungere un file di classe e assegnargli il nome `KeyBindingCommandFilter`.

2. Aggiungere le direttive using seguenti.

    ```csharp
    using System;
    using System.Runtime.InteropServices;
    using Microsoft.VisualStudio.OLE.Interop;
    using Microsoft.VisualStudio;
    using Microsoft.VisualStudio.Text.Editor;

    ```

3. La classe denominata KeyBindingCommandFilter deve ereditare da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .

    ```csharp
    internal class KeyBindingCommandFilter : IOleCommandTarget
    ```

4. Aggiungere campi privati per la visualizzazione testo, il comando successivo nella catena di comandi e un flag per indicare se il filtro dei comandi è già stato aggiunto.

    ```csharp
    private IWpfTextView m_textView;
    internal IOleCommandTarget m_nextTarget;
    internal bool m_added;
    internal bool m_adorned;
    ```

5. Aggiungere un costruttore che imposta la visualizzazione testo.

    ```csharp
    public KeyBindingCommandFilter(IWpfTextView textView)
    {
        m_textView = textView;
        m_adorned = false;
    }
    ```

6. Implementare il `QueryStatus()` metodo come indicato di seguito.

    ```csharp
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)
    {
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);
    }
    ```

7. Implementare il metodo in modo da aggiungere una casella viola alla visualizzazione se viene digitato un segno `Exec()` più **+** ().

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

## <a name="add-the-command-filter-prior-to-visual-studio-2017-version-156"></a>Aggiungere il filtro dei comandi (prima Visual Studio 2017 versione 15.6)
 Il provider dell'area di controllo deve aggiungere un filtro di comando alla visualizzazione testo. In questo esempio il provider implementa per <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> restare in ascolto degli eventi di creazione della visualizzazione testo. Questo provider di elementi decorativi esporta anche il livello dell'area di controllo, che definisce l'ordine Z dell'area di controllo.

1. Nel file KeyBindingTestTextViewCreationListener aggiungere le direttive using seguenti:

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

2. Per ottenere l'adattatore di visualizzazione testo, è necessario importare <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .

    ```csharp
    [Import(typeof(IVsEditorAdaptersFactoryService))]
    internal IVsEditorAdaptersFactoryService editorFactory = null;

    ```

3. Modificare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo da aggiungere `KeyBindingCommandFilter` l'oggetto .

    ```csharp
    public void TextViewCreated(IWpfTextView textView)
    {
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));
    }
    ```

4. Il `AddCommandFilter` gestore ottiene l'adattatore di visualizzazione del testo e aggiunge il filtro del comando.

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

## <a name="implement-a-command-handler-starting-in-visual-studio-2017-version-156"></a>Implementare un gestore comandi (a partire Visual Studio 2017 versione 15.6)

Prima di tutto, aggiornare i riferimenti NuGet del progetto in modo che facciano riferimento all'API dell'editor più recente:

1. Fare clic con il pulsante destro del mouse sul progetto e **scegliere Gestisci pacchetti NuGet.**

2. In **NuGet Gestione pacchetti** selezionare la **scheda Aggiornamenti,** selezionare la **casella di controllo Seleziona tutti i** pacchetti e quindi selezionare **Aggiorna.**

Il gestore comandi è un'implementazione di <xref:Microsoft.VisualStudio.Commanding.ICommandHandler%601> , che gestisce il comando creando un'istanza dell'area di controllo.

1. Aggiungere un file di classe e assegnargli il nome `KeyBindingCommandHandler`.

2. Aggiungere le direttive using seguenti.

   ```csharp
   using Microsoft.VisualStudio.Commanding;
   using Microsoft.VisualStudio.Text.Editor;
   using Microsoft.VisualStudio.Text.Editor.Commanding.Commands;
   using Microsoft.VisualStudio.Utilities;
   using System.ComponentModel.Composition;
   ```

3. La classe denominata KeyBindingCommandHandler deve ereditare da `ICommandHandler<TypeCharCommandArgs>` ed esportarla come <xref:Microsoft.VisualStudio.Commanding.ICommandHandler> :

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

5. Implementare il `GetCommandState()` metodo come indicato di seguito. Poiché questo gestore di comandi gestisce il comando TYPECHAR dell'editor principale, può delegare l'abilitazione del comando all'editor principale.

   ```csharp
   public CommandState GetCommandState(TypeCharCommandArgs args)
   {
       return CommandState.Unspecified;
   }
   ```

6. Implementare il metodo in modo da aggiungere una casella viola alla visualizzazione se viene digitato un segno `ExecuteCommand()` più **+** ().

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

   7. Copiare la definizione del livello dell'area di controllo dal file *KeyBindingTestTextViewCreationListener.cs* in *KeyBindingCommandHandler.cs* e quindi eliminare il file *KeyBindingTestTextViewCreationListener.cs:*

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

## <a name="make-the-adornment-appear-on-every-line"></a>Fare in modo che l'area di controllo venga visualizzata in ogni riga

L'area di controllo originale è presente in ogni carattere "a" in un file di testo. Ora che il codice è stato modificato per aggiungere l'area di controllo in risposta al carattere, aggiunge l'area di controllo solo nella riga in cui è **+** **+** digitato il carattere. È possibile modificare il codice dell'area di controllo in modo che l'area di controllo venga ancora una volta visualizzata in ogni "a".

Nel file *KeyBindingTest.cs* modificare il metodo per scorrere tutte le righe nella visualizzazione per decorare `CreateVisuals()` il carattere "a".

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

1. Compilare la soluzione KeyBindingTest ed eseguirla nell'istanza sperimentale.

2. Creare o aprire un file di testo. Digitare alcune parole contenenti il carattere "a" e quindi digitare **+** un punto qualsiasi nella visualizzazione testo.

     Dovrebbe essere visualizzato un quadrato viola in ogni carattere "a" del file.
