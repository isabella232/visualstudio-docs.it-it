---
title: "Procedura dettagliata: utilizzo di un tasto di scelta rapida con un'estensione dell'editor | Microsoft Docs"
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], new - link keystrokes to commands
ms.assetid: cf6cc6c6-5a65-4f90-8f14-663decf74672
caps.latest.revision: 33
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5c9cb20bafa552c47a2f599d12e6b66fdb2bde59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201952"
---
# <a name="walkthrough-using-a-shortcut-key-with-an-editor-extension"></a>Procedura dettagliata: uso di una combinazione di tasti con un'estensione dell'editor
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile rispondere ai tasti di scelta rapida nell'estensione dell'editor. Nella procedura dettagliata seguente viene illustrato come aggiungere un'area di visualizzazione della vista a una visualizzazione di testo utilizzando un tasto di scelta rapida. Questa procedura dettagliata è basata sul modello dell'editor dell'area di visualizzazione del viewport e consente di aggiungere l'area di visualizzazione utilizzando il carattere +.  
  
## <a name="prerequisites"></a>Prerequisiti  
 A partire da Visual Studio 2015, non si installa Visual Studio SDK dall'area download. Viene inclusa come funzionalità facoltativa nel programma di installazione di Visual Studio. È anche possibile installare Visual Studio SDK in un secondo momento. Per ulteriori informazioni, vedere [installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="creating-a-managed-extensibility-framework-mef-project"></a>Creazione di un progetto Managed Extensibility Framework (MEF)  
  
1. Creare un progetto VSIX in C#. Nella finestra di dialogo **nuovo progetto** selezionare **Visual C#/extensibility**, quindi **progetto VSIX**. Assegnare un nome alla soluzione `KeyBindingTest` .  
  
2. Aggiungere un modello di elemento dell'area di testo dell'editor al progetto e denominarlo `KeyBindingTest` . Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento dell'editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3. Aggiungere i riferimenti seguenti e impostare **CopyLocal** su `false` :  
  
    Microsoft. VisualStudio. Editor  
  
    Microsoft. VisualStudio. OLE. Interop  
  
    Microsoft. VisualStudio. Shell. 14.0  
  
    Microsoft. VisualStudio. TextManager. Interop  
  
   Nel file di classe KeyBindingTest, modificare il nome della classe in PurpleCornerBox. Usare la lampadina visualizzata nel margine sinistro per apportare le altre modifiche appropriate. All'interno del costruttore, modificare il nome del livello di area di analisi da **KeyBindingTest** a **PurpleCornerBox**:  
  
```csharp  
this.layer = view.GetAdornmentLayer("PurpleCornerBox");  
```  
  
## <a name="defining-the-command-filter"></a>Definizione del filtro dei comandi  
 Il filtro dei comandi è un'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> che gestisce il comando creando un'istanza dell'area di controllo.  
  
1. Aggiungere un file di classe e assegnargli il nome `KeyBindingCommandFilter`.  
  
2. Aggiungere le istruzioni using seguenti.  
  
    ```csharp  
    using System;  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Text.Editor;  
  
    ```  
  
3. La classe denominata KeyBindingCommandFilter deve ereditare da <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  
  
    ```csharp  
    internal class KeyBindingCommandFilter : IOleCommandTarget  
    ```  
  
4. Aggiungere campi privati per la visualizzazione di testo, il comando successivo nella catena di comandi e un flag per indicare se il filtro del comando è già stato aggiunto.  
  
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
  
6. Implementare il `QueryStatus()` metodo come indicato di seguito.  
  
    ```vb  
    int IOleCommandTarget.QueryStatus(ref Guid pguidCmdGroup, uint cCmds, OLECMD[] prgCmds, IntPtr pCmdText)  
    {  
        return m_nextTarget.QueryStatus(ref pguidCmdGroup, cCmds, prgCmds, pCmdText);  
    }  
    ```  
  
7. Implementare il `Exec()` metodo in modo che aggiunga una casella viola alla visualizzazione se viene digitato un carattere +.  
  
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
  
## <a name="adding-the-command-filter"></a>Aggiunta del filtro dei comandi  
 Il provider dell'area di controllo deve aggiungere un filtro per la visualizzazione di testo. In questo esempio, il provider implementa <xref:Microsoft.VisualStudio.Editor.IVsTextViewCreationListener> per ascoltare gli eventi di creazione della visualizzazione testo. Questo provider di aree di ornamento esporta anche il livello di area di ornamento, che definisce l'ordine Z dell'area di l'area di decorazione.  
  
1. Nel file KeyBindingTestTextViewCreationListener aggiungere le istruzioni using seguenti:  
  
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
  
2. Nella definizione del livello di ornamento modificare il nome del AdornmentLayer da **KeyBindingTest** a **PurpleCornerBox**.  
  
    ```csharp  
    [Export(typeof(AdornmentLayerDefinition))]  
    [Name("PurpleCornerBox")]  
    [Order(After = PredefinedAdornmentLayers.Selection, Before = PredefinedAdornmentLayers.Text)]  
    public AdornmentLayerDefinition editorAdornmentLayer;  
    ```  
  
3. Per ottenere l'adattatore della visualizzazione di testo, è necessario importare il <xref:Microsoft.VisualStudio.Editor.IVsEditorAdaptersFactoryService> .  
  
    ```csharp  
    [Import(typeof(IVsEditorAdaptersFactoryService))]  
    internal IVsEditorAdaptersFactoryService editorFactory = null;  
  
    ```  
  
4. Modificare il <xref:Microsoft.VisualStudio.Text.Editor.IWpfTextViewCreationListener.TextViewCreated%2A> metodo in modo da aggiungere `KeyBindingCommandFilter` .  
  
    ```csharp  
    public void TextViewCreated(IWpfTextView textView)  
    {  
        AddCommandFilter(textView, new KeyBindingCommandFilter(textView));  
    }  
    ```  
  
5. Il `AddCommandFilter` gestore ottiene l'adattatore della visualizzazione di testo e aggiunge il filtro del comando.  
  
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
  
## <a name="making-the-adornment-appear-on-every-line"></a>Visualizzazione dell'area di visualizzazione in ogni riga  
 L'area di visualizzazione originale è stata visualizzata su ogni carattere "a" in un file di testo. Ora che il codice è stato modificato per aggiungere l'area di visualizzazione in risposta al carattere ' +', viene aggiunta l'area di visualizzazione solo sulla riga in cui è tipizzato ' +'. È possibile modificare il codice di area di visualizzazione in modo che l'area di visualizzazione venga visualizzata una volta in ogni ' a'.  
  
 Nel file KeyBindingTest.cs modificare il metodo CreateVisuals () per eseguire un'iterazione in tutte le righe della vista per decorare il carattere "a".  
  
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
  
## <a name="building-and-testing-the-code"></a>Compilazione e testing del codice  
  
1. Compilare la soluzione KeyBindingTest ed eseguirla nell'istanza sperimentale.  
  
2. Creare o aprire un file di testo. Digitare alcune parole contenenti il carattere "a" e quindi digitare + in un punto qualsiasi nella visualizzazione di testo.  
  
     Un quadrato viola dovrebbe essere visualizzato ogni carattere ' a' nel file.
