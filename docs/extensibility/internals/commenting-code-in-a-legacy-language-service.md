---
title: Commento al codice in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sulle classi del Framework di pacchetto gestito (MPF) che forniscono supporto per l'inserimento di commenti nel codice in un servizio di linguaggio legacy in Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- comments, supporting in language services [managed package framework]
- language services [managed package framework], commenting code
ms.assetid: 9600d6f0-e2b6-4fe0-b935-fb32affb97a4
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07205a8e15cd338fa1acf0d3b081301a083bba5d
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305005"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Codice di commento in un servizio di linguaggio legacy
I linguaggi di programmazione forniscono in genere un mezzo per aggiungere annotazioni o aggiungere commenti al codice. Un commento è una sezione di testo che fornisce informazioni aggiuntive sul codice, ma viene ignorato durante la compilazione o l'interpretazione.

 Le classi del Framework di pacchetto gestito (MPF) forniscono supporto per la creazione di commenti e il testo selezionato.

## <a name="comment-styles"></a>Stili di commento
Sono disponibili due stili generali per il commento:

1. Commenti alla riga, in cui il commento si trova su una sola riga.

2. Blocca i commenti, in cui il commento può includere più righe.

I commenti della riga hanno in genere un carattere iniziale (o caratteri), mentre i commenti del blocco hanno sia caratteri iniziali che finali. Ad esempio, in C#, un commento di riga inizia con e `//` un commento di blocco inizia con `/*` e termina con `*/` .

Quando l'utente seleziona la **selezione di commenti** del comando dal menu **modifica**  >  **Avanzate** , il comando viene indirizzato al <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> metodo della <xref:Microsoft.VisualStudio.Package.Source> classe. Quando l'utente seleziona il comando **Rimuovi commento selezione**, il comando viene indirizzato al <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> metodo.

## <a name="support-code-comments"></a>Commenti del codice di supporto
 È possibile fare in modo che il servizio di linguaggio supporti i commenti del codice tramite il `EnableCommenting` parametro denominato di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> . Viene impostata la <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> proprietà della <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe. Per ulteriori informazioni sull'impostazione delle funzionalità del servizio di linguaggio, vedere [registrare un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md).

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
- [Funzionalità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrare un servizio di linguaggio legacy](../../extensibility/internals/registering-a-legacy-language-service1.md)
