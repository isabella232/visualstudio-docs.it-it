---
title: Flag Command-Line del compilatore VSCT | Microsoft Docs
description: Il compilatore Visual Studio command table fornisce opzioni della riga di comando per garantire la corretta compilazione dei file con estensione vsct.
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
ms.openlocfilehash: de48995abe6547b9f73c27a3c749609e8f99cfd8c8f17aa74f5200106238d205
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121375440"
---
# <a name="vsct-compiler-command-line-flags"></a>Flag della riga di comando del compilatore VSCT
Il compilatore Visual Studio command table (VSCT) fornisce opzioni della riga di comando per garantire la corretta compilazione dei file con estensione vsct.

## <a name="command-line-parameters"></a>Parametri della riga di comando
 Per visualizzare la Guida vsct di base da una finestra di comando, passare alla cartella [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]  *Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ e digitare:

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

 I flag accettabili e il significato sono i seguenti.

|Opzione|Descrizione|
|------------|-----------------|
|-d|Specificare eventuali simboli definiti aggiuntivi.|
|-I|Indicare i percorsi di inclusione aggiuntivi da usare per la risoluzione dei riferimenti ai file.|
|-l|Specificare il <xref:System.Globalization.CultureInfo> nome delle impostazioni cultura, ad esempio "en-US".|
|-E|Creare oggetti C# nello spazio dei nomi specificato per gli elementi di comando, seguiti da [C&#124;H&#124;N]:*filename* dove C = C#, H = intestazione C++, N = spazio dei nomi. Lo spazio dei nomi è obbligatorio per C#.|
|-v|Output dettagliato.|

 L'opzione -L indica al compilatore di selezionare un gruppo di stringhe per produrre il file binario CTO corrispondente al nome <xref:System.Globalization.CultureInfo> delle impostazioni cultura specificato. Il nome delle impostazioni cultura specificato deve corrispondere all'attributo Language di uno o più [elementi Strings](../../extensibility/strings-element.md) nel file con estensione vsct. Se un elemento Strings non ha alcun attributo Language, viene ereditato dall'elemento [CommandTable contenitore.](../../extensibility/commandtable-element.md)

 Un file con estensione vsct può avere più elementi Strings e ognuno può avere un attributo Language diverso. La globalizzazione si ottiene eseguendo più volte il compilatore VSCT e modificando l'opzione -L per ogni nome delle impostazioni cultura.

 Se il nome delle impostazioni cultura specificato dall'opzione -L non corrisponde all'attributo Language di alcun elemento Strings, il compilatore tenterà di trovare la corrispondenza con la lingua e non con l'area. Ad esempio, se non è possibile trovare "en-US", il compilatore proverà invece "en". In caso contrario, proverà le impostazioni cultura correnti del sistema operativo. In caso contrario, compilerà il primo elemento Strings trovato.

 L'opzione -E può essere usata per generare un file di intestazione di tipo C contenente i simboli usati dalla tabella dei comandi o per generare un file C# contenente oggetti per i simboli di comando.

 Le opzioni -D e -I hanno la sintassi dei flag Cl.exe del preprocessore C con lo stesso nome. Le definizioni -D con il formato X=Y vengono usate per l'espansione dei test basati su XML \<Defined> negli `Condition` attributi. -I percorsi di inclusione vengono usati per risolvere \<Include> i riferimenti ai file e \<Extern> \<Bitmap> . Per altre informazioni, vedere Informazioni di [riferimento su VSCT XML Schema.](../../extensibility/vsct-xml-schema-reference.md)

 Il compilatore VSCT può anche decompilare un file binario compilato in precedenza. A tale scopo, specificare un file binario per \<infile> .   Se il file binario è stato prodotto dal compilatore VSCT, avrà i simboli già incorporati e produrrà l'output con i nomi simbolici in una sezione \<Symbols> dell'output. Se il file binario è stato prodotto dal compilatore CTC, l'output conterrà i GUID e gli ID effettivi. Se il file *.ctsym prodotto dalle versioni correnti di Ctc.exe si trova nella stessa cartella del file di input binario, i simboli verranno caricati da tale file e usati per l'output.

## <a name="see-also"></a>Vedi anche
- [File Visual Studio Command Table (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
