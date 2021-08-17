---
title: Proprietà personalizzate dei documenti nei servizi di linguaggio legacy
description: Informazioni su come creare proprietà personalizzate del documento visualizzate nel Visual Studio Finestra Proprietà, come parte di un servizio di linguaggio legacy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- custom document properties, language services [managed package framework]
- document properties, custom
- language services [managed package framework], custom document properties
ms.assetid: cc714a67-b33e-4440-9203-3c90f648bd9c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 6bff9a834c40396ea7ad34689787c85cb6b46345
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122050072"
---
# <a name="custom-document-properties-in-a-legacy-language-service"></a>Proprietà personalizzate del documento in un servizio di linguaggio legacy
Le proprietà del documento possono essere visualizzate nella [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **finestra** Proprietà. I linguaggi di programmazione in genere non hanno proprietà associate ai singoli file di origine. XML supporta tuttavia le proprietà del documento che influiscono sulla codifica, sullo schema e sul foglio di stile.

## <a name="discussion"></a>Discussione
 Se il linguaggio richiede proprietà del documento personalizzate, è necessario derivare una classe dalla classe e implementare le <xref:Microsoft.VisualStudio.Package.DocumentProperties> proprietà necessarie nella classe derivata.

 Inoltre, le proprietà del documento vengono in genere archiviate nel file di origine stesso. Ciò richiede al servizio di linguaggio di analizzare le  informazioni sulle proprietà del file di origine da visualizzare nella finestra Proprietà e di aggiornare il file di origine quando viene apportata una modifica alle proprietà del documento nella finestra **Proprietà.**

## <a name="customize-the-documentproperties-class"></a>Personalizzare la classe DocumentProperties
 Per supportare le proprietà personalizzate del documento, è necessario derivare una classe dalla classe e aggiungere tutte le <xref:Microsoft.VisualStudio.Package.DocumentProperties> proprietà necessarie. È anche necessario specificare gli attributi utente per organizzarli nella **visualizzazione della** finestra Proprietà. Se una proprietà ha solo una funzione di accesso, viene visualizzata `get` come di sola lettura nella **finestra** Proprietà. Se una proprietà ha `get` entrambe le funzioni di accesso e `set` , la proprietà può essere aggiornata anche nella **finestra** Proprietà .

### <a name="example"></a>Esempio
 Ecco una classe di esempio derivata da <xref:Microsoft.VisualStudio.Package.DocumentProperties> , che mostra due `Filename` proprietà, e `Description` . Quando una proprietà viene aggiornata, viene chiamato un metodo personalizzato nella <xref:Microsoft.VisualStudio.Package.LanguageService> classe per scrivere la proprietà nel file di origine.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestDocumentProperties : DocumentProperties
    {
        private string m_filename;
        private string m_description;

        public TestDocumentProperties(CodeWindowManager mgr)
            : base(mgr)
        {
        }

        // Helper function to initialize this property without
        // going through the FileName property (which does a lot
        // more than we need when the filename is set).
        public void SetFileName(string filename)
        {
            m_filename = filename;
        }

        // Helper function to initialize this property without
        // going through the Description property (which does a lot
        // more than we need when the description is set).
        public void SetDescription(string description)
        {
            m_description = description;
        }

        ////////////////////////////////////////////////////////////
        // The document properties

        [CategoryAttribute("General")]
        [DescriptionAttribute("Name of the file")]
        [DisplayNameAttribute("Filename")]
        public string FileName
        {
            get { return m_filename; }
            set
            {
               if (value != m_filename)
               {
                    m_filename = value;
                    SetPropertyValue("Filename", m_filename);
               }
            }
        }

        [CategoryAttribute("General")]
        [DescriptionAttribute("Description of the file")]
        [DisplayNameAttribute("Description")]
        public string Description
        {
            get { return m_description; }
            set
            {
                if (value != m_description)
                {
                    m_description = value;
                    SetPropertyValue("Description", m_description);
                }
            }
        }

        ///////////////////////////////////////////////////////////
        // Private methods.

        private void SetPropertyValue(string propertyName, string propertyValue)
        {
            Source src = this.GetSource();
            if (src != null)
            {
                TestLanguageService service = src.LanguageService as TestLanguageService;
                if (service != null)
                {
                    // Set the property in to the source file.
                    service.SetPropertyValue(src, propertyName, propertyValue);
                }
            }
        }
    }
}
```

## <a name="instantiate-the-custom-documentproperties-class"></a>Creare un'istanza della classe DocumentProperties personalizzata
 Per creare un'istanza della classe delle proprietà del documento personalizzata, è necessario eseguire l'override del metodo nella versione della classe per restituire <xref:Microsoft.VisualStudio.Package.LanguageService.CreateDocumentProperties%2A> una singola istanza della <xref:Microsoft.VisualStudio.Package.LanguageService> <xref:Microsoft.VisualStudio.Package.DocumentProperties> classe.

### <a name="example"></a>Esempio

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        private TestDocumentProperties m_documentProperties;

        public override DocumentProperties CreateDocumentProperties(CodeWindowManager mgr)
        {
            if (m_documentProperties == null)
            {
                m_documentProperties = new TestDocumentProperties(mgr);
            }
            return m_documentProperties;
        }
    }
}
```

## <a name="properties-in-the-source-file"></a>Proprietà nel file di origine
 Poiché le proprietà del documento sono in genere specifiche del file di origine, i valori vengono archiviati nel file di origine stesso. Per definire queste proprietà, è necessario il supporto del parser o dello scanner del linguaggio. Ad esempio, le proprietà di un documento XML vengono archiviate nel nodo radice. I valori nel nodo radice vengono modificati quando **i** valori della finestra Proprietà vengono modificati e il nodo radice viene aggiornato nell'editor.

### <a name="example"></a>Esempio
 In questo esempio vengono archiviate le proprietà e nelle prime due righe del file di `Filename` `Description` origine, incorporate in un'intestazione di commento speciale, come segue:

```
//!Filename = file.testext
//!Description = A sample file
```

 In questo esempio vengono illustrati i due metodi necessari per ottenere e impostare le proprietà del documento dalle prime due righe del file di origine, nonché il modo in cui le proprietà vengono aggiornate se l'utente modifica direttamente il file di origine. Il metodo nell'esempio illustrato di seguito è lo stesso chiamato dalla classe , come illustrato nella sezione Personalizzazione della `SetPropertyValue` `TestDocumentProperties` classe *DocumentProperties.*

 In questo esempio viene utilizzato lo scanner per determinare il tipo di token nelle prime due righe. Questo esempio è solo a scopo illustrativo. Un approccio più tipico a questa situazione consiste nell'analizzare il file di origine in quello che viene chiamato albero di analisi in cui ogni nodo dell'albero contiene informazioni su un token specifico. Il nodo radice conterrà le proprietà del documento.

```csharp
using System.ComponentModel;
using Microsoft.VisualStudio.Package;

namespace TestLanguagePackage
{
    // TokenType.Comment is the last item in that enumeration.
    public enum TestTokenTypes
    {
        DocPropertyLine = TokenType.Comment + 1,
        DocPropertyName,
        DocPropertyAssign,
        DocPropertyValue
    }

    class TestLanguageService : LanguageService
    {
        // Search this many lines from the beginning for properties.
        private static int maxLinesToSearch = 2;

        private TestDocumentProperties m_documentProperties;

        // Called whenever a full parsing operation has completed.
        public override void OnParseComplete(ParseRequest req)
        {
            if (m_documentProperties != null)
            {
                Source src = GetSource(req.View);
                if (src != null)
                {
                    string value = GetPropertyValue(src, "Filename");
                    m_documentProperties.SetFileName(value);

                    value = GetPropertyValue(src, "Description");
                    m_documentProperties.SetDescription(value);

                    // Update the Properties Window.
                    m_documentProperties.Refresh();
                }
            }
        }

        // Retrieves the specified property value from the given source.
        public string GetPropertyValue(Source src, string propertyName)
        {
            string propertyValue = "";

            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    string      line;
                    TokenInfo[] lineInfo = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line.
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                for ( ;
                                     tokenIndex < lineInfo.Length;
                                     tokenIndex++)
                                {
                                    if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyValue)
                                    {
                                        break;
                                    }
                                }
                                if (tokenIndex < lineInfo.Length)
                                {
                                    propertyValue = src.GetText(i,
                                                          lineInfo[tokenIndex].StartIndex,
                                                          i,
                                                          lineInfo[tokenIndex].EndIndex + 1);
                                }
                                break;
                            }
                        }
                    }
                }
            }
            return propertyValue;
        }

        // Sets the specified property into the given source file.
        // Called from the TestDocumentProperties class.
        public void SetPropertyValue(Source src, string propertyName, string propertyValue)
        {
            string newLine;

            if (propertyName == null || propertyName == "")
            {
                // No property name, so nothing to do
                return;
            }
            if (propertyValue == null)
            {
                propertyValue = "";
            }
            // This is the line to be inserted.
            newLine = String.Format("//!{0} = {1}", propertyName, propertyValue);

            // First, find the line on which the property belongs.
            // If line is found, replace it.
            // Otherwise, insert the line at the beginning of the file.
            if (src != null)
            {
                IVsTextColorState colorState = src.ColorState;
                if (colorState != null)
                {
                    int         lineNumber = -1;
                    string      line;
                    TokenInfo[] lineInfo   = null;
                    int         i;

                    for (i = 0; i < maxLinesToSearch; i++)
                    {
                        line     = src.GetLine(i);
                        lineInfo = src.GetColorizer().GetLineInfo(
                                                        src.GetTextLines(),
                                                        i,
                                                        colorState);
                        if (lineInfo == null)
                        {
                            continue;
                        }
                        if (lineInfo[0].Type != (TokenType)TestTokenTypes.DocPropertyLine)
                        {
                            // Not a property line
                            continue;
                        }
                        TokenInfo valueInfo = new TokenInfo();
                        int tokenIndex = -1;
                        for (tokenIndex = 0;
                             tokenIndex < lineInfo.Length;
                             tokenIndex++)
                        {
                            if (lineInfo[tokenIndex].Type == (TokenType)TestTokenTypes.DocPropertyName)
                            {
                                break;
                            }
                        }
                        if (tokenIndex >= lineInfo.Length)
                        {
                            // No property name on the line.
                            continue;
                        }
                        string name = src.GetText(i,
                                                  lineInfo[tokenIndex].StartIndex,
                                                  i,
                                                  lineInfo[tokenIndex].EndIndex + 1);
                        if (name != null)
                        {
                            if (String.Compare(name, propertyName, true) == 0)
                            {
                                lineNumber = i;
                                break;
                            }
                        }
                    }

                    // Set up an undo context that also handles the insert/replace.
                    EditArray editArray = new EditArray(src,
                                                        true,
                                                        "Update Property");
                    if (editArray != null)
                    {
                        TextSpan span = new TextSpan();
                        if (lineNumber != -1)
                        {
                            // Replace line.
                            int lineLength = 0;
                            src.GetTextLines().GetLengthOfLine(lineNumber,
                                                               out lineLength);
                            span.iStartLine  = lineNumber;
                            span.iStartIndex = 0;
                            span.iEndLine    = lineNumber;
                            span.iEndIndex   = lineLength;
                        }
                        else
                        {
                            // Insert new line.
                            span.iStartLine  = 0;
                            span.iStartIndex = 0;
                            span.iEndLine    = 0;
                            span.iEndIndex   = 0;
                            newLine += "\n";
                        }
                        editArray.Add(new EditSpan(span, newLine));
                        editArray.ApplyEdits();
                    }
                }
            }
        }
    }
}
```

## <a name="see-also"></a>Vedi anche
- [Funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
