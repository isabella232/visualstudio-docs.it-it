---
title: Commenting Code in a Legacy Language Service | Microsoft Docs
description: Informazioni sulle classi del framework del pacchetto gestito (MPF) che forniscono supporto per l'applicazione di commenti al codice in un servizio di linguaggio legacy in Visual Studio.
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
ms.openlocfilehash: d01cb64696e4f440ad0c92125dab0411c722371f2d86f478c5553f0f02f9e013
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121321207"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Aggiungere commenti al codice in un servizio di linguaggio legacy
I linguaggi di programmazione offrono in genere un modo per annotare o commentare il codice. Un commento è una sezione di testo che fornisce informazioni aggiuntive sul codice, ma viene ignorata durante la compilazione o l'interpretazione.

 Le classi del framework del pacchetto gestito (MPF) forniscono il supporto per l'impostazione di commenti e rimozione dei commenti per il testo selezionato.

## <a name="comment-styles"></a>Stili dei commenti
Esistono due stili generali di commento:

1. Commenti di riga, in cui il commento si trova su una singola riga.

2. Bloccare i commenti, in cui il commento può includere più righe.

I commenti di riga hanno in genere un carattere iniziale (o caratteri), mentre i commenti di blocco hanno sia caratteri di inizio che di fine. In C#, ad esempio, un commento di riga inizia con e un commento `//` di blocco inizia con e termina con `/*` `*/` .

Quando l'utente seleziona il comando Comment Selection (Comment **Selection)** dal menu **Edit** Advanced (Modifica avanzate), il comando viene  >   indirizzato al metodo nella <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> classe <xref:Microsoft.VisualStudio.Package.Source> . Quando l'utente seleziona il comando **Uncomment Selection**, il comando viene indirizzato al <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> metodo .

## <a name="support-code-comments"></a>Commenti del codice di supporto
 È possibile fare in modo che il servizio di linguaggio supporti i commenti del codice tramite `EnableCommenting` il parametro denominato di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . In questo modo <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> viene impostata la proprietà della <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe . Per altre informazioni sull'impostazione delle funzionalità del servizio di linguaggio, [vedere Registrare un servizio di linguaggio legacy.](../../extensibility/internals/registering-a-legacy-language-service1.md)

 È inoltre necessario eseguire l'override <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> del metodo per restituire una struttura con i caratteri di commento per la <xref:Microsoft.VisualStudio.Package.CommentInfo> lingua. I caratteri di commento di riga in stile C# sono i caratteri predefiniti.

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
