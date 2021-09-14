---
title: Aggiungere commenti al codice in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sulle classi MPF (Managed Package Framework) che forniscono supporto per l'applicazione di commenti al codice in un servizio di linguaggio legacy in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 92df2305d35180be4fe3df594e809c8e599fad42
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126709583"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Aggiungere commenti al codice in un servizio di linguaggio legacy
I linguaggi di programmazione forniscono in genere un mezzo per aggiungere annotazioni o aggiungere commenti al codice. Un commento è una sezione di testo che fornisce informazioni aggiuntive sul codice, ma viene ignorata durante la compilazione o l'interpretazione.

 Le classi MPF (Managed Package Framework) forniscono il supporto per aggiungere commenti e rimuovere commenti dal testo selezionato.

## <a name="comment-styles"></a>Stili dei commenti
Esistono due stili generali di commento:

1. Commenti di riga, in cui il commento si trova su una singola riga.

2. Blocca i commenti, in cui il commento può includere più righe.

I commenti di riga in genere hanno un carattere iniziale (o caratteri), mentre i commenti di blocco hanno sia caratteri di inizio che di fine. In C#, ad esempio, un commento di riga inizia con e un commento `//` di blocco inizia con e termina con `/*` `*/` .

Quando l'utente seleziona il comando **Comment Selection** (Selezione commento) dal menu **Edit**  >  **Advanced** (Modifica avanzate), il comando viene indirizzato <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> al metodo nella classe <xref:Microsoft.VisualStudio.Package.Source> . Quando l'utente seleziona il comando **Annulla commento selezione**, il comando viene indirizzato al metodo <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> .

## <a name="support-code-comments"></a>Commenti del codice di supporto
 È possibile fare in modo che il servizio di linguaggio supporti i commenti del codice tramite il `EnableCommenting` parametro denominato di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . In questo modo <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> viene impostata la proprietà della <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe . Per altre informazioni sull'impostazione delle funzionalità del servizio di linguaggio, vedere [Registrare un servizio di linguaggio legacy.](../../extensibility/internals/registering-a-legacy-language-service1.md)

 È anche necessario eseguire l'override <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> del metodo per restituire una struttura con i caratteri di commento per la <xref:Microsoft.VisualStudio.Package.CommentInfo> lingua. I caratteri di commento di riga in stile C# sono l'impostazione predefinita.

### <a name="example"></a>Esempio
 Di seguito è riportato un esempio di implementazione del <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> metodo .

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

## <a name="see-also"></a>Vedi anche
- [Funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrare un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
