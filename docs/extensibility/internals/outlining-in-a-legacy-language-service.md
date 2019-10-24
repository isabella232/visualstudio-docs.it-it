---
title: Struttura in un servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a6b2ba55a2e77a1f7261812a181ad780c2ef2b71
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72726169"
---
# <a name="outlining-in-a-legacy-language-service"></a>Struttura in un servizio di linguaggio legacy
La struttura rende possibile la compressione di un programma complesso in una panoramica o una struttura. Ad esempio, in C# tutti i metodi possono essere compressi in una sola riga, mostrando solo la firma del metodo. Inoltre, le strutture e le classi possono essere compresse per visualizzare solo i nomi delle strutture e delle classi. All'interno di un singolo metodo, la logica complessa può essere compressa per mostrare il flusso generale mostrando solo la prima riga di istruzioni, ad esempio `foreach`, `if` e `while`.

 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni, vedere [procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="enabling-support-for-outlining"></a>Abilitazione del supporto per la struttura
 La voce del registro di sistema `AutoOutlining` è impostata su 1 per abilitare la struttura automatica. La struttura automatica configura un'analisi dell'intera origine quando un file viene caricato o modificato per identificare le aree nascoste e Mostra i glifi della struttura. La struttura può essere controllata anche manualmente dall'utente.

 Il valore della voce del registro di sistema `AutoOutlining` può essere ottenuto tramite la proprietà <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> della classe <xref:Microsoft.VisualStudio.Package.LanguagePreferences>. La voce del registro di sistema `AutoOutlining` può essere inizializzata con un parametro denominato nell'attributo <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> (vedere [registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md) per informazioni dettagliate).

## <a name="the-hidden-region"></a>Area nascosta
 Per fornire la struttura, il servizio di linguaggio deve supportare le aree nascoste. Si tratta di un intervallo di testo che può essere espanso o compresso. Le aree nascoste possono essere delimitate da simboli di linguaggio standard, ad esempio parentesi graffe o simboli personalizzati. C# Dispone ad esempio di un `#region` / `#endregion` coppia che delimita un'area nascosta.

 Le aree nascoste sono gestite da un gestore di aree nascoste, esposto come interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession>.

 La struttura Usa aree nascoste l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> e contiene l'intervallo dell'area nascosta, lo stato visibile corrente e il banner da visualizzare quando l'intervallo è compresso.

 Il parser del servizio di linguaggio usa il metodo <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> per aggiungere una nuova area nascosta con il comportamento predefinito per le aree nascoste, mentre il metodo <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> consente di personalizzare l'aspetto e il comportamento della struttura. Una volta assegnate le aree nascoste alla sessione dell'area nascosta, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gestisce le aree nascoste per il servizio di linguaggio.

 Se è necessario determinare quando la sessione dell'area nascosta viene distrutta, viene modificata un'area nascosta oppure è necessario assicurarsi che sia visibile una determinata area nascosta; è necessario derivare una classe dalla classe <xref:Microsoft.VisualStudio.Package.Source> ed eseguire l'override rispettivamente dei metodi, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> e <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> appropriati.

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio semplificato di creazione di aree nascoste per tutte le coppie di parentesi graffe. Si presuppone che il linguaggio fornisca la corrispondenza tra parentesi graffe e che le parentesi graffe da confrontare includano almeno le parentesi graffe ({e}). Questo approccio è solo a scopo illustrativo. Un'implementazione completa avrebbe una gestione completa dei case in <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. Questo esempio illustra anche come impostare la preferenza <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> su `true` temporaneamente. In alternativa, è possibile specificare il `AutoOutlining` parametro denominato nell'attributo `ProvideLanguageServiceAttribute` nel pacchetto di linguaggio.

 In questo esempio C# si presuppone la presenza di regole per commenti, stringhe e valori letterali.

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