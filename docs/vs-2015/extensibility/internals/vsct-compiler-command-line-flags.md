---
title: Flag della riga di comando del compilatore VSCT | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- VSCT files, compiling
- command-table file compilation (VSCT files)
ms.assetid: 9dc6c33f-e6cf-4cf2-9b05-e8f7bfac1cfb
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 19ebf1713c2a0d42b1269befa3bea28d4dc0309b
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529269"
---
# <a name="vsct-compiler-command-line-flags"></a>Flag della riga di comando del compilatore VSCT
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [flag della riga di comando del compilatore VSCT](https://docs.microsoft.com/visualstudio/extensibility/internals/vsct-compiler-command-line-flags).  
  
Il compilatore di Visual Studio comando tabella (VSCT) offre opzioni della riga di comando per garantire una corretta compilazione del file con estensione vsct.  
  
## <a name="command-line-parameters"></a>Parametri della riga di comando  
 Per visualizzare informazioni di base VSCT da un [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] **comandi** finestra, passare al *percorso di installazione di Visual Studio SDK*\VisualStudioIntegration\Tools\Bin\ cartella e digitare:  
  
```  
vsct /?  
```  
  
 Viene restituito:  
  
```  
Microsoft (R) Visual Studio (R) Command Table Compiler Version 3.00.2000  
  
Syntax: vsct <infile> [<outfile>] [-S[symbols file]] [-D<preprocessor-define>]*  
[-I<include-path>]* [-L<language>] [-E[C|H|N]:<name>]  
  
  -D    Specify any additional preprocessor defines  
  -I    Indcate what additional include paths to send to the preprocessor  
  -L    Specify the langauge to use when selecting strings  
  -E    Emit C# objects in the specified namespace for command items,  
        folowed by [L|F|H|N]:<value>  
        F = Name of the file to emit (used if -EL is provided)  
        L = Name of a language providing a CodeDOM provider  
        N = namespace (required if -EL is provided)  
        H = C++ header  
  -c    Clean build skipping dependancy checks  
  -v    Verbose output  
```  
  
> [!NOTE]
>  I caratteri - (trattino) e / (barra) vengono entrambi notazione accettati per indicare i parametri della riga di comando.  
  
 Di seguito sono riportati i flag accettabile e relativo significato.  
  
|Opzione|Descrizione|  
|------------|-----------------|  
|-D|Specificare eventuali altri simboli definiti.|  
|-SARÒ|Indicare che percorsi da utilizzare durante la risoluzione di riferimenti a file di inclusione aggiuntive.|  
|-L|Specificare il <xref:System.Globalization.CultureInfo> nome delle impostazioni cultura, ad esempio "en-US".|  
|-E|Generare oggetti c# nello spazio dei nomi specificato per le voci di comando, seguito da [C&#124;H&#124;N]:*filename*dove C = c#, H = intestazione di C++, N = lo spazio dei nomi. Lo spazio dei nomi è necessaria per il linguaggio c#.|  
|-v|Output dettagliato.|  
  
 All'opzione -L indica al compilatore di selezionare un gruppo di stringhe per produrre il file CTO binario corrispondente per il dato <xref:System.Globalization.CultureInfo> nome delle impostazioni cultura. Il nome delle impostazioni cultura specificato deve corrispondere all'attributo di linguaggio di uno o più [elemento Strings](../../extensibility/strings-element.md) nel file con estensione vsct. Se un elemento stringhe disponga di alcun attributo di linguaggio, è ereditata dal che contiene [elemento CommandTable](../../extensibility/commandtable-element.md).  
  
 Un file con estensione vsct può disporre di più elementi di stringhe, e ognuno può avere un attributo di linguaggio diverso. Globalizzazione si ottiene eseguendo il compilatore VSCT più volte e modificando l'opzione -L per ogni nome di impostazioni cultura.  
  
 Se il nome delle impostazioni cultura assegnato all'opzione -L non corrisponde all'attributo di linguaggio di qualsiasi elemento di stringhe, il compilatore proverà in modo che corrisponda alla lingua e non dell'area geografica. Ad esempio, se non viene trovato "en-US", il compilatore proverà "en" invece. In caso contrario, verrà effettuato un tentativo di impostazioni cultura correnti del sistema operativo. In caso contrario, esegue la compilazione del primo elemento di stringhe che viene trovato.  
  
 L'opzione -E utilizzabile per generare un file di intestazione di tipo C che contiene i simboli utilizzati per la tabella di comando o per generare un file c# che contiene gli oggetti per i simboli di comando.  
  
 -D e -I cambi di avere la sintassi dei flag per il preprocessore C Cl.exe che hanno lo stesso nome. – D per l'espansione del basato su XML vengano utilizzate le definizioni che hanno il formato X = Y \<definiti > test in `Condition` attributi. : I percorsi di inclusione vengono usati per risolvere \<inclusione >, \<Extern > e \<Bitmap > i riferimenti di file. Per altre informazioni, vedere la [VSCT XML Schema Reference](../../extensibility/vsct-xml-schema-reference.md).  
  
 Il compilatore VSCT anche in grado di decompilare un file binario compilato in precedenza. A tale scopo, specificare un file binario per il \<FileIn >.   Se il file binario è stato generato dal compilatore VSCT, avrà relativi simboli già incorporati e produrrà l'output con i nomi simbolici in una \<simboli > sezione dell'output. Se il file binario è stato generato dal compilatore CTC, l'output conterrà i GUID e ID effettivo. Se il file *.ctsym derivante da versioni correnti di Ctc.exe è nella stessa cartella del file di input binario, i simboli verranno caricati da tale file e usati per l'output.  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Command Table (. File Vsct)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimento allo Schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)   
 [Come i pacchetti VSPackage aggiungono elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

