---
title: Registrazione di verbi per estensioni di File | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 73555abcc1a3c6afebf6528cc493e62a403ad00a
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49196326"
---
# <a name="registering-verbs-for-file-name-extensions"></a>Registrazione di verbi per le estensioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'associazione di un'estensione di file a un'applicazione ha in genere un'azione da preferire che si verifica quando un utente fa doppio clic su un file. Preferibile utilizzare l'azione è collegata a un verbo, ad esempio open, che corrisponde all'azione.  
  
 È possibile registrare i verbi associati con un identificatore a livello di codice (ProgID) per un'estensione usando la chiave di Shell che si trova in HKEY_CLASSES_ROOT\\*progid*\shell. Per altre informazioni, vedere [tipi di File](http://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Registrazione di verbi Standard  
 Il sistema operativo riconosce i verbi standard seguenti:  
  
-   Apri  
  
-   Edit  
  
-   Riproduci  
  
-   Print  
  
-   Anteprima  
  
 Quando possibile, registrare un verbo standard. La scelta più comune è il verbo Open. Usare il verbo di modifica solo se è presente una netta differenza tra l'apertura del file e la modifica del file. Ad esempio, aprire un file con estensione htm lo visualizza nel browser, mentre la modifica di un file con estensione htm avvia un editor HTML. Verbi standard vengono localizzati con impostazioni locali del sistema operativo.  
  
> [!NOTE]
>  Quando si registrano i verbi standard, non impostare il valore predefinito per il codice Open. Il valore predefinito contiene la stringa di visualizzazione del menu. Il sistema operativo fornisce questa stringa per i verbi standard.  
  
 I file di progetto devono essere registrati per avviare una nuova istanza della [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] quando un utente apre il file. L'esempio seguente illustra una registrazione di un verbo standard per un [!INCLUDE[csprcs](../includes/csprcs-md.md)] progetto.  
  
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
  
 Per aprire un file in un'istanza esistente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], registrare una chiave DDEEXEC. L'esempio seguente illustra una registrazione di un verbo standard per un [!INCLUDE[csprcs](../includes/csprcs-md.md)] file con estensione cs.  
  
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
  
## <a name="setting-the-default-verb"></a>Impostare il verbo predefinito  
 Il verbo predefinito è l'azione che viene eseguito quando un utente fa doppio clic su un file in Windows Explorer. Il verbo predefinito è il verbo specificato come valore predefinito per il HKEY_CLASSES_ROOT\\*progid*\Shell chiave. Se viene specificato alcun valore, il verbo predefinito è il primo verbo specificato nella chiave HKEY_CLASSES_ROOT\\*progid*\Shell elenco di chiavi.  
  
> [!NOTE]
>  Se si prevede di modificare il verbo predefinito per un'estensione in una distribuzione side-by-side, prendere in considerazione l'impatto sull'installazione e rimozione. Durante l'installazione il valore predefinito originale viene sovrascritto.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle associazioni di file side-by-side](../extensibility/managing-side-by-side-file-associations.md)

