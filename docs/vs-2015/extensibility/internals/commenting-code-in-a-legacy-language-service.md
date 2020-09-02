---
title: Commento al codice in un servizio di linguaggio legacy | Microsoft Docs
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "68160916"
---
# <a name="commenting-code-in-a-legacy-language-service"></a>Aggiunta di commenti al codice in un servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

I linguaggi di programmazione forniscono in genere un mezzo per aggiungere annotazioni o aggiungere commenti al codice. Un commento è una sezione di testo che fornisce informazioni aggiuntive sul codice, ma viene ignorato durante la compilazione o l'interpretazione.  
  
 Le classi del Framework di pacchetto gestito (MPF) forniscono supporto per la creazione di commenti e il testo selezionato.  
  
## <a name="comment-styles"></a>Stili di commento  
 Sono disponibili due stili generali per il commento:  
  
1. Commenti alla riga, in cui il commento si trova su una sola riga.  
  
2. Blocca i commenti, in cui il commento può includere più righe.  
  
   I commenti della riga hanno in genere un carattere iniziale (o caratteri), mentre i commenti del blocco hanno sia caratteri iniziali che finali. Ad esempio, in C#, un commento di riga inizia con//e un commento di blocco inizia con/* e termina con \* /.  
  
   Quando l'utente seleziona la **selezione di commenti** del comando dal menu **modifica**  ->  **Avanzate** , il comando viene indirizzato al <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> metodo della <xref:Microsoft.VisualStudio.Package.Source> classe. Quando l'utente seleziona il comando **Rimuovi commento selezione**, il comando viene indirizzato al <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> metodo.  
  
## <a name="supporting-code-comments"></a>Supporto di commenti del codice  
 È possibile fare in modo che il servizio di linguaggio supporti i commenti del codice tramite il `EnableCommenting` parametro denominato di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Viene impostata la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> proprietà della <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Per ulteriori informazioni sull'impostazione delle funzionalità del linguaggio Servicce, vedere la pagina relativa alla [registrazione di un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md).  
  
 È inoltre necessario eseguire l'override del <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metodo per restituire una <xref:Microsoft.VisualStudio.Package.CommentInfo> struttura con i caratteri di commento per la lingua. I caratteri di commento della riga di tipo C# rappresentano il valore predefinito.  
  
### <a name="example"></a>Esempio  
 Di seguito è riportato un esempio di implementazione del <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metodo.  
  
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
