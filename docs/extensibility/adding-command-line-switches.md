---
title: Aggiunta della riga di comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68e8cb770bdad809ffc6b8f150ddba2070dc4190
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "55009141"
---
# <a name="add-command-line-switches"></a>Aggiungere i parametri della riga di comando
È possibile aggiungere opzioni della riga di comando che si applicano al pacchetto VSPackage quando *devenv.exe* viene eseguita. Usare <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> per dichiarare il nome dell'opzione e le relative proprietà. In questo esempio viene aggiunta l'opzione MySwitch per una sottoclasse di VSPackage denominato **AddCommandSwitchPackage** senza argomenti e con il pacchetto VSPackage caricato automaticamente.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 I parametri denominati vengono visualizzati nelle descrizioni seguenti.

||||
|-|-|-|-|
| Parametro | Descrizione|
| Argomenti | Il numero di argomenti per il commutatore. Può essere "*", o un elenco di argomenti. |
| DemandLoad | Caricare il pacchetto VSPackage automaticamente se è impostato su 1, altrimenti è impostato su 0. |  
| HelpString | L'ID della Guida stringa o una risorsa della stringa da visualizzare con **devenv /?**. |
| nome | Questo parametro. |
| PackageGuid | Il GUID del pacchetto. |  
  
 Il primo valore degli argomenti è in genere 0 o 1. Un valore speciale di ' *' può essere utilizzato per indicare che tutto il resto della riga di comando è costituito dall'argomento. Ciò può essere utile negli scenari in cui un utente deve passare una stringa di comando del debugger di debug.  
  
 È il valore DemandLoad `true` (1) o `false` (0) indica che il pacchetto VSPackage deve essere caricato automaticamente.  
  
 Il valore HelpString è l'ID risorsa della stringa che viene visualizzato nei **devenv /?** Visualizzazione della Guida. Questo valore deve essere nel formato "#nnn" dove nnn è un numero intero. Il valore di stringa nel file di risorse deve terminare con un carattere di nuova riga.  
  
 Il valore del nome è il nome del commutatore.  
  
 Il valore PackageGuid è il GUID del pacchetto che implementa questo commutatore. L'IDE Usa questo GUID per trovare il pacchetto VSPackage nel Registro di sistema a cui viene applicata l'opzione della riga di comando.  
  
## <a name="retrieve-command-line-switches"></a>Recupero della riga di comando  
 Quando viene caricato il pacchetto, è possibile recuperare le opzioni della riga di comando, completare i passaggi seguenti.  
  
1. In un VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> implementazione, chiamare `QueryService` sul <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> per ottenere il <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfaccia.  
  
2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> per recuperare le opzioni della riga di comando immesso dall'utente.  
  
   Il codice seguente viene illustrato come determinare se l'opzione della riga di comando MySwitch è stata immessa dall'utente:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 È responsabilità dell'utente per verificare la presenza di opzioni della riga di comando ogni volta che viene caricato il pacchetto.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)   
 [CreatePkgDef utility](../extensibility/internals/createpkgdef-utility.md)   
 [.Pkgdef files](/visualstudio/extensibility/shell/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file)