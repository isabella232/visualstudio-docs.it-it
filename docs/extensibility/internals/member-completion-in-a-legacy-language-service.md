---
title: Completamento dei membri in un servizio di linguaggio Legacy . Documenti Microsoft
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
ms.openlocfilehash: b6445aec4954590e4d361189f053592eebe7767e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80707189"
---
# <a name="member-completion-in-a-legacy-language-service"></a>Completamento dei membri in un servizio di linguaggio legacy

Il completamento dei membri IntelliSense è una descrizione comando che visualizza un elenco di possibili membri di un ambito specifico, ad esempio una classe, una struttura, un'enumerazione o uno spazio dei nomi. Ad esempio, se l'utente digita "this" seguito da un punto, un elenco di tutti i membri della classe o della struttura nell'ambito corrente viene presentato in un elenco da cui l'utente può selezionare.

Il framework del pacchetto gestito (MPF) fornisce il supporto per la descrizione comandi e la gestione dell'elenco nella descrizione comandi; tutto ciò che serve è la cooperazione dal parser per fornire i dati che appaiono nell'elenco.

Servizi di linguaggio legacy vengono implementati come parte di un VSPackage, ma il modo più recente per implementare le funzionalità del servizio di linguaggio consiste nell'utilizzare le estensioni MEF. Per ulteriori informazioni, vedere [Estensione dell'editor e](../../extensibility/extending-the-editor-and-language-services.md)dei servizi di linguaggio .

> [!NOTE]
> Si consiglia di iniziare a utilizzare la nuova API dell'editor il prima possibile. Ciò migliorerà le prestazioni del servizio di linguaggio e consentirà di sfruttare le nuove funzionalità dell'editor.

## <a name="how-it-works"></a>Come funziona

Di seguito sono riportati i due modi in cui un elenco di membri viene visualizzato utilizzando le classi MPF:

- Posizionare il punto di inserimento su un identificatore o dopo un carattere di completamento del membro e selezionare **Elenca membri** dal menu **IntelliSense.**

- Lo <xref:Microsoft.VisualStudio.Package.IScanner> scanner rileva un carattere di completamento del membro e imposta un trigger di token [di TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) per tale carattere.

Un carattere di completamento del membro indica che deve seguire un membro di una classe, una struttura o un'enumerazione. Ad esempio, in Visual Basic o in `.`Visual Basic il carattere di `.` completamento `->`del membro è un , mentre in C, il carattere è a o . Il valore del trigger viene impostato quando il membro seleziona il carattere viene analizzato.

### <a name="the-intellisense-member-list-command"></a>Comando Elenco membri IntelliSense

Il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando avvia una <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> chiamata al <xref:Microsoft.VisualStudio.Package.Source> metodo <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> sulla classe e il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo, a sua volta, chiama il parser del metodo con il motivo di analisi [ParseReason.DisplayMemberList](<xref:Microsoft.VisualStudio.Package.ParseReason.DisplayMemberList>).

Il parser determina il contesto della posizione corrente e il token sotto o immediatamente prima della posizione corrente. Sulla base di questo token, viene presentato un elenco di dichiarazioni. Se, ad esempio, si posiziona il livello di inserimento su un membro di classe e si seleziona **Elenca membri**, viene visualizzato un elenco di tutti i membri della classe. Se si posiziona il punto di inserimento dopo un punto che segue una variabile oggetto, si ottiene un elenco di tutti i membri della classe che rappresenta l'oggetto. Si noti che se il cuore di inserimento è posizionato su un membro quando viene visualizzato l'elenco dei membri, la selezione di un membro dall'elenco sostituisce il membro su cui si trova il caret con quello nell'elenco.

### <a name="the-token-trigger"></a>Il trigger di tokenThe Token Trigger

Il trigger [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) avvia una <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> chiamata <xref:Microsoft.VisualStudio.Package.Source> al metodo <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> sulla classe e il metodo, a sua volta, chiama il parser con il motivo di analisi [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>). Se il trigger di token include anche il flag [TokenTriggers.MatchBraces,](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MatchBraces>) il motivo di analisi è [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>), che combina la selezione dei membri e l'evidenziazione delle parentesi graffe.

Il parser determina il contesto della posizione corrente e ciò che è stato digitato prima del carattere di selezione del membro. Da queste informazioni, il parser crea un elenco di tutti i membri dell'ambito richiesto. Questo elenco di dichiarazioni <xref:Microsoft.VisualStudio.Package.AuthoringScope> viene archiviato nell'oggetto restituito dal <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo. Se vengono restituite dichiarazioni, viene visualizzata la descrizione comandi di completamento del membro. La descrizione comandi è gestita <xref:Microsoft.VisualStudio.Package.CompletionSet> da un'istanza della classe.

## <a name="enable-support-for-member-completion"></a>Abilitare il supporto per il completamento dei membriEnable Support for Member Completion

È necessario `CodeSense` disporre della voce del Registro di sistema impostata su 1 per supportare qualsiasi operazione IntelliSense.You must have the registry entry set to 1 to support any IntelliSense operation. Questa voce del Registro di sistema <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> può essere impostata con un parametro denominato passato all'attributo utente associato al pacchetto di lingua. Le classi del servizio di linguaggio <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> leggono <xref:Microsoft.VisualStudio.Package.LanguagePreferences> il valore di questa voce del Registro di sistema dalla proprietà nella classe.

Se lo scanner restituisce il trigger di token [di TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>)e il parser restituisce un elenco di dichiarazioni, viene visualizzato l'elenco di completamento dei membri.

## <a name="support-member-completion-in-the-scanner"></a>Completamento dei membri di supporto nello scanner

Lo scanner deve essere in grado di rilevare un carattere di completamento del membro e impostare il trigger di token di [TokenTriggers.MemberSelect](<xref:Microsoft.VisualStudio.Package.TokenTriggers.MemberSelect>) quando tale carattere viene analizzato.

### <a name="scanner-example"></a>Esempio di scanner

Ecco un esempio semplificato di rilevamento del <xref:Microsoft.VisualStudio.Package.TokenTriggers> carattere di completamento del membro e l'impostazione del flag appropriato. Questo esempio è solo a scopo illustrativo. Si presuppone che lo scanner `GetNextToken` contenga un metodo che identifica e restituisce i token da una riga di testo. Il codice di esempio imposta semplicemente il trigger ogni volta che viene visualizzato il tipo di carattere corretto.

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

## <a name="support-member-completion-in-the-parser"></a>Completamento dei membri di supporto nel parserSupport Member Completion in the Parser

Per il completamento del membro, la <xref:Microsoft.VisualStudio.Package.Source> classe chiama il <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodo . È necessario implementare l'elenco in <xref:Microsoft.VisualStudio.Package.Declarations> una classe derivata dalla classe . Vedere <xref:Microsoft.VisualStudio.Package.Declarations> la classe per informazioni dettagliate sui metodi che è necessario implementare.

Il parser viene chiamato con [ParseReason.MemberSelect](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelect>) o [ParseReason.MemberSelectAndHighlightBraces](<xref:Microsoft.VisualStudio.Package.ParseReason.MemberSelectAndHighlightBraces>) quando viene digitato un carattere di selezione del membro. La posizione specificata <xref:Microsoft.VisualStudio.Package.ParseRequest> nell'oggetto è immediatamente dopo il carattere di selezione del membro. Il parser deve raccogliere i nomi di tutti i membri che possono essere visualizzati in un elenco di membri in quel particolare punto del codice sorgente. Il parser deve quindi analizzare la riga corrente per determinare l'ambito che l'utente desidera associato al carattere di selezione del membro.

Questo ambito è basato sul tipo di identificatore prima del carattere di selezione del membro. Ad esempio, in C, data `languageService` la variabile `LanguageService`membro che dispone di un tipo di , digitare **languageService.** produce un elenco di tutti `LanguageService` i membri della classe. Anche in C , digitando **questo.** produce un elenco di tutti i membri della classe nell'ambito corrente.

### <a name="parser-example"></a>Esempio del parser

Nell'esempio seguente viene illustrato <xref:Microsoft.VisualStudio.Package.Declarations> un modo per popolare un elenco. Questo codice presuppone che il parser costruisca una dichiarazione `AddDeclaration` e `TestAuthoringScope` la aggiunga all'elenco chiamando un metodo sulla classe.

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
