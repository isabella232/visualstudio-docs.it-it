---
title: Registrazione dei verbi per le estensioni di file | Microsoft Docs
description: Informazioni su come registrare un verbo associato a un identificatore a livello di codice per un'estensione di file usando una chiave della shell.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 00359f3d7d367333af8796b8d1a6ece104287539
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122124490"
---
# <a name="register-verbs-for-file-name-extensions"></a>Registrare i verbi per le estensioni di file
L'associazione di un'estensione di file a un'applicazione in genere ha un'azione preferita che si verifica quando un utente fa doppio clic su un file. Questa azione preferita è collegata a un verbo, ad esempio open, che corrisponde all'azione.

 È possibile registrare verbi associati a un identificatore a livello di codice (ProgID) per un'estensione usando la chiave shell disponibile **in \{ HKEY_CLASSES_ROOT progid}\shell**. Per altre informazioni, vedere [Tipi di file](/windows/desktop/shell/fa-file-types).

## <a name="register-standard-verbs"></a>Registrare verbi standard
 Il sistema operativo riconosce i verbi standard seguenti:

- Apri

- Modifica

- Esegui

- Stampa

- Anteprima

  Quando possibile, registrare un verbo standard. La scelta più comune è il verbo Open. Usare il verbo Edit solo se esiste una differenza chiara tra l'apertura del file e la modifica del file. Ad esempio, *l'apertura.htm* file di testo lo visualizza nel browser, mentre la modifica di un *file*.htmavvia un editor HTML. I verbi standard sono localizzati con le impostazioni locali del sistema operativo.

> [!NOTE]
> Quando si registrano verbi standard, non impostare il valore predefinito per la chiave Open. Il valore predefinito contiene la stringa di visualizzazione nel menu. Il sistema operativo fornisce questa stringa per i verbi standard.

 Project i file devono essere registrati per avviare una nuova istanza di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] quando un utente apre il file. Nell'esempio seguente viene illustrata una registrazione di verbi standard per un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] progetto.

```
[HKEY_CLASSES_ROOT\.csproj]
@="VisualStudio.csproj.8.0"

[HKEY_CLASSES_ROOT\.csproj\OpenWithList]
[HKEY_CLASSES_ROOT\.csproj\OpenWithList\VSLauncher.exe]
@=""

[HKEY_CLASSES_ROOT\.csproj\OpenWithProgids]
"VisualStudio.csproj.8.0"=""

[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open]
[HKEY_CLASSES_ROOT\Applications\VSLauncher.exe\Shell\Open\Command]
@="C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0]
@="C# Project file"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,0"

[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.csproj.8.0\shell\Open\Command]
@="\"C:\\Program Files\\Common Files\\Microsoft Shared\\MSEnv\\VSLauncher.exe\" \"%1\""
```

 Per aprire un file in un'istanza esistente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , registrare una chiave DDEEXEC. L'esempio seguente illustra una registrazione di verbi standard per un file [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] *con estensione cs.*

```
[HKEY_CLASSES_ROOT\.cs]
@="VisualStudio.cs.8.0"

[HKEY_CLASSES_ROOT\.cs\OpenWithList]
[HKEY_CLASSES_ROOT\.cs\OpenWithList\devenv.exe]
@=""

[HKEY_CLASSES_ROOT\.cs\OpenWithProgids]
"VisualStudio.cs.8.0"=""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0]
@="C# Source file"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\DefaultIcon]
@="C:\\VisualStudioPath\\VC#\\VCSPackages\\csproj.dll,1"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open]
[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\Command]
@="\"C:\\VisualStudioPath\\Common7\\IDE\\devenv.exe\" /dde \"%1\""

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec]
@="Open(\"%1\")"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Application]
@="VisualStudio.8.0"

[HKEY_CLASSES_ROOT\VisualStudio.cs.8.0\shell\Open\ddeexec\Topic]
@="system"
```

## <a name="set-the-default-verb"></a>Impostare il verbo predefinito
 Il verbo predefinito è l'azione eseguita quando un utente fa doppio clic su un file in Windows Explorer. Il verbo predefinito è il verbo specificato come valore predefinito per la chiave **\\ *HKEY_CLASSES_ROOT progid*\Shell.** Se non viene specificato alcun valore, il verbo predefinito è il primo verbo specificato nell'elenco HKEY_CLASSES_ROOT **\\ *chiave progid*\Shell.**

> [!NOTE]
> Se si prevede di modificare il verbo predefinito per un'estensione in una distribuzione side-by-side, considerare l'impatto sull'installazione e sulla rimozione. Durante l'installazione il valore predefinito originale viene sovrascritto.

## <a name="see-also"></a>Vedi anche
- [Gestire le associazioni di file side-by-side](../extensibility/managing-side-by-side-file-associations.md)
