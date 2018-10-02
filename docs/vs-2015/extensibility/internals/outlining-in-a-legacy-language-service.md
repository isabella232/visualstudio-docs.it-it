---
title: La struttura in un servizio di linguaggio Legacy | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- outlining
- language services [managed package framework], outlining
- outlining, supporting in language services [managed package framework]
ms.assetid: 7b5578b4-a20a-4b94-ad4c-98687ac133b9
caps.latest.revision: 16
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 9e450a41db4e56067424e89acf8bb4af048acfc8
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47541020"
---
# <a name="outlining-in-a-legacy-language-service"></a>Struttura in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [della struttura in un servizio di linguaggio Legacy](https://docs.microsoft.com/visualstudio/extensibility/internals/outlining-in-a-legacy-language-service).  
  
La struttura rende possibile comprimere un programma complesso panoramica in o in una struttura. Ad esempio, in c# tutti i metodi possono essere compressi in una singola riga, che mostra solo la firma del metodo. Inoltre, classi e strutture possono essere compressi per mostrare solo i nomi delle classi e strutture. All'interno di un singolo metodo, è possibile comprimere una logica complessa in modo da mostrare il flusso generale che mostra solo la prima riga di istruzioni, ad esempio `foreach`, `if`, e `while`.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni, vedere [procedura dettagliata: struttura](../../extensibility/walkthrough-outlining.md).  
  
> [!NOTE]
>  È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## <a name="enabling-support-for-outlining"></a>Abilitazione del supporto per la struttura  
 Il `AutoOutlining` voce del Registro di sistema è impostata su 1 per abilitare la struttura automatica. La struttura automatica consente di impostare un'analisi dell'intera origine quando un file viene caricato o modificato allo scopo di identificare le aree nascoste e Mostra le icone della struttura. La struttura può anche essere controllata anche manualmente dall'utente.  
  
 Il valore del `AutoOutlining` voce del Registro di sistema può essere ottenuto tramite il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> proprietà di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Il `AutoOutlining` voce del Registro di sistema può essere inizializzati con un parametro denominato per il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo (vedere [registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md) per informazioni dettagliate).  
  
## <a name="the-hidden-region"></a>L'area nascosta  
 Per fornire la struttura, il servizio di linguaggio deve supportare le aree nascoste. Si tratta di intervalli di testo che possono essere espansi o compressi. Le aree nascoste possono essere delimitate dai simboli standard del linguaggio, ad esempio le parentesi graffe, o dai simboli personalizzati. Ad esempio, c# ha un `#region` / `#endregion` coppia che delimita un'area nascosta.  
  
 Le aree nascoste sono gestite da un responsabile di area nascosta, che viene esposto come il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> interfaccia.  
  
 La struttura Usa le aree nascoste le <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenRegion> interfaccia e contenere l'intervallo dell'area nascosta, lo stato visibile corrente e il banner da visualizzare quando l'intervallo è compressa.  
  
 Il parser servizio di linguaggio utilizza il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metodo per aggiungere una nuova area nascosta con il comportamento predefinito per le aree nascoste, mentre il <xref:Microsoft.VisualStudio.Package.AuthoringSink.AddHiddenRegion%2A> metodo consente di personalizzare l'aspetto e comportamento del contorno. Una volta che le aree nascoste sono concesso per la sessione di area nascosta, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] gestisce le aree nascoste per il servizio di linguaggio.  
  
 Se è necessario determinare quando viene eliminata definitivamente la sessione di area nascosta, un'area nascosta viene modificata o è necessario assicurarsi che una determinata area nascosta è visibile; è necessario derivare una classe dalla classe la <xref:Microsoft.VisualStudio.Package.Source> classe ed eseguire l'override dei metodi appropriati, <xref:Microsoft.VisualStudio.Package.Source.OnBeforeSessionEnd%2A>, <xref:Microsoft.VisualStudio.Package.Source.OnHiddenRegionChange%2A>, e <xref:Microsoft.VisualStudio.Package.Source.MakeBaseSpanVisible%2A>, rispettivamente.  
  
### <a name="example"></a>Esempio  
 Ecco un esempio semplificato di creazione di aree nascoste per tutte le coppie di parentesi graffe. Si presuppone che il linguaggio fornisce corrispondenza parentesi graffe e che le parentesi graffe devono corrispondere almeno includono le parentesi graffe ({e}). Questo approccio è solo a scopo illustrativo. Un'implementazione completa avrebbe una gestione completa dei case in <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A>. In questo esempio viene inoltre illustrato come impostare il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.AutoOutlining%2A> preferenza `true` temporaneamente. In alternativa è possibile specificare il `AutoOutlining` parametro denominato nella `ProvideLanguageServiceAttribute` attributo nel pacchetto di linguaggio.  
  
 Questo esempio si presuppone le regole di c# per i commenti, stringhe e valori letterali.  
  
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

