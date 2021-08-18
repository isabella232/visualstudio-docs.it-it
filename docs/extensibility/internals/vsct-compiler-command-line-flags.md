---
title: Flag Command-Line del compilatore VSCT | Microsoft Docs
description: Il Visual Studio della tabella dei comandi offre opzioni della riga di comando per garantire la corretta compilazione dei file con estensione vsct.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 0ce1e699901f6f4aab0145a41c606d05ea083c04
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122034572"
---
# <a name="vsct-compiler-command-line-flags"></a>Flag della riga di comando del compilatore VSCT
Il Visual Studio della tabella dei comandi di visual studio (VSCT) fornisce opzioni della riga di comando per garantire la corretta compilazione dei file con estensione vsct.

## <a name="command-line-parameters"></a>Parametri della riga di comando
 Per visualizzare la Guida di base di VSCT da una finestra di comando, passare alla cartella di installazione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  *Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ e digitare:

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
> I caratteri - (trattino) e / (barra) sono entrambi notazione accettata per indicare i parametri della riga di comando.

 I flag accettabili e il loro significato sono i seguenti.

|Opzione|Descrizione|
|------------|-----------------|
|-d|Specificare eventuali simboli definiti aggiuntivi.|
|-I|Indicare i percorsi di inclusione aggiuntivi da usare per la risoluzione dei riferimenti ai file.|
|-l|Specificare il <xref:System.Globalization.CultureInfo> nome delle impostazioni cultura, ad esempio "en-US".|
|-E|Creare oggetti C# nello spazio dei nomi specificato per gli elementi di comando, seguiti da [C&#124;H&#124;N]:*filename* dove C = C#, H = intestazione C++, N = spazio dei nomi. Lo spazio dei nomi è obbligatorio per C#.|
|-v|Output dettagliato.|

 L'opzione -L indica al compilatore di selezionare un gruppo di stringhe per produrre il file binario con estensione cto corrispondente al nome delle impostazioni <xref:System.Globalization.CultureInfo> cultura specificato. Il nome delle impostazioni cultura specificato deve corrispondere all'attributo Language di uno o più [elementi Strings](../../extensibility/strings-element.md) nel file con estensione vsct. Se un elemento Strings non ha un attributo Language, viene ereditato dall'elemento [CommandTable che lo contiene.](../../extensibility/commandtable-element.md)

 Un file con estensione vsct può avere più elementi Strings e ognuno può avere un attributo Language diverso. La globalizzazione si ottiene eseguendo più volte il compilatore VSCT e modificando l'opzione -L per ogni nome di impostazioni cultura.

 Se il nome delle impostazioni cultura specificato dall'opzione -L non corrisponde all'attributo Language di alcun elemento Strings, il compilatore tenterà di trovare la corrispondenza con la lingua e non con l'area. Ad esempio, se non è possibile trovare "en-US", il compilatore proverà invece "en". In caso contrario, proverà a utilizzare le impostazioni cultura correnti del sistema operativo. In caso contrario, compilerà il primo elemento Strings trovato.

 L'opzione -E può essere usata per creare un file di intestazione di tipo C che contiene i simboli usati dalla tabella dei comandi o per generare un file C# contenente oggetti per i simboli di comando.

 Le opzioni -D e -I hanno la sintassi Cl.exe flag del preprocessore C con lo stesso nome. Le definizioni -D con formato X=Y vengono usate per l'espansione di test basati su XML \<Defined> negli `Condition` attributi. I percorsi di inclusione vengono usati per risolvere \<Include> i riferimenti ai file , e \<Extern> \<Bitmap> . Per altre informazioni, vedere le informazioni [di riferimento su XML Schema VSCT.](../../extensibility/vsct-xml-schema-reference.md)

 Il compilatore VSCT può anche decompilare un file binario compilato in precedenza. A tale scopo, specificare un file binario per \<infile> .   Se il file binario è stato prodotto dal compilatore VSCT, avrà i simboli già incorporati e genererà l'output con i nomi simbolici in una sezione \<Symbols> dell'output. Se il file binario è stato prodotto dal compilatore CTC, l'output conterrà i GUID e gli ID effettivi. Se il file *.ctsym prodotto dalle versioni correnti di Ctc.exe si trova nella stessa cartella del file di input binario, i simboli verranno caricati da tale file e usati per l'output.

## <a name="see-also"></a>Vedi anche
- [File Visual Studio Command Table (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
