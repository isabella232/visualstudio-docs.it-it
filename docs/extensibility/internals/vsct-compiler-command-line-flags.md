---
title: Flag Command-Line del compilatore VSCT | Microsoft Docs
description: Il compilatore della tabella dei comandi di Visual Studio fornisce opzioni della riga di comando per garantire la corretta compilazione dei file con estensione vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 53e50e408166eb2d2e1545549cdd6c72018c9553
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99938785"
---
# <a name="vsct-compiler-command-line-flags"></a>Flag della riga di comando del compilatore VSCT
Il compilatore della tabella dei comandi di Visual Studio (VSCT) fornisce opzioni della riga di comando per garantire la corretta compilazione dei file. vsct.

## <a name="command-line-parameters"></a>Parametri della riga di comando
 Per visualizzare la Guida di base di VSCT da una finestra di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] **comando** , passare alla cartella \VisualStudioIntegration\Tools\Bin\ del *percorso di installazione di Visual Studio SDK* e digitare:

```
vsct /?
```

 Il comando restituisce:

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
|-d|Specificare eventuali simboli definiti aggiuntivi.|
|-I|Indica i percorsi di inclusione aggiuntivi da utilizzare durante la risoluzione dei riferimenti a file.|
|-l|Specificare il <xref:System.Globalization.CultureInfo> nome delle impostazioni cultura, ad esempio "en-US".|
|-E|Crea oggetti C# nello spazio dei nomi specificato per gli elementi Command, seguiti da [C&#124;H&#124;N]:*filename* where C = C#, H = C++ Header, N = Namespace. Lo spazio dei nomi è obbligatorio per C#.|
|-v|Output dettagliato.|

 L'opzione-L indica al compilatore di selezionare un gruppo di stringhe per produrre il file binario con estensione CTO corrispondente al <xref:System.Globalization.CultureInfo> nome delle impostazioni cultura specificato. Il nome delle impostazioni cultura specificato deve corrispondere all'attributo Language di uno o più [elementi Strings](../../extensibility/strings-element.md) nel file con estensione vsct. Se un elemento Strings non ha un attributo Language, viene ereditato dall' [elemento CommandTable](../../extensibility/commandtable-element.md)che lo contiene.

 Un file con estensione vsct può avere più elementi Strings e ognuno di essi può avere un attributo Language diverso. La globalizzazione viene eseguita eseguendo più volte il compilatore VSCT e modificando l'opzione-L per ogni nome di impostazioni cultura.

 Se il nome delle impostazioni cultura specificato dall'opzione-L non corrisponde all'attributo Language di un elemento Strings, il compilatore tenterà di trovare la corrispondenza con la lingua e non con l'area. Se, ad esempio, "en-US" non viene trovato, il compilatore tenterà invece di usare "en". In caso contrario, proverà a usare le impostazioni cultura correnti del sistema operativo. In caso contrario, verrà compilato il primo elemento Strings trovato.

 L'opzione-E può essere usata per creare un file di intestazione di tipo C che contiene i simboli usati dalla tabella dei comandi oppure per creare un file C# che contiene gli oggetti per i simboli di comando.

 Le opzioni-D e-I hanno la sintassi dei flag del preprocessore di Cl.exe C con lo stesso nome. Le definizioni-D con formato X = Y vengono usate per l'espansione di test basati su XML \<Defined> negli `Condition` attributi. -I percorsi di inclusione vengono usati per risolvere \<Include> \<Extern> e i riferimenti a \<Bitmap> file. Per ulteriori informazioni, vedere [vsct XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).

 Il compilatore VSCT può anche decompilare un file binario compilato in precedenza. A tale scopo, specificare un file binario per il \<infile> .   Se il file binario è stato prodotto dal compilatore VSCT, avrà i simboli già incorporati e produrrà l'output con i nomi simbolici in una \<Symbols> sezione dell'output. Se il file binario è stato prodotto dal compilatore CTC, l'output conterrà i GUID e gli ID effettivi. Se il file *. ctsym prodotto dalle versioni correnti di Ctc.exe si trova nella stessa cartella del file di input binario, i simboli verranno caricati da tale file e usati per l'output.

## <a name="see-also"></a>Vedi anche
- [File Visual Studio Command Table (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
