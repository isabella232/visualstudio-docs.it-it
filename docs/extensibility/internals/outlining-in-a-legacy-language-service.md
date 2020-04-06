---
title: Struttura in un servizio di linguaggio Legacy Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: be485a0e7406d49c4dcce77958c720e0b62504b6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706807"
---
# <a name="outlining-in-a-legacy-language-service"></a>Struttura in un servizio di linguaggio legacy
La struttura consente di comprimere un programma complesso in una panoramica o in una struttura. Ad esempio, tutti i metodi possono essere compressi in una sola riga, mostrando solo la firma del metodo. Inoltre, le strutture e le classi possono essere compresse per mostrare solo i nomi delle strutture e delle classi. All'interno di un singolo metodo, la logica complessa può essere compressa `foreach`per `if`mostrare `while`il flusso complessivo mostrando solo la prima riga di istruzioni, ad esempio , e .

 Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni, vedere [Procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="enabling-support-for-outlining"></a>Abilitazione del supporto per la strutturaEnabling Support for Outlining
 La `AutoOutlining` voce del Registro di sistema è impostata su 1 per abilitare la struttura automatica. La struttura automatica imposta un'analisi dell'intera origine quando un file viene caricato o modificato per identificare le aree nascoste e mostrare i glifi della struttura. La struttura può anche essere controllata manualmente dall'utente.

 Il valore `AutoOutlining` della voce del Registro di sistema può essere ottenuto tramite la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> proprietà nella <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. La `AutoOutlining` voce del Registro di sistema <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> può essere inizializzata con un parametro denominato per l'attributo (vedere Registrazione di un servizio di [linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md) per informazioni dettagliate).

## <a name="the-hidden-region"></a>La regione nascosta
 Per fornire la struttura, il servizio di linguaggio deve supportare le aree nascoste. Si tratta di intervalli di testo che possono essere espansi o compressi. Le aree nascoste possono essere delimitate da simboli di linguaggio standard, ad esempio parentesi graffe, o da simboli personalizzati. Ad esempio, in `#region` / `#endregion` Cè è associata una coppia che delimita un'area nascosta.

 Le aree nascoste vengono gestite da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> un gestore di aree nascoste, esposto come interfaccia.

 La struttura utilizza <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> le aree nascoste dell'interfaccia e contiene l'intervallo dell'area nascosta, lo stato visibile corrente e l'intestazione da visualizzare quando l'intervallo viene compresso.

 Il parser del <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> servizio di linguaggio utilizza il metodo per aggiungere <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> una nuova area nascosta con il comportamento predefinito per le aree nascoste, mentre il metodo consente di personalizzare l'aspetto e il comportamento della struttura. Una volta assegnate aree nascoste alla sessione dell'area nascosta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce le aree nascoste per il servizio di linguaggio.

 Se è necessario determinare quando la sessione dell'area nascosta viene eliminata, un'area nascosta viene modificata o è necessario assicurarsi che una determinata area nascosta sia visibile; è necessario derivare <xref:Microsoft.VisualStudio.Package.Source> una classe dalla classe <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>ed <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>eseguire l'override dei metodi appropriati, rispettivamente , e , .

### <a name="example"></a>Esempio
 Ecco un esempio semplificato di creazione di aree nascoste per tutte le coppie di parentesi graffe. Si presuppone che il linguaggio fornisca la corrispondenza tra parentesi graffe e che le parentesi graffe da abbinare includano almeno le parentesi graffe (Sezione e ) . Questo approccio è solo a scopo illustrativo. Un'implementazione completa avrebbe una <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>gestione completa dei casi in . In questo esempio viene <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> inoltre `true` illustrato come impostare temporaneamente la preferenza. Un'alternativa consiste `AutoOutlining` nello specificare `ProvideLanguageServiceAttribute` il parametro denominato nell'attributo nel pacchetto della lingua.

 In questo esempio vengono presupposte le regole di C' per i commenti, le stringhe e i valori letterali.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace MyLanguagePackage
{

    public class MyLanguageService : LanguageService
    {
        private LanguagePreferences m_preferences;

        public override LanguagePreferences  GetLanguagePreferences()
        {
            if (m_preferences == null)
            {
                m_preferences = new LanguagePreferences(this.Site,
                                                        typeof(MyLanguageService).GUID,
                                                        Name);
                m_preferences.Init();
                // Temporarily enabled auto-outlining
                m_preferences.AutoOutlining = true;
            }
            return m_preferences;
        }

        public override AuthoringScope  ParseSource(ParseRequest req)
        {
            Source source = (Source) this.GetSource(req.FileName);
            switch (req.Reason)
            {
               case ParseReason.HighlightBraces:
               case ParseReason.MatchBraces:
               case ParseReason.MemberSelectAndHighlightBraces:
                  if (source.Braces != null)
                  {
                      foreach (TextSpan[] brace in source.Braces)
                      {
                         if (brace.Length == 2)
                         {
                             if (req.Sink.HiddenRegions == true
                                   && source.GetText(brace[0]).Equals("{")
                                   && source.GetText(brace[1]).Equals("}"))
                             {
                                //construct a TextSpan of everything between the braces
                                TextSpan hideSpan = new TextSpan();
                                hideSpan.iStartIndex = brace[0].iStartIndex;
                                hideSpan.iStartLine = brace[0].iStartLine;
                                hideSpan.iEndIndex = brace[1].iEndIndex;
                                hideSpan.iEndLine = brace[1].iEndLine;
                                req.Sink.ProcessHiddenRegions = true;
                                req.Sink.AddHiddenRegion(hideSpan);
                             }
                             req.Sink.MatchPair(brace[0], brace[1], 1);
                         }
                         else if (brace.Length >= 3)
                             req.Sink.MatchTriple(brace[0], brace[1], brace[2], 1);
                  }
        }
                   break;
               default:
                   break;
      }
            // Must always return a valid AuthoringScope object.
            return new MyAuthoringScope();
        }
    }
}
```

## <a name="see-also"></a>Vedere anche
- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
