---
title: Aggiunta di commenti al codice in un servizio di linguaggio Legacy . Documenti Microsoft
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
ms.openlocfilehash: 5450199fde29f581dafdf9b2884c88ef26ea4ce7
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709431"
---
# <a name="comment-code-in-a-legacy-language-service"></a>Commento del codice in un servizio di linguaggio legacyComment code in a legacy language service
I linguaggi di programmazione in genere consentono di annotare o commentare il codice. Un commento è una sezione di testo che fornisce informazioni aggiuntive sul codice ma viene ignorato durante la compilazione o l'interpretazione.

 Le classi del framework di pacchetto gestito (MPF) forniscono il supporto per l'aggiunta e la modifica del commento al testo selezionato.

## <a name="comment-styles"></a>Stili di commento
Ci sono due stili generali di commento:

1. Commenti di riga, in cui il commento si trova su una singola riga.

2. Bloccare i commenti, in cui il commento può includere più righe.

I commenti di riga hanno in genere un carattere iniziale (o caratteri), mentre i commenti di blocco hanno caratteri di inizio e di fine. Ad esempio, in C, un `//`commento di riga inizia `/*` con `*/`, e un commento di blocco inizia con e termina con .

Quando l'utente seleziona il comando **Selezione commento** dal menu **Modifica** >  <xref:Microsoft.VisualStudio.Package.Source.CommentSpan%2A> **avanzate** , il comando viene indirizzato al metodo sulla <xref:Microsoft.VisualStudio.Package.Source> classe. Quando l'utente seleziona il comando **Rimuovi commento alla** <xref:Microsoft.VisualStudio.Package.Source.UncommentSpan%2A> selezione , il comando viene indirizzato al metodo .

## <a name="support-code-comments"></a>Commenti del codice di supporto
 È possibile fare in modo che i `EnableCommenting` commenti al <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> codice di supporto del servizio di linguaggio siano indicati tramite il parametro denominato dell'oggetto . In questo <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCommenting%2A> modo <xref:Microsoft.VisualStudio.Package.LanguagePreferences> viene impostata la proprietà della classe . Per ulteriori informazioni sull'impostazione delle funzionalità del servizio di linguaggio, vedere [Registrare un servizio](../../extensibility/internals/registering-a-legacy-language-service1.md)di linguaggio legacy .

 È inoltre necessario <xref:Microsoft.VisualStudio.Package.Source.GetCommentFormat%2A> eseguire l'override del metodo per restituire una <xref:Microsoft.VisualStudio.Package.CommentInfo> struttura con i caratteri di commento per la lingua. I caratteri di commento riga in stile C' sono quelli di default.

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
- [Funzionalità del servizio di linguaggio legacyLegacy language service features](../../extensibility/internals/legacy-language-service-features1.md)
- [Registrare un servizio di linguaggio legacyRegister a legacy language service](../../extensibility/internals/registering-a-legacy-language-service1.md)
