---
title: Completamento del membro in un servizio di linguaggio legacy | Microsoft Docs
description: Informazioni sul funzionamento della descrizione comando per il completamento dei membri di IntelliSense in un servizio di linguaggio legacy e sul modo in cui è supportata dal framework di pacchetto gestito (MPF).
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- IntelliSense, Member Completion tool tip
- Member Completion, supporting in language services [managed package framework]
- language services [managed package framework], IntelliSense Member Completion
ms.assetid: 500f718d-9028-49a4-8615-ba95cf47fc52
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 4fbf88dab2f1ffad0b4a6e5dc6b2ad516c28afca
ms.sourcegitcommit: a436ba564717b992eb1984b28ea0aec801eacaec
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/14/2021
ms.locfileid: "98205801"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Completamento dei membri in un servizio di linguaggio legacy

Il completamento del membro IntelliSense è una descrizione comando che visualizza un elenco di membri possibili di un determinato ambito, ad esempio una classe, una struttura, un'enumerazione o uno spazio dei nomi. Ad esempio, in C#, se l'utente digita "This" seguito da un punto, un elenco di tutti i membri della classe o della struttura nell'ambito corrente viene visualizzato in un elenco da cui l'utente può selezionare.

Il Framework di pacchetto gestito (MPF) fornisce il supporto per la descrizione comando e la gestione dell'elenco nella descrizione comando; è sufficiente collaborare dal parser per fornire i dati visualizzati nell'elenco.

I servizi di linguaggio legacy sono implementati come parte di un pacchetto VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'usare le estensioni MEF. Per ulteriori informazioni, vedere [estensione dei servizi di editor e di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).

> [!NOTE]
> Si consiglia di iniziare a usare la nuova API editor appena possibile. Ciò consente di migliorare le prestazioni del servizio di linguaggio e di sfruttare i vantaggi delle nuove funzionalità dell'editor.

## <a name="how-it-works"></a>Come funziona

Di seguito sono illustrati i due modi in cui viene visualizzato un elenco di membri con le classi MPF:

- Posizionare il cursore su un identificatore o dopo un carattere di completamento del membro e selezionare **Elenca membri** dal menu di **IntelliSense** .

- Lo <xref:Microsoft.VisualStudio.Package.IScanner> scanner rileva un carattere di completamento del membro e imposta un trigger di token di [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) per tale carattere.

Un carattere di completamento del membro indica che è necessario seguire un membro di una classe, una struttura o un'enumerazione. Ad esempio, in C# o Visual Basic il carattere di completamento del membro è `.` , mentre in C++ il carattere è `.` o `->` . Il valore del trigger viene impostato quando viene eseguita l'analisi del carattere Select del membro.

### <a name="the-intellisense-member-list-command"></a>Comando elenco membri IntelliSense

Il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando avvia una chiamata al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Metodo sulla <xref:Microsoft.VisualStudio.Package.Source> classe e il <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo, a sua volta, chiama il parser del <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo con il motivo dell'analisi di [ParseReason. DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Il parser determina il contesto della posizione corrente, nonché il token sotto o immediatamente prima della posizione corrente. In base a questo token, viene visualizzato un elenco di dichiarazioni. Ad esempio, in C#, se si posiziona il cursore su un membro della classe e si seleziona **Elenca membri**, si ottiene un elenco di tutti i membri della classe. Se si posiziona il cursore dopo un periodo che segue una variabile oggetto, si ottiene un elenco di tutti i membri della classe rappresentata dall'oggetto. Si noti che se il punto di inserimento è posizionato in corrispondenza di un membro quando viene visualizzato l'elenco dei membri, la selezione di un membro dall'elenco sostituisce il membro in cui si trova il cursore con quello dell'elenco.

### <a name="the-token-trigger"></a>Trigger del token

Il trigger [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) avvia una chiamata al <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> Metodo sulla <xref:Microsoft.VisualStudio.Package.Source> classe e il <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo, a sua volta, chiama il parser con il motivo dell'analisi di [ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Se il trigger del token include anche il flag [TokenTriggers. MatchBraces](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) , il motivo dell'analisi è [ParseReason. MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), che combina la selezione dei membri e l'evidenziazione delle parentesi graffe.

Il parser determina il contesto della posizione corrente, nonché quello che è stato digitato prima del carattere Select del membro. Da queste informazioni, il parser crea un elenco di tutti i membri dell'ambito richiesto. Questo elenco di dichiarazioni viene archiviato nell' <xref:Microsoft.VisualStudio.Package.AuthoringScope> oggetto restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo. Se vengono restituite dichiarazioni, viene visualizzata la descrizione comando per il completamento dei membri. La descrizione comando viene gestita da un'istanza della <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.

## <a name="enable-support-for-member-completion"></a>Abilita supporto per il completamento del membro

`CodeSense`Per supportare qualsiasi operazione di IntelliSense, è necessario che la voce del registro di sistema sia impostata su 1. Questa voce del registro di sistema può essere impostata con un parametro denominato passato all' <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo utente associato al pacchetto di linguaggio. Le classi del servizio di linguaggio leggono il valore di questa voce del registro di sistema dalla <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà della <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.

Se lo scanner restituisce il trigger del token di [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)e il parser restituisce un elenco di dichiarazioni, viene visualizzato l'elenco di completamento dei membri.

## <a name="support-member-completion-in-the-scanner"></a>Supporto del completamento dei membri nello scanner

Lo scanner deve essere in grado di rilevare un carattere di completamento del membro e impostare il trigger del token di [TokenTriggers. MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) quando il carattere viene analizzato.

### <a name="scanner-example"></a>Esempio di scanner

Di seguito è riportato un esempio semplificato di rilevamento del carattere di completamento del membro e dell'impostazione del <xref:Microsoft.VisualStudio.Package.TokenTriggers> flag appropriato. Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner contenga un metodo `GetNextToken` che identifica e restituisce token da una riga di testo. Il codice di esempio imposta semplicemente il trigger ogni volta che viene visualizzato il tipo di carattere corretto.

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

Per il completamento del membro, la <xref:Microsoft.VisualStudio.Package.Source> classe chiama il <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodo. È necessario implementare l'elenco in una classe derivata dalla <xref:Microsoft.VisualStudio.Package.Declarations> classe. <xref:Microsoft.VisualStudio.Package.Declarations>Per informazioni dettagliate sui metodi che è necessario implementare, vedere la classe.

Il parser viene chiamato con [ParseReason. MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) o [ParseReason. MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) quando viene digitato il carattere di selezione di un membro. Il percorso specificato nell' <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto si trova immediatamente dopo il carattere Select del membro. Il parser deve raccogliere i nomi di tutti i membri che possono essere visualizzati in un elenco di membri in quel particolare punto del codice sorgente. Il parser deve quindi analizzare la riga corrente per determinare l'ambito che l'utente desidera associare al carattere Select del membro.

Questo ambito è basato sul tipo dell'identificatore prima del carattere di selezione del membro. Ad esempio, in C#, data la variabile membro di `languageService` tipo `LanguageService` , digitando **LanguageService.** produce un elenco di tutti i membri della `LanguageService` classe. Anche in C#, digitando **questo.** produce un elenco di tutti i membri della classe nell'ambito corrente.

### <a name="parser-example"></a>Esempio di parser

Nell'esempio seguente viene illustrato un modo per popolare un <xref:Microsoft.VisualStudio.Package.Declarations> elenco. Questo codice presuppone che il parser costruisca una dichiarazione e la aggiunga all'elenco chiamando un `AddDeclaration` Metodo sulla `TestAuthoringScope` classe.

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
