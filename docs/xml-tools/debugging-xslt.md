---
title: Modalità di debug di codice XSLT
ms.date: 03/05/2019
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- multiple
ms.openlocfilehash: 67ea95e3c52daed03acfe451f353edc039e1fecb
ms.sourcegitcommit: 9753c7544cec852ca5efd0834e0956d9e53a5734
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/13/2019
ms.locfileid: "67043531"
---
# <a name="debugging-xslt"></a>Debug di fogli di stile XSLT (Extensible Stylesheet Language Transformation)

È possibile eseguire il debug di codice XSLT in Visual Studio. La trasformazione XSLT il debugger supporta l'impostazione di punti di interruzione, la visualizzazione degli stati di esecuzione di XSLT e così via. Il debugger XSLT è utilizzabile per il debug di fogli di stile XSLT o le applicazioni XSLT.

Per istruzioni, ignorandole o eseguendole di fuori di codice, è possibile eseguire una riga di codice alla volta. I comandi per l'uso di funzionalità di esecuzione codice del debugger XSLT sono che identici a quelli per Visual Studio debugger.

Una volta avviato il debug, nel debugger XSLT vengono aperte finestre di visualizzazione del documento di input e dell'output XSLT.

> [!NOTE]
> Il debugger XSLT è disponibile solo nelle edizioni Professional ed Enterprise di Visual Studio.

## <a name="debug-from-the-xml-editor"></a>Eseguire il debug dall'editor XML

È possibile avviare il debugger quando si dispone di un foglio di stile o un file XML di input aprire nell'editor. Ciò consente di eseguire il debug quando si progetta il foglio di stile.

1. Aprire il foglio di stile o un file XML in Visual Studio.

1. Selezionare **avviare il debug di XSLT** dalle **XML** dal menu oppure premere **Alt**+**F5**.

## <a name="debug-from-an-app-that-uses-xslt"></a>Eseguire il debug da un'app che usa XSLT

È possibile eseguire le istruzioni XSLT durante il debug di un'applicazione. Quando si preme **F11** su un <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A?displayProperty=fullName> chiamata, il debugger può eseguire il codice XSLT.

> [!NOTE]
> Non è supportata l'esecuzione di istruzioni XSLT dalla classe <xref:System.Xml.Xsl.XslTransform>. La classe <xref:System.Xml.Xsl.XslCompiledTransform> è l'unico processore XSLT in grado di supportare l'esecuzione di istruzioni XSLT durante il debug.

### <a name="to-start-debugging-an-xslt-application"></a>Per avviare il debug di un'applicazione XSLT

1. Durante la creazione dell'istanza dell'oggetto <xref:System.Xml.Xsl.XslCompiledTransform>, impostare il parametro `enableDebug` su `true` nel codice. In questo modo viene indicato al processore XSLT di creare le informazioni di debug dopo la compilazione del codice.

1. Premere **F11** per eseguire l'istruzione il codice XSLT.

   Il foglio di stile XSLT viene caricato in una nuova finestra del documento e avvia il debugger XSLT.

   In alternativa, è possibile aggiungere un punto di interruzione al foglio di stile ed eseguire l'applicazione.

### <a name="example"></a>Esempio

Di seguito è riportato un esempio di programma XSLT in C#. Viene illustrato come abilitare il debug di XSLT.

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Xsl;

namespace ConsoleApplication
{
  class Program
  {
    private const string sourceFile = @"c:\data\xsl_files\books.xml";
    private const string stylesheet = @"c:\data\xsl_files\below-average.xsl";
    private const string outputFile = @"c:\data\xsl_files\output.xml";

    static void Main(string[] args)
    {
      // Enable XSLT debugging.
      XslCompiledTransform xslt = new XslCompiledTransform(true);

      // Compile the style sheet.
      xslt.Load(stylesheet)

      // Execute the XSLT transform.
      FileStream outputStream = new FileStream(outputFile, FileMode.Append);
      xslt.Transform(sourceFile, null, outputStream);
    }
  }
}
```

## <a name="xslt-profiler"></a>Profiler XSLT

Il [profiler XSLT](../xml-tools/xslt-profiler.md) è uno strumento che consente agli sviluppatori di misurare, valutare e trattare problemi correlati alle prestazioni nel codice XSLT creando rapporti di prestazioni XSLT dettagliati. Per altre informazioni, vedere [profiler XSLT](../xml-tools/xslt-profiler.md).

## <a name="see-also"></a>Vedere anche

- [Procedura dettagliata: Eseguire il debug di un foglio di stile XSLT](../xml-tools/walkthrough-debug-an-xslt-style-sheet.md)
- [Sguardo al debugger di Visual Studio](../debugger/debugger-feature-tour.md)
- [Informazioni di base sul debug: Punti di interruzione](../debugger/using-breakpoints.md)
