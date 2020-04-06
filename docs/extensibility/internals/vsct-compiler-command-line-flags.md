---
title: Flag della riga di comando del compilatore VSCT Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e4ee29710049453c3163c366eccf96e257b6028d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703962"
---
# <a name="vsct-compiler-command-line-flags"></a>Flag della riga di comando del compilatore VSCT
Il compilatore Visual Studio Command Table (VSCT) fornisce opzioni della riga di comando per garantire la corretta compilazione dei file vsct.

## <a name="command-line-parameters"></a>Parametri della riga di comando
 Per visualizzare la Guida [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] di base di VSCT da una finestra di **comando,** passare alla cartella di installazione di *Visual Studio SDK,* ovvero la cartella e digitare:

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
> I caratteri - (trattino) e / (barra) sono entrambi notazione accettata per indicare i parametri della riga di comando.

 I flag accettabili e il loro significato sono i seguenti.

|Opzione|Descrizione|
|------------|-----------------|
|-d|Specificare eventuali simboli definiti aggiuntivi.|
|-I|Indicare i percorsi di inclusione aggiuntivi da utilizzare per la risoluzione dei riferimenti ai file.|
|-l|Specificare <xref:System.Globalization.CultureInfo> il nome delle impostazioni cultura, ad esempio "en-US".|
|-E|Generare oggetti in C' nello spazio dei nomi specificato per gli elementi di comando, seguito da [C&#124;H&#124;N]:*nomefile*in cui C ' C ' , H , intestazione C , N . Lo spazio dei nomi è obbligatorio per C.|
|-v|Output dettagliato.|

 L'opzione -L indica al compilatore di selezionare un gruppo di stringhe per <xref:System.Globalization.CultureInfo> produrre il file binario con estensione cto che corrisponde al nome delle impostazioni cultura specificato. Il nome delle impostazioni cultura specificato deve corrispondere all'attributo Language di uno o più [elementi Strings](../../extensibility/strings-element.md) nel file vsct. Se un elemento Strings non dispone di alcun attributo Language, viene ereditato [dall'elemento CommandTable](../../extensibility/commandtable-element.md)che lo contiene.

 Un file vsct può avere più Strings elementi e ognuno può avere un attributo Language diverso. La globalizzazione viene ottenuta eseguendo più volte il compilatore VSCT e modificando l'opzione -L per ogni nome di impostazioni cultura.

 Se il nome delle impostazioni cultura specificato dall'opzione -L non corrisponde all'attributo Language di alcun elemento Strings, il compilatore tenterà di trovare una corrispondenza tra la lingua e non l'area. Ad esempio, se non è possibile trovare "en-US", il compilatore tenterà invece "en". In caso contrario, proverà le impostazioni cultura correnti del sistema operativo. In caso contrario, verrà compilato il primo elemento Strings trovato.

 L'opzione -E può essere utilizzata per generare un file di intestazione di tipo C che contiene i simboli utilizzati dalla tabella dei comandi o per generare un file C, che contiene oggetti per i simboli di comando.

 Le opzioni -D e -I hanno la sintassi dei flag del preprocessore Cl.exe che hanno lo stesso nome. Le definizioni -D con il formato X-Y vengono \<utilizzate per `Condition` l'espansione dei test di> definiti basati su XML negli attributi. -I percorsi di \<inclusione \<vengono utilizzati \<per risolvere i riferimenti ai file di> Include, Extern> e Bitmap>. Per ulteriori informazioni, vedere [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).

 Il compilatore VSCT può anche decompilare un file binario compilato in precedenza. A tale scopo, fornire un \<file binario per il file infile>.   Se il file binario è stato prodotto dal compilatore VSCT, avrà i \<simboli già incorporati e produrrà l'output con i nomi simbolici in un Symbols> sezione dell'output. Se il file binario è stato prodotto dal compilatore CTC, l'output conterrà i GUID e gli ID effettivi. Se il file ctsym prodotto dalle versioni correnti di Ctc.exe si trova nella stessa cartella del file di input binario, i simboli verranno caricati da tale file e utilizzati per l'output.

## <a name="see-also"></a>Vedere anche
- [File Visual Studio Command Table (con estensione vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)
- [Riferimenti sullo schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)
- [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
