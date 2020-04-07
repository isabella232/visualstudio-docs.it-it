---
title: Aggiunta di opzioni della riga di comando Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 3f2df3a704c34d97c9d5acfa72249fe492b7f812
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740174"
---
# <a name="add-command-line-switches"></a>Aggiungere opzioni della riga di comando
È possibile aggiungere opzioni della riga di comando che si applicano al pacchetto VSPackage quando *devenv.exe* viene eseguito. Utilizzare <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> per dichiarare il nome dell'opzione e le relative proprietà. In questo esempio, l'opzione MySwitch viene aggiunta per una sottoclasse di VSPackage denominata **AddCommandSwitchPackage** senza argomenti e con il pacchetto VSPackage caricato automaticamente.

```csharp
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]
```

 I parametri denominati sono riportati nelle descrizioni seguenti.

||||
|-|-|-|-|
| Parametro | Descrizione|
| Argomenti | Numero di argomenti per l'opzione. Può essere "" o un elenco di argomenti. |
| Caricodirichieste | Caricare automaticamente il pacchetto VSPackage se è impostato su 1, altrimenti impostato su 0.Load the VSPackage automatically if this is set to 1, otherwise set to 0. |
| Helpstring | Stringa della Guida o ID risorsa della stringa da visualizzare con **devenv /?**. |
| Nome | L'interruttore. |
| PackageGuid | GUID del pacchetto. |

 Il primo valore di Arguments è in genere 0 o 1.The first of Arguments is usually 0 or 1. È possibile utilizzare un valore speciale di '' per indicare che l'intero resto della riga di comando è l'argomento. Ciò può essere utile per gli scenari di debug in cui un utente deve passare una stringa di comando del debugger.

 Il valore DemandLoad `true` è (1) o `false` (0) indica che il pacchetto VSPackage deve essere caricato automaticamente.

 Il valore HelpString è l'ID di risorsa della stringa visualizzata in **devenv /?** Visualizzazione della Guida. Questo valore deve essere nel formato "#nnn" dove nnn è un numero intero. Il valore stringa nel file di risorse deve terminare con un carattere di nuova riga.

 Il valore Name è il nome dell'opzione.

 Il valore PackageGuid è il GUID del pacchetto che implementa questa opzione. L'IDE utilizza questo GUID per trovare il pacchetto VSPackage nel Registro di sistema a cui si applica l'opzione della riga di comando.

## <a name="retrieve-command-line-switches"></a>Recuperare le opzioni della riga di comando
 Quando il pacchetto viene caricato, è possibile recuperare le opzioni della riga di comando completando la procedura seguente.

1. Nell'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> VSPackage, chiamare `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> per ottenere l'interfaccia.

2. Chiamata <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> per recuperare le opzioni della riga di comando immesse dall'utente.

   Nel codice seguente viene illustrato come determinare se l'opzione della riga di comando MySwitch è stata immessa dall'utente:

```csharp
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));

int isPresent = 0;
string optionValue = "";

cmdline.GetOption("MySwitch", out isPresent, out optionValue);
```

 È tua responsabilità controllare le opzioni della riga di comando ogni volta che il pacchetto viene caricato.

## <a name="see-also"></a>Vedere anche
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>
- <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>
- [Opzioni della riga di comando devenv](../ide/reference/devenv-command-line-switches.md)
- [Utilità CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)
- [. File Pkgdef](https://devblogs.microsoft.com/visualstudio/whats-a-pkgdef-and-why/)
