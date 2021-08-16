---
title: Completamento dei membri in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sul funzionamento della descrizione comando completamento membri IntelliSense in un servizio di linguaggio legacy e su come è supportata dal framework del pacchetto gestito (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: beb0dc40253ddf4280a3cd4854c53151369098a0ef03c1c275769c498570966a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121414649"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Completamento dei membri in un servizio di linguaggio legacy

IntelliSense Member Completion è una descrizione comando che visualizza un elenco di possibili membri di un ambito specifico, ad esempio una classe, una struttura, un'enumerazione o uno spazio dei nomi. In C#, ad esempio, se l'utente tipo "this" seguito da un punto, un elenco di tutti i membri della classe o della struttura nell'ambito corrente viene visualizzato in un elenco da cui l'utente può selezionare.

Managed Package Framework (MPF) fornisce il supporto per la descrizione comando e la gestione dell'elenco nella descrizione comando. È necessaria solo la collaborazione del parser per fornire i dati visualizzati nell'elenco.

I servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio è usare le estensioni MEF. Per altre informazioni, vedere [Estensione dell'editor e di Servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> È consigliabile iniziare a usare la nuova API dell'editor appena possibile. In questo modo si miglioreranno le prestazioni del servizio di linguaggio e si potranno sfruttare le nuove funzionalità dell'editor.

## <a name="how-it-works"></a>Come funziona

Di seguito sono riportati i due modi in cui un elenco di membri viene visualizzato usando le classi MPF:

- Posizionamento del cursore su un identificatore o dopo un carattere di completamento dei membri e selezione **di Elenca** membri dal menu **IntelliSense.**

- Lo <xref:Microsoft.VisualStudio.Package.IScanner> scanner rileva un carattere di completamento membro e imposta un trigger token di [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) per tale carattere.

Un carattere di completamento del membro indica che deve essere seguito un membro di una classe, una struttura o un'enumerazione. Ad esempio, in C# o Visual Basic il carattere di completamento del membro è , mentre in C++ il carattere `.` è o `.` `->` . Il valore del trigger viene impostato quando viene analizzato il carattere di selezione del membro.

### <a name="the-intellisense-member-list-command"></a>Comando IntelliSense Member List

Il comando avvia una chiamata al metodo sulla classe e il metodo chiama a sua volta il parser del metodo con il motivo di analisi <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> [ParseReason.DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Il parser determina il contesto della posizione corrente, nonché il token in o immediatamente prima della posizione corrente. In base a questo token, viene presentato un elenco di dichiarazioni. Ad esempio, in C#, se si posiziona il cursore su un membro della classe e si seleziona **Elenca** membri , si ottiene un elenco di tutti i membri della classe. Se si posiziona il cursore dopo un punto che segue una variabile oggetto, si ottiene un elenco di tutti i membri della classe rappresentato dall'oggetto. Si noti che se il cursore è posizionato su un membro quando viene visualizzato l'elenco dei membri, la selezione di un membro nell'elenco sostituisce il membro su cui si trova il cursore con quello nell'elenco.

### <a name="the-token-trigger"></a>Trigger di token

Il trigger [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) avvia una chiamata al metodo sulla classe e il metodo chiama a sua volta il parser con il motivo di analisi <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> <xref:Microsoft.VisualStudio.Package.Source> <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Se il trigger del token include anche il flag [TokenTriggers.MatchBraces,](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) il motivo di analisi è [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), che combina la selezione dei membri e l'evidenziazione delle parentesi graffe.

Il parser determina il contesto della posizione corrente e ciò che è stato digitato prima del carattere di selezione del membro. Da queste informazioni, il parser crea un elenco di tutti i membri dell'ambito richiesto. Questo elenco di dichiarazioni viene archiviato <xref:Microsoft.VisualStudio.Package.AuthoringScope> nell'oggetto restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo . Se vengono restituite dichiarazioni, viene visualizzata la descrizione comando per il completamento dei membri. La descrizione comando è gestita da un'istanza della <xref:Microsoft.VisualStudio.Package.CompletionSet> classe .

## <a name="enable-support-for-member-completion"></a>Abilitare il supporto per il completamento dei membri

Per supportare qualsiasi operazione IntelliSense, è necessario che la voce del Registro di sistema sia impostata su `CodeSense` 1. Questa voce del Registro di sistema può essere impostata con un parametro denominato passato <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> all'attributo utente associato al pacchetto di linguaggio. Le classi del servizio di linguaggio leggono il valore di questa voce del Registro di sistema <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> dalla proprietà nella classe <xref:Microsoft.VisualStudio.Package.LanguagePreferences> .

Se lo scanner restituisce il trigger del token [di TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)e il parser restituisce un elenco di dichiarazioni, viene visualizzato l'elenco di completamento dei membri.

## <a name="support-member-completion-in-the-scanner"></a>Supporto del completamento dei membri nello scanner

Lo scanner deve essere in grado di rilevare un carattere di completamento dei membri e impostare il trigger del token [di TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) quando tale carattere viene analizzato.

### <a name="scanner-example"></a>Esempio di scanner

Di seguito è riportato un esempio semplificato di rilevamento del carattere di completamento del membro e dell'impostazione del <xref:Microsoft.VisualStudio.Package.TokenTriggers> flag appropriato. Questo esempio è solo a scopo illustrativo. Presuppone che lo scanner contenga un metodo che identifica e `GetNextToken` restituisce token da una riga di testo. Il codice di esempio imposta semplicemente il trigger ogni volta che vede il tipo di carattere giusto.

```csharp
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestScanner : IScanner
    {
        private Lexer lex;
        private const char memberSelectChar = '.';

        public bool ScanTokenAndProvideInfoAboutIt(TokenInfo tokenInfo,
                                                   ref int state)
        {
            bool foundToken = false
            string token = lex.GetNextToken();
            if (token != null)
            {
                foundToken = true;
                char c = token[0];
                if (c == memberSelectChar)
                {
                        tokenInfo.Trigger |= TokenTriggers.MemberSelect;
                }
            }
            return foundToken;
        }
    }
}
```

## <a name="support-member-completion-in-the-parser"></a>Supporto del completamento dei membri nel parser

Per il completamento dei membri, <xref:Microsoft.VisualStudio.Package.Source> la classe chiama il metodo <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> . È necessario implementare l'elenco in una classe derivata dalla <xref:Microsoft.VisualStudio.Package.Declarations> classe . Per informazioni <xref:Microsoft.VisualStudio.Package.Declarations> dettagliate sui metodi che è necessario implementare, vedere la classe .

Il parser viene chiamato con [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) o [ParseReason.MemberSelectAndHighlightBraces quando](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) viene digitato un carattere di selezione del membro. La posizione specificata <xref:Microsoft.VisualStudio.Package.ParseRequest> nell'oggetto è immediatamente dopo il carattere di selezione del membro. Il parser deve raccogliere i nomi di tutti i membri che possono essere visualizzati in un elenco di membri in un determinato punto del codice sorgente. Il parser deve quindi analizzare la riga corrente per determinare l'ambito che l'utente vuole associare al carattere di selezione del membro.

Questo ambito è basato sul tipo dell'identificatore prima del carattere di selezione del membro. In C#, ad esempio, data la variabile membro con tipo , digitare `languageService` `LanguageService` **languageService.** genera un elenco di tutti i membri della `LanguageService` classe . Anche in C# digitare **questo valore.** genera un elenco di tutti i membri della classe nell'ambito corrente.

### <a name="parser-example"></a>Esempio di parser

L'esempio seguente illustra un modo per popolare un <xref:Microsoft.VisualStudio.Package.Declarations> elenco. Questo codice presuppone che il parser costruisca una dichiarazione e la aggiunge all'elenco chiamando `AddDeclaration` un metodo sulla classe `TestAuthoringScope` .

```csharp
using System.Collections;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    internal class TestDeclaration
    {
        public string Name;            // Name of declaration
        public int     TypeImageIndex; // Glyph index
        public string Description;     // Description of declaration

        public TestDeclaration(string name, int typeImageIndex, string description)
        {
            this.Name = name;
            this.TypeImageIndex = typeImageIndex;
            this.Description = description;
        }
    }

    //===================================================
    internal class TestDeclarations : Declarations
    {
        private ArrayList declarations;

        public TestDeclarations()
            : base()
        {
            declarations = new ArrayList();
        }

        public void AddDeclaration(TestDeclaration declaration)
        {
            declarations.Add(declaration);
        }

        //////////////////////////////////////////////////////////////////////
        // Declarations of class methods that must be implemented.
        public override int GetCount()
        {
            // Return the number of declarations to show.
            return declarations.Count;
        }

        public override string GetDescription(int index)
        {
            // Return the description of the specified item.
            string description = "";
            if (index >= 0 && index < declarations.Count)
            {
                description = ((TestDeclaration)declarations[index]).Description;
            }
            return description;
        }

        public override string GetDisplayText(int index)
        {
            // Determine what is displayed in the tool tip list.
            string text = null;
            if (index >= 0 && index < declarations.Count)
            {
                text = ((TestDeclaration)declarations[index]).Name;
            }
            return text;
        }

        public override int GetGlyph(int index)
        {
            // Return index of image to display next to the display text.
            int imageIndex = -1;
            if (index >= 0 && index < declarations.Count)
            {
                imageIndex = ((TestDeclaration)declarations[index]).TypeImageIndex;
            }
            return imageIndex;
        }

        public override string GetName(int index)
        {
            string name = null;
            if (index >= 0 && index < declarations.Count)
            {
                name = ((TestDeclaration)declarations[index]).Name;
            }
            return name;
        }
    }

    //===================================================
    public class TestAuthoringScope : AuthoringScope
    {
        private TestDeclarations declarationsList;

        public void AddDeclaration(TestDeclaration declaration)
        {
            if (declaration != null)
            {
                if (declarationsList == null)
                {
                    declarationsList = new TestDeclarations();
                }
                declarationsList.AddDeclaration(declaration);
            }
        }

        public override Declarations GetDeclarations(IVsTextView view,
                                                     int line,
                                                     int col,
                                                     TokenInfo info,
                                                     ParseReason reason)
        {
            return declarationsList;
        }

        /////////////////////////////////////////////////
        // Remainder of AuthoringScope methods not shown.
        /////////////////////////////////////////////////
    }

    //===================================================
    class TestLanguageService : LanguageService
    {
        public override AuthoringScope ParseSource(ParseRequest req)
        {
            TestAuthoringScope scope = new TestAuthoringScope();
            if (req.Reason == ParseReason.MemberSelect ||
                req.Reason == ParseReason.MemberSelectAndHighlightBraces)
            {
                // Gather list of declarations based on what the user
                // has typed so far. In this example, this list is an array of
                // MemberDeclaration objects (a helper class you might implement
                // to hold member declarations).
                // How this list is gathered is dependent on the parser
                // and is not shown here.
                MemberDeclarations memberDeclarations;
                memberDeclarations = GetDeclarationsForScope();

                // Now populate the Declarations list in the authoring scope.
                // GetImageIndexBasedOnType() is a helper method you
                // might implement to convert a member type to an index into
                // the image list returned from the language service.
                foreach (MemberDeclaration dec in memberDeclarations)
                {
                    scope.AddDeclaration(new TestDeclaration(
                                             dec.Name,
                                             GetImageIndexBasedOnType(dec.Type),
                                             dec.Description));
                }
            }
            return scope;
        }
    }
}
```
