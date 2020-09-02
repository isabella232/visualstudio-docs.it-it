---
title: Registrazione dei verbi per le estensioni di file | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- verbs, registering
ms.assetid: 81a58e40-7cd0-4ef4-a475-c4e1e84d6e06
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: dbd97310163a4eb3ae5502c6341dc73322ca653d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65685278"
---
# <a name="registering-verbs-for-file-name-extensions"></a>Registrazione di verbi per le estensioni
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

L'associazione di un'estensione di file a un'applicazione in genere presenta un'azione preferenziale che si verifica quando un utente fa doppio clic su un file. Questa azione preferita è collegata a un verbo, ad esempio Open, che corrisponde all'azione.  
  
 È possibile registrare i verbi associati a un identificatore a livello di codice (ProgID) per un'estensione usando la chiave della shell situata in HKEY_CLASSES_ROOT \\ *ProgID*\Shell. Per ulteriori informazioni, vedere [tipi di file](https://msdn.microsoft.com/library/windows/desktop/cc144148\(v=vs.85\).aspx).  
  
## <a name="registering-standard-verbs"></a>Registrazione di verbi standard  
 Il sistema operativo riconosce i verbi standard seguenti:  
  
- Apri  
  
- Modifica  
  
- Esegui  
  
- Stampa  
  
- Anteprima  
  
  Quando possibile, registrare un verbo standard. La scelta più comune è il verbo Open. Usare il verbo di modifica solo se esiste una differenza netta tra l'apertura del file e la modifica del file. Se ad esempio si apre un file con estensione htm, questo viene visualizzato nel browser, mentre la modifica di un file con estensione htm avvia un editor HTML. I verbi standard sono localizzati con le impostazioni locali del sistema operativo.  
  
> [!NOTE]
> Quando si registrano verbi standard, non impostare il valore predefinito per la chiave di apertura. Il valore predefinito contiene la stringa di visualizzazione nel menu. Il sistema operativo fornisce questa stringa per i verbi standard.  
  
 I file di progetto devono essere registrati per avviare una nuova istanza di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] quando un utente apre il file. Nell'esempio seguente viene illustrata la registrazione di un verbo standard per un [!INCLUDE[csprcs](../includes/csprcs-md.md)] progetto.  
  
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
  
 Per aprire un file in un'istanza esistente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , registrare una chiave di DDEExec. Nell'esempio seguente viene illustrata la registrazione di un verbo standard per un [!INCLUDE[csprcs](../includes/csprcs-md.md)] file con estensione cs.  
  
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
  
## <a name="setting-the-default-verb"></a>Impostazione del verbo predefinito  
 Il verbo predefinito è l'azione che viene eseguita quando un utente fa doppio clic su un file in Esplora risorse. Il verbo predefinito è il verbo specificato come valore predefinito per la \\ chiave \Shell contiene*progid*del HKEY_CLASSES_ROOT. Se non viene specificato alcun valore, il verbo predefinito è il primo verbo specificato nell' \\ elenco di chiavi \Shell contiene*ProgID*HKEY_CLASSES_ROOT.  
  
> [!NOTE]
> Se si prevede di modificare il verbo predefinito per un'estensione in una distribuzione side-by-Side, considerare l'effetto sull'installazione e la rimozione. Durante l'installazione, il valore predefinito originale viene sovrascritto.  
  
## <a name="see-also"></a>Vedere anche  
 [Gestione delle associazioni di file side-by-side](../extensibility/managing-side-by-side-file-associations.md)
