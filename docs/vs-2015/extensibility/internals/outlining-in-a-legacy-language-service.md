---
title: Struttura in un servizio di linguaggio legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6096f89a36cdd47d2dec68af5801a94dc77acb43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "90839635"
---
# <a name="outlining-in-a-legacy-language-service"></a>Struttura in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La struttura rende possibile la compressione di un programma complesso in una panoramica o una struttura. In C#, ad esempio, tutti i metodi possono essere compressi in una sola riga, mostrando solo la firma del metodo. Inoltre, le strutture e le classi possono essere compresse per visualizzare solo i nomi delle strutture e delle classi. All'interno di un singolo metodo, la logica complessa può essere compressa per mostrare il flusso generale mostrando solo la prima riga di istruzioni, ad esempio `foreach` , `if` e `while` .  
  
 I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni, vedere [procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.  
  
## <a name="enabling-support-for-outlining"></a>Abilitazione del supporto per la struttura  
 La `AutoOutlining` voce del registro di sistema è impostata su 1 per abilitare la struttura automatica. La struttura automatica configura un'analisi dell'intera origine quando un file viene caricato o modificato per identificare le aree nascoste e Mostra i glifi della struttura. La struttura può essere controllata anche manualmente dall'utente.  
  
 Il valore della `AutoOutlining` voce del registro di sistema può essere ottenuto tramite la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> proprietà nella <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. La `AutoOutlining` voce del registro di sistema può essere inizializzata con un parametro denominato per l' <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo. per informazioni dettagliate, vedere la pagina relativa alla [registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md) .  
  
## <a name="the-hidden-region"></a>Area nascosta  
 Per fornire la struttura, il servizio di linguaggio deve supportare le aree nascoste. Si tratta di un intervallo di testo che può essere espanso o compresso. Le aree nascoste possono essere delimitate da simboli di linguaggio standard, ad esempio parentesi graffe o simboli personalizzati. Ad esempio, in C# è presente una `#region` / `#endregion` coppia che delimita un'area nascosta.  
  
 Le aree nascoste sono gestite da un gestore di aree nascoste, esposto come <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interfaccia.  
  
 La struttura Usa aree nascoste l' <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> interfaccia e contiene l'intervallo dell'area nascosta, lo stato visibile corrente e il banner da visualizzare quando l'intervallo è compresso.  
  
 Il parser del servizio di linguaggio usa il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metodo per aggiungere una nuova area nascosta con il comportamento predefinito per le aree nascoste, mentre il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metodo consente di personalizzare l'aspetto e il comportamento del contorno. Una volta assegnate le aree nascoste alla sessione dell'area nascosta, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestisce le aree nascoste per il servizio di linguaggio.  
  
 Se è necessario determinare quando la sessione dell'area nascosta viene distrutta, viene modificata un'area nascosta oppure è necessario assicurarsi che sia visibile una determinata area nascosta; è necessario derivare una classe dalla <xref:Microsoft.VisualStudio.Package.Source> classe ed eseguire l'override dei metodi appropriati, rispettivamente,, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A> <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A> e <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A> .  
  
### <a name="example"></a>Esempio  
 Di seguito è riportato un esempio semplificato di creazione di aree nascoste per tutte le coppie di parentesi graffe. Si presuppone che il linguaggio fornisca la corrispondenza tra parentesi graffe e che le parentesi graffe da confrontare includano almeno le parentesi graffe ({e}). Questo approccio è solo a scopo illustrativo. Un'implementazione completa avrebbe una gestione completa dei case in <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> . Questo esempio mostra anche come impostare la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> preferenza su `true` temporaneamente. In alternativa, è possibile specificare il `AutoOutlining` parametro denominato nell' `ProvideLanguageServiceAttribute` attributo nel pacchetto di linguaggio.  
  
 In questo esempio si presuppone la presenza di regole C# per commenti, stringhe e valori letterali.  
  
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
 [Funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
