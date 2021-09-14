---
title: Struttura in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni su come supportare la struttura tramite l'implementazione di aree nascoste in un servizio di linguaggio legacy.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: c9a4906b500d7c073f3f17d06e04b656f27be1fb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709531"
---
# <a name="outlining-in-a-legacy-language-service"></a>Struttura in un servizio di linguaggio legacy
La struttura consente di comprimere un programma complesso in una panoramica o in una struttura. In C#, ad esempio, tutti i metodi possono essere compressi in una singola riga, visualizzando solo la firma del metodo. Inoltre, le strutture e le classi possono essere compresse per visualizzare solo i nomi delle strutture e delle classi. All'interno di un singolo metodo è possibile comprimere la logica complessa per visualizzare il flusso complessivo visualizzando solo la prima riga di istruzioni, ad esempio `foreach` `if` , e `while` .

 I servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni, vedere [Procedura dettagliata: Struttura .](../../extensibility/walkthrough-outlining.md)

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. In questo modo si miglioreranno le prestazioni del servizio di linguaggio e si potranno sfruttare le nuove funzionalità dell'editor.

## <a name="enabling-support-for-outlining"></a>Abilitazione del supporto per la struttura
 La `AutoOutlining` voce del Registro di sistema è impostata su 1 per abilitare la struttura automatica. La struttura automatica configura un'analisi dell'intera origine quando un file viene caricato o modificato per identificare le aree nascoste e visualizzare i glifi di struttura. La struttura può anche essere controllata manualmente dall'utente.

 Il valore della voce `AutoOutlining` del Registro di sistema può essere ottenuto tramite la proprietà della classe <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> <xref:Microsoft.VisualStudio.Package.LanguagePreferences> . La `AutoOutlining` voce del Registro di sistema può essere inizializzata con un parametro denominato per l'attributo . Per informazioni dettagliate, vedere Registrazione di un servizio di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> [linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md) legacy.

## <a name="the-hidden-region"></a>Area nascosta
 Per fornire la struttura, il servizio di linguaggio deve supportare le aree nascoste. Si tratta di intervalli di testo che possono essere espansi o compressi. Le aree nascoste possono essere delimitate da simboli di lingua standard, ad esempio parentesi graffe o simboli personalizzati. Ad esempio, C# ha una `#region` / `#endregion` coppia che delimita un'area nascosta.

 Le aree nascoste vengono gestite da un gestore di aree nascoste, esposto come <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interfaccia.

 La struttura usa le aree nascoste dell'interfaccia e contengono l'intervallo dell'area nascosta, lo stato visibile corrente e il banner da visualizzare quando <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> l'intervallo viene compresso.

 Il parser del servizio di linguaggio usa il metodo per aggiungere una nuova area nascosta con il comportamento predefinito per le aree nascoste, mentre il metodo consente di personalizzare l'aspetto e il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> comportamento della struttura. Dopo aver assegnato aree nascoste alla sessione dell'area nascosta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce le aree nascoste per il servizio di linguaggio.

 Se è necessario determinare quando la sessione dell'area nascosta viene distrutta, un'area nascosta viene modificata o è necessario assicurarsi che una determinata area nascosta sia visibile. è necessario derivare una classe dalla <xref:Microsoft.VisualStudio.Package.Source> classe ed eseguire l'override dei metodi appropriati, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> rispettivamente , e <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> .

### <a name="example"></a>Esempio
 Ecco un esempio semplificato di creazione di aree nascoste per tutte le coppie di parentesi graffe. Si presuppone che il linguaggio includa la corrispondenza delle parentesi graffe e che le parentesi graffe da trovare includano almeno le parentesi graffe ({ e }). Questo approccio è solo a scopo illustrativo. Un'implementazione completa avrebbe una gestione completa dei case in <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . Questo esempio mostra anche come impostare temporaneamente <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> la `true` preferenza su . In alternativa, specificare il `AutoOutlining` parametro denominato `ProvideLanguageServiceAttribute` nell'attributo nel pacchetto del linguaggio.

 Questo esempio presuppone regole C# per commenti, stringhe e valori letterali.

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

## <a name="see-also"></a>Vedi anche
- [Funzionalità dei servizi di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
