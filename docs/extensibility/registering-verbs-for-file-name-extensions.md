---
title: Registrazione dei verbi per le estensioni di file Documenti Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ac2854f1799075cc14d9beb557335be5228be21d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701527"
---
# <a name="register-verbs-for-file-name-extensions"></a>Registrare i verbi per le estensioni di fileRegister verbs for file name extensions
L'associazione di un'estensione di file con un'applicazione ha in genere un'azione preferita che si verifica quando un utente fa doppio clic su un file. Questa azione preferita è collegata a un verbo, ad esempio open, che corrisponde all'azione.

 È possibile registrare i verbi associati a un identificatore a livello di codice (ProgID) per un'estensione utilizzando la chiave Shell che si trova in **\{HKEY_CLASSES_ROOT progid**. Per ulteriori informazioni, consultate [Tipi di file.](/windows/desktop/shell/fa-file-types)

## <a name="register-standard-verbs"></a>Registrare verbi standard
 Il sistema operativo riconosce i seguenti verbi standard:

- Apri

- Modifica

- Esegui

- Print

- Anteprima

  Quando possibile, registrare un verbo standard. La scelta più comune è il verbo Open. Utilizzare il verbo Edit solo se esiste una chiara differenza tra l'apertura del file e la modifica del file. Ad esempio, l'apertura di un file *htm* lo visualizza nel browser, mentre la modifica di un file *htm* avvia un editor HTML. I verbi standard vengono localizzati con le impostazioni locali del sistema operativo.

> [!NOTE]
> Quando si registrano verbi standard, non impostare il valore predefinito per il tasto Open. Il valore predefinito contiene la stringa di visualizzazione nel menu. Il sistema operativo fornisce questa stringa per i verbi standard.

 I file di progetto devono essere [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] registrati per avviare una nuova istanza di quando un utente apre il file. Nell'esempio seguente viene illustrata [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] la registrazione di un verbo standard per un progetto.

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

 Per aprire un file in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]un'istanza esistente di , registrare una chiave DDEEXEC. Nell'esempio seguente viene illustrata [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] una registrazione dei verbi standard per un file *con estensione cs.*

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
 Il verbo predefinito è l'azione che viene eseguita quando un utente fa doppio clic su un file in Esplora risorse. Il verbo predefinito è il verbo specificato come valore predefinito per la **\\*progid*** HKEY_CLASSES_ROOT chiave progid . Se non viene specificato alcun valore, il verbo predefinito è il primo verbo specificato nell'elenco **\\*progid*** di HKEY_CLASSES_ROOT chiave progid .

> [!NOTE]
> Se si prevede di modificare il verbo predefinito per un'estensione in una distribuzione side-by-side, considerare l'impatto sull'installazione e la rimozione. Durante l'installazione il valore predefinito originale viene sovrascritto.

## <a name="see-also"></a>Vedere anche
- [Gestire le associazioni di file side-by-side](../extensibility/managing-side-by-side-file-associations.md)
