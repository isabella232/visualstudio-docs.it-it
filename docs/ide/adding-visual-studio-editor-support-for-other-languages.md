---
title: Aggiungere il supporto di altri linguaggi nell'editor
description: Informazioni su come l'editor Visual Studio supporta la lettura e lo spostamento tra diversi linguaggi di computer e su come è possibile aggiungere il supporto per altri linguaggi.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- syntax colorization
- IntelliSense
- IDE, navigation
- documents [Visual Studio], navigation
- TextMate bundle
- TextMate language grammar
- language support
ms.assetid: d78c43ee-4ef2-42e5-984e-d137de4e7e92
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 4933868248da896766d95875dc8e78b2eb56b1052456e55ca086a554cd7296cb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121358448"
---
# <a name="add-visual-studio-editor-support-for-other-languages"></a>Aggiungere il supporto di altri linguaggi all'editor di Visual Studio

Informazioni su come l'editor di Visual Studio supporti la lettura e il passaggio da un linguaggio di programmazione a un altro e su come aggiungere il supporto per altri linguaggi all'editor di Visual Studio.

## <a name="syntax-colorization-statement-completion-and-navigate-to-support"></a>Supporto della colorazione della sintassi, del completamento istruzioni e di Navigate To (Passa a)

Alcune funzionalità dell'editor di Visual Studio, ad esempio la colorazione della sintassi, il completamento istruzioni (chiamato anche IntelliSense) e _Passa a_ consentono una maggiore facilità di scrittura, lettura e modifica del codice. Lo screenshot seguente mostra un esempio di modifica di uno script Perl in Visual Studio. La sintassi viene colorata automaticamente. Ad esempio, i commenti nel codice sono di colore verde, il codice è nero, i percorsi sono rossi e le istruzioni sono blu. L'editor di Visual Studio applica automaticamente la colorazione della sintassi per qualsiasi linguaggio supportato. Oltre a questo, quando si inizia a immettere una parola chiave o un oggetto noto del linguaggio, la funzionalità di completamento istruzioni visualizza l'elenco delle istruzioni e degli oggetti possibili. Il completamento istruzioni consente di scrivere codice in modo più rapido e facile.

![Colorazione della sintassi in uno script Perl](../ide/media/vside_perledit.png)

Attualmente Visual Studio supporta le funzioni di colorazione della sintassi e di completamento istruzioni per i linguaggi riportati di seguito tramite le [grammatiche TextMate](https://manual.macromates.com/en/language_grammars). Se nella tabella non è presente il linguaggio preferito, tuttavia, non è il caso di preoccuparsi perché è possibile aggiungerlo.


- Bat
- F#
- Java
- Markdown
- Rust
- Visual Basic
- Clojure
- Go
- JavaDoc
- Objective-C
- ShaderLab
- C#
- CMake
- Groovy
- JSON
- Perl
- ShellScript
- Visual C++
- CoffeeScript
- HTML
- LESS
- Python
- SQL
- VBNet
- CSS
- INI
- LUA
- R
- Swift
- XML
- Docker
- Jade
- Casa automobilistica
- Ruby
- TypeScript
- YAML

Oltre alla colorazione della sintassi e al completamento delle istruzioni di base, Visual Studio ha una funzionalità detta [Navigate To](/archive/blogs/benwilli/visual-studio-tip-3-use-navigate-to) (Passa a). Questa funzionalità consente di cercare rapidamente file di codice, percorsi dei file e simboli di codice. Visual Studio supporta la funzione Navigate To (Passa a) per i linguaggi seguenti.

- C#

- C++

- TypeScript

- JavaScript

- Visual Basic

- Go

- Java

- PHP

Per tutti questi tipi di file sono disponibili le funzionalità descritte in precedenza anche se il supporto di un linguaggio specifico non è stato ancora installato. L'installazione di supporto specializzato per alcuni linguaggi può offrire il supporto di linguaggi aggiuntivi, ad esempio IntelliSense, o di altre funzionalità avanzate di un linguaggio, ad esempio le lampadine.

## <a name="add-support-for-non-supported-languages"></a>Aggiungere il supporto per linguaggi non supportati

Visual Studio offre il supporto dei linguaggi nell'editor tramite le [grammatiche TextMate](https://manual.macromates.com/en/language_grammars). Se il linguaggio di programmazione preferito non è attualmente supportato nell'editor di Visual Studio, prima di tutto eseguire una ricerca sul Web. Un bundle TextMate per questo linguaggio potrebbe già essere disponibile. Se non si riesce a trovare il bundle, tuttavia, è possibile aggiungere il supporto del linguaggio autonomamente creando un modello di bundle TextMate per la grammatica e i frammenti del linguaggio.

Aggiungere le nuove grammatiche TextMate per Visual Studio nella cartella seguente:

*%userprofile% \\ .vs\Extensions*

In questo percorso di base aggiungere le cartelle seguenti, se applicabili alla situazione specifica:

|Nome cartella|Descrizione|
|-----------------|-----------------|
|\\*\<language name>*|Cartella del linguaggio. Sostituire *\<language name>* con il nome della lingua. ad esempio, *\Matlab*.|
|*\Syntaxes*|Cartella della grammatica. Contiene i file *json di grammatica* per il linguaggio, ad esempioMatlab.js *in*.|
|*\Snippets*|Cartella dei frammenti. Contiene frammenti di codice per il linguaggio.|

In Windows% *userprofile%* si risolve nel percorso: *\\ \<user name> c:\Users*. Se nel sistema non esiste la cartella *Extensions*, sarà necessario crearla. Se la cartella esiste già, verrà nascosta.

> [!TIP]
> Se ci sono file aperti nell'editor, sarà necessario chiuderli e riaprirli per vedere l'evidenziazione della sintassi dopo aver aggiunto le grammatiche TextMate.

Per informazioni dettagliate su come creare grammatiche TextMate, vedere [TextMate - Introduction to Language Grammars](https://developmentality.wordpress.com/2011/02/08/textmate-introduction-to-language-grammars/) (TextMate: introduzione alle grammatiche dei linguaggi) e [Notes on how to create a Language Grammar and Custom Theme for a Textmate Bundle](https://benparizek.com/notebook/notes-on-how-to-create-a-language-grammar-and-custom-theme-for-a-textmate-bundle) (Note sulla creazione della grammatica di un linguaggio e di un tema personalizzato per un bundle TextMate).

## <a name="see-also"></a>Vedi anche

- [Aggiungere un'estensione del protocollo di server di linguaggio](../extensibility/adding-an-lsp-extension.md)
- [Procedura dettagliata: Creare un frammento di codice](../ide/walkthrough-creating-a-code-snippet.md)
- [Procedura dettagliata: Visualizzare il completamento istruzioni](../extensibility/walkthrough-displaying-statement-completion.md)
- [Codice di esempio: Grammatica TextMate](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/TextmateGrammar)
- [Codice di esempio: supporto della lingua personalizzata](https://github.com/microsoft/VSSDK-Extensibility-Samples/tree/master/Ook_Language_Integration)