---
title: Completamento dei membri in un servizio di linguaggio Legacy | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 8f618c9500b79ec5e1ef0db8c2c6b8b130c6c75b
ms.sourcegitcommit: 0bf2aff6abe485e3fe940f5344a62a885ad7f44e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 06/27/2018
ms.locfileid: "37057270"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Completamento dei membri in un servizio di linguaggio legacy

Completamento dei membri di IntelliSense è una descrizione comando che consente di visualizzare un elenco di possibili membri di un determinato ambito, ad esempio una classe, struttura, enumerazione o dello spazio dei nomi. Ad esempio, nel linguaggio c#, se l'utente digita "this" seguito da un punto, un elenco di tutti i membri della classe o struttura nell'ambito corrente viene visualizzato in un elenco da cui l'utente può selezionare.

Il framework di pacchetto gestito (MPF) fornisce supporto per la descrizione comando e la gestione dell'elenco nella descrizione comando; tutto ciò che serve è collaborazione proveniente dal parser per fornire i dati visualizzati nell'elenco.

Servizi di linguaggio legacy vengono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per altre informazioni, vedere [estensione dell'Editor e servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> È consigliabile che si inizia a usare il nuovo editor delle API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.

## <a name="how-it-works"></a>Come funziona

Di seguito sono i due modi in cui viene illustrato un elenco di membri utilizzando le classi MPF:

- Posizionando il cursore su un identificatore o dopo un carattere di completamento del membro e selezionando **Elenca membri** dalle **IntelliSense** menu.

- Il <xref:Microsoft.VisualStudio.Package.IScanner> scanner rileva un carattere di completamento di membro e imposta un trigger di token [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) per tale carattere.

Un carattere di completamento membro indica che un membro di una classe, struttura o enumerazione consiste nel seguire. In c# o Visual Basic, ad esempio, il carattere di completamento membro è un `.`, mentre in C++ il carattere è un `.` o un `->`. Il valore del trigger è impostato quando viene analizzato il carattere di selezione del membro.

### <a name="the-intellisense-member-list-command"></a>Il comando di elenco di membri IntelliSense

Il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando avvia una chiamata al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo sul <xref:Microsoft.VisualStudio.Package.Source> classe e il <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo, a sua volta, chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser di metodo con il motivo di analisi di [ParseReason.DisplayMemberList ](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Il parser determina il contesto della posizione corrente, nonché il token sotto o immediatamente prima della posizione corrente. Basato su questo token, viene presentato un elenco di dichiarazioni. Ad esempio, in c#, se si posiziona il cursore su un membro di classe e selezionare **Elenca membri**, otterrai un elenco di tutti i membri della classe. Se si posiziona il cursore dopo un periodo che segue una variabile oggetto, si ottiene un elenco di tutti i membri della classe di tale oggetto rappresenta. Si noti che se il cursore è posizionato su un membro quando viene visualizzato l'elenco dei membri, se si seleziona un membro dall'elenco sostituisce il membro che si trova il cursore con l'uno nell'elenco.

### <a name="the-token-trigger"></a>Il Trigger di Token

Il [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) trigger avvia una chiamata al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo sul <xref:Microsoft.VisualStudio.Package.Source> classe e il <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo, a sua volta, chiama il parser il motivo per l'analisi di [ ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Se il trigger token incluso anche il [TokenTriggers.MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) flag, il motivo per l'analisi è [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), che combina selezione dei membri e l'evidenziazione delle parentesi graffe .

Il parser determina il contesto dell'oggetto corrente posizionare oltre a ciò che è stata tipizzata prima che il membro selezionare carattere. Da queste informazioni, il parser crea un elenco di tutti i membri dell'ambito richiesto. Questo elenco delle dichiarazioni viene archiviato nel <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> (metodo). Se vengono restituite tutte le dichiarazioni, viene visualizzato il suggerimento dello strumento di completamento membro. La descrizione comando è gestita da un'istanza di <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.

## <a name="enable-support-for-member-completion"></a>Abilita supporto del completamento dei membri

È necessario disporre di `CodeSense` voce del Registro di sistema è impostato su 1 per supportare qualsiasi operazione di IntelliSense. Questa voce del Registro di sistema può essere impostata con un parametro denominato passato al <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo utente associato al pacchetto di linguaggio. Le classi del servizio linguaggio leggere il valore di questa voce del Registro di sistema dal <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà di <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.

Se lo scanner restituisce il trigger del token [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)e il parser restituisce un elenco di dichiarazioni, quindi viene visualizzato l'elenco di completamento del membro.

## <a name="support-member-completion-in-the-scanner"></a>Supporto di completamento dei membri nello Scanner

Lo scanner deve essere in grado di rilevare un carattere di completamento di membro e impostare il trigger di token [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) quando tale carattere viene analizzato.

### <a name="scanner-example"></a>Esempio di analisi

Ecco un esempio semplificato di rilevare il carattere di completamento di membro e l'impostazione appropriata <xref:Microsoft.VisualStudio.Package.TokenTriggers> flag. Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contiene un metodo `GetNextToken` che identifica e restituisce i token da una riga di testo. L'esempio di codice semplicemente imposta il trigger quando viene rilevato il tipo di carattere a destra.

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

## <a name="support-member-completion-in-the-parser"></a>Supporto di completamento dei membri nel Parser

Per il completamento di membro, il <xref:Microsoft.VisualStudio.Package.Source> classe chiama il <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> (metodo). È necessario implementare l'elenco in una classe derivata dal <xref:Microsoft.VisualStudio.Package.Declarations> classe. Vedere il <xref:Microsoft.VisualStudio.Package.Declarations> classe per informazioni dettagliate sui metodi è necessario implementare.

Il parser viene chiamato con [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) oppure [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) quando viene digitato un carattere di selezione del membro. Il percorso specificato <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto è immediatamente dopo il membro selezionato carattere. Il parser deve raccogliere i nomi di tutti i membri che possono essere visualizzati in un elenco di membri in quel particolare nel codice sorgente. Il parser deve quindi analizzare la riga corrente per determinare l'ambito che il consenso dell'utente associato al carattere selezionare membro.

In questo ambito si basa sul tipo di identificatore prima che il membro selezionare carattere. In c#, si consideri ad esempio la variabile membro `languageService` che è di tipo `LanguageService`e digitando **languageService.** produce un elenco di tutti i membri del `LanguageService` classe. Anche in c#, digitare **questo.** produce un elenco di tutti i membri della classe nell'ambito corrente.

### <a name="parser-example"></a>Esempio di parser

L'esempio seguente illustra un modo per popolare un <xref:Microsoft.VisualStudio.Package.Declarations> elenco. Questo codice si presuppone che il parser crea una dichiarazione e lo aggiunge all'elenco chiamando un' `AddDeclaration` metodo di `TestAuthoringScope` classe.

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