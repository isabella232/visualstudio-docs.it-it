---
title: Aggiunta di opzioni della riga di comando | Microsoft Docs
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bb4abf5352ac6ad78852bd3224df0b22784470db
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "85903481"
---
# <a name="add-command-line-switches"></a>Aggiungi opzioni della riga di comando
È possibile aggiungere opzioni della riga di comando che si applicano al pacchetto VSPackage quando *devenv.exe* viene eseguito. Usare <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> per dichiarare il nome dell'opzione e le relative proprietà. In questo esempio viene aggiunta l'opzione di commutazione a pagina per una sottoclasse di VSPackage denominata **AddCommandSwitchPackage** senza argomenti e con il pacchetto VSPackage caricato automaticamente.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 I parametri denominati sono indicati nelle descrizioni seguenti.

|Nome|Descrizione|
|-|-|
| Argomenti | Numero di argomenti per l'opzione. Può essere "*" o un elenco di argomenti. |
| DemandLoad – viene | Caricare il pacchetto VSPackage automaticamente se è impostato su 1, in caso contrario è impostato su 0. |
| HelpString | Stringa della guida o ID della risorsa della stringa da visualizzare con **devenv/?**. |
| Nome | Opzione. |
| PackageGuid | GUID del pacchetto. |

 Il primo valore di arguments è in genere 0 o 1. È possibile usare un valore speciale di "*" per indicare che l'intero resto della riga di comando è l'argomento. Questa operazione può essere utile per gli scenari di debug in cui un utente deve passare una stringa di comando del debugger.

 Il valore DemandLoad – viene è `true` (1) o `false` (0) indica che il pacchetto VSPackage deve essere caricato automaticamente.

 Il valore HelpString è l'ID risorsa della stringa visualizzata in **devenv/?** Visualizzazione della guida. Questo valore deve essere nel formato "#nnn", dove nnn è un numero intero. Il valore stringa nel file di risorse deve terminare con un carattere di nuova riga.

 Il valore Name è il nome dell'opzione.

 Il valore PackageGuid è il GUID del pacchetto che implementa questa opzione. L'IDE usa questo GUID per trovare il pacchetto VSPackage nel registro di sistema a cui si applica l'opzione della riga di comando.

## <a name="retrieve-command-line-switches"></a>Recupera opzioni della riga di comando
 Quando il pacchetto viene caricato, è possibile recuperare le opzioni della riga di comando completando i passaggi seguenti.

1. Nell'implementazione di VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> , chiamare `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> per ottenere l' <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interfaccia.

2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> per recuperare le opzioni della riga di comando immesse dall'utente.

   Nel codice riportato di seguito viene illustrato come verificare se l'opzione della riga di comando del parametro è stata immessa dall'utente:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 È responsabilità dell'utente verificare le opzioni della riga di comando ogni volta che il pacchetto viene caricato.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)
- [Utilità CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. File pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
