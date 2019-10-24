---
title: Flag della riga di comando del compilatore VSCT | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 71634a007019dd39e843ccc63af1c3188f778ea9
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72722023"
---
# <a name="vsct-compiler-command-line-flags"></a>Flag della riga di comando del compilatore VSCT
Il compilatore della tabella dei comandi di Visual Studio (VSCT) fornisce opzioni della riga di comando per garantire la corretta compilazione dei file. vsct.

## <a name="command-line-parameters"></a>Parametri della riga di comando
 Per visualizzare la Guida di base di VSCT da una finestra di **comando** di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], passare alla cartella \VisualStudioIntegration\Tools\Bin\ del *percorso di installazione di Visual Studio SDK*e digitare:

```
vsct /?
```

 Viene restituito:

```
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000

Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]

  -D    Specify any additional preprocessor defines
  -I    Indicate what additional include paths to send to the preprocessor
  -L    Specify the language to use when selecting strings
  -E    Emit C# objects in the specified namespace for command items,
        followed by [L|F|H|N]:<value>
        F = Name of the file to emit (used if -EL is provided)
        L = Name of a language providing a CodeDOM provider
        N = namespace (required if -EL is provided)
        H = C++ header
  -c    Clean build skipping dependency checks
  -v    Verbose output
```

> [!NOTE]
> I caratteri-(Dash) e/(barra) sono entrambi notazione accettata per indicare i parametri della riga di comando.

 I flag accettabili e le relative implicazioni sono i seguenti.

|Opzione|Descrizione|
|------------|-----------------|
|-D|Specificare eventuali simboli definiti aggiuntivi.|
|-I|Indica i percorsi di inclusione aggiuntivi da utilizzare durante la risoluzione dei riferimenti a file.|
|-L|Specificare il nome delle impostazioni cultura <xref:System.Globalization.CultureInfo>, ad esempio "en-US".|
|-E|Crea C# gli oggetti nello spazio dei nomi specificato per gli elementi del comando,&#124;seguiti da [C H&#124;N]:*filename*dove C = C#, H = C++ header, N = Namespace. Lo spazio dei nomi è C#necessario per.|
|-v|Output dettagliato.|

 L'opzione-L indica al compilatore di selezionare un gruppo di stringhe per produrre il file binary. CTO corrispondente al nome delle impostazioni cultura <xref:System.Globalization.CultureInfo> specificato. Il nome delle impostazioni cultura specificato deve corrispondere all'attributo Language di uno o più [elementi Strings](../../extensibility/strings-element.md) nel file con estensione vsct. Se un elemento Strings non ha un attributo Language, viene ereditato dall' [elemento CommandTable](../../extensibility/commandtable-element.md)che lo contiene.

 Un file con estensione vsct può avere più elementi Strings e ognuno di essi può avere un attributo Language diverso. La globalizzazione viene eseguita eseguendo più volte il compilatore VSCT e modificando l'opzione-L per ogni nome di impostazioni cultura.

 Se il nome delle impostazioni cultura specificato dall'opzione-L non corrisponde all'attributo Language di un elemento Strings, il compilatore tenterà di trovare la corrispondenza con la lingua e non con l'area. Se, ad esempio, "en-US" non viene trovato, il compilatore tenterà invece di usare "en". In caso contrario, proverà a usare le impostazioni cultura correnti del sistema operativo. In caso contrario, verrà compilato il primo elemento Strings trovato.

 È possibile utilizzare l'opzione-E per creare un file di intestazione C contenente i simboli utilizzati dalla tabella dei comandi oppure per creare un C# file contenente gli oggetti per i simboli dei comandi.

 Le opzioni-D e-I hanno la sintassi dei flag del preprocessore cl. exe C con lo stesso nome. Le definizioni-D con formato X = Y vengono usate per l'espansione di \<Defined basati su XML > i test negli attributi di `Condition`. -I percorsi di inclusione vengono usati per risolvere \<Include >, \<Extern > e \<Bitmap riferimenti a file >. Per ulteriori informazioni, vedere [vsct XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).

 Il compilatore VSCT può anche decompilare un file binario compilato in precedenza. A tale scopo, specificare un file binario per la > di \<infile.   Se il file binario è stato prodotto dal compilatore VSCT, avrà i simboli già incorporati e produrrà l'output con i nomi simbolici in una \<Symbols > sezione dell'output. Se il file binario è stato prodotto dal compilatore CTC, l'output conterrà i GUID e gli ID effettivi. Se il file *. ctsym prodotto dalle versioni correnti di CTC. exe si trova nella stessa cartella del file di input binario, i simboli verranno caricati da tale file e usati per l'output.

## <a name="see-also"></a>Vedere anche
- [File Visual Studio Command Table (VSCT)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)