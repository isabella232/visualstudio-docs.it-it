---
title: Aggiunta Command-Line opzioni | Microsoft Docs
description: Informazioni su come aggiungere opzioni della riga di comando che vengono applicate a un vspackage quando viene devenv.exe comando.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 539ab9c7a70d1e2ed22c864132048175eebfcda3
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122043856"
---
# <a name="add-command-line-switches"></a>Aggiungere opzioni della riga di comando
È possibile aggiungere opzioni della riga di comando che si applicano al pacchetto VSPackage *quando* devenv.exeviene eseguito. Usare <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> per dichiarare il nome dell'opzione e le relative proprietà. In questo esempio viene aggiunta l'opzione MySwitch per una sottoclasse di VSPackage denominata **AddCommandSwitchPackage** senza argomenti e con il pacchetto VSPackage caricato automaticamente.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 I parametri denominati sono illustrati nelle descrizioni seguenti.

|Nome|Descrizione|
|-|-|
| Argomenti | Numero di argomenti per l'opzione. Può essere "*" o un elenco di argomenti. |
| DemandLoad | Caricare automaticamente il pacchetto VSPackage se è impostato su 1, in caso contrario impostato su 0. |
| Helpstring | Stringa della Guida o ID risorsa della stringa da visualizzare con **devenv /?**. |
| Nome | Opzione . |
| PackageGuid | GUID del pacchetto. |

 Il primo valore di Arguments è in genere 0 o 1. È possibile usare un valore speciale '*' per indicare che l'intero resto della riga di comando è l'argomento . Ciò può essere utile per scenari di debug in cui un utente deve passare una stringa di comando del debugger.

 Il valore DemandLoad `true` è (1) o (0) indica che il `false` pacchetto VSPackage deve essere caricato automaticamente.

 Il valore HelpString è l'ID risorsa della stringa visualizzata in **devenv /?** Visualizzazione della Guida. Questo valore deve essere nel formato "#nnn" dove nnn è un numero intero. Il valore stringa nel file di risorse deve terminare con un carattere di nuova riga.

 Il valore Name è il nome dell'opzione.

 Il valore PackageGuid è il GUID del pacchetto che implementa questa opzione. L'IDE usa questo GUID per trovare il pacchetto VSPackage nel Registro di sistema a cui si applica l'opzione della riga di comando.

## <a name="retrieve-command-line-switches"></a>Recuperare le opzioni della riga di comando
 Quando il pacchetto viene caricato, è possibile recuperare le opzioni della riga di comando completando la procedura seguente.

1. Nell'implementazione di VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> chiamare `QueryService` per ottenere <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> l'interfaccia .

2. Chiamare <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> per recuperare le opzioni della riga di comando immesse dall'utente.

   Il codice seguente illustra come determinare se l'opzione della riga di comando MySwitch è stata immessa dall'utente:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 È responsabilità dell'utente verificare le opzioni della riga di comando ogni volta che viene caricato il pacchetto.

## <a name="see-also"></a>Vedi anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)
- [Utilità CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. File Pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
