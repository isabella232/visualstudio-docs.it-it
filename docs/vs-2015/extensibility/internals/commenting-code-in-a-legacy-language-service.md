---
title: Commenti di codice in un servizio di linguaggio Legacy | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: cd1405456ca9a6ba00926c82bcc7959ea36d26c2
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58964611"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Aggiunta di commenti al codice in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I linguaggi di programmazione in genere forniscono un mezzo per inserire annotazioni o commenti nel codice. Un commento è una sezione di testo che fornisce informazioni aggiuntive sul codice, ma viene ignorato durante la compilazione o interpretazione.  
  
 Le classi di framework (MPF) di pacchetto gestito forniscono supporto per l'inserimento e rimozione dei commenti sul testo selezionato.  
  
## <a name="comment-styles"></a>Stili di commento  
 Esistono due stili generali di commento:  
  
1. Commenti di riga, in cui il commento è su una singola riga.  
  
2. Commenti di blocco, dove il commento può includere più righe.  
  
   I commenti a riga sono in genere un carattere iniziale (o caratteri), mentre i commenti di blocco sono caratteri di inizio e fine. Ad esempio, nel linguaggio C#, un commento a riga inizia con / /, e inizia un blocco di commento con / * e termina con \*/.  
  
   Quando l'utente seleziona il comando **Commenta selezione** dal **modificare** -> **avanzate** dal menu il comando viene indirizzato al <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> metodo sul <xref:Microsoft.VisualStudio.Package.Source> classe. Quando l'utente seleziona il comando **rimuovere il commento dalla selezione**, il comando viene instradato al <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> (metodo).  
  
## <a name="supporting-code-comments"></a>Commenti del codice di supporto  
 È possibile avere commenti del codice supporto servizio di linguaggio per mezzo del `EnableCommenting` del parametro denominato il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Consente di impostare il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> proprietà del <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Per altre informazioni sull'impostazione della lingua servicce funzionalità, vedere [la registrazione di un servizio di linguaggio Legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)).  
  
 È anche necessario eseguire l'override di <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> per restituire un <xref:Microsoft.VisualStudio.Package.CommentInfo> struttura con i caratteri di commento per la propria lingua. C#-caratteri del commento riga stile sono quelli predefiniti.  
  
### <a name="example"></a>Esempio  
 Ecco un esempio di implementazione del <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> (metodo).  
  
```csharp  
using Microsoft.VisualStudio.Package;  
  
namespace MyLanguagePackage  
{  
    class MySource : Source  
    {  
        public override CommentInfo GetCommentFormat() {  
            CommentInfo info = new CommentInfo();  
            info.LineStart       = "//";  
            info.BlockStart      = "/*";  
            info.BlockEnd        = "*/";  
            info.UseLineComments = true;  
            return info;  
        }  
    }  
}  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)   
 [Registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
