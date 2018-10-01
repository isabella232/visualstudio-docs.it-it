---
title: -Clean (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- builds [Team System], cleaning files
- clean Devenv switch
- /clean Devenv switch
- Devenv, /clean switch
ms.assetid: 79929dfd-22c9-4cec-a0d0-a16f15b8f7e4
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 194081570d3b6e99966e960b3cef3163aeb945f9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47527703"
---
# <a name="clean-devenvexe"></a>/Clean (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [-Clean (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/clean-devenv-exe).  
  
  
Pulisce tutti i file intermedi e le directory di output.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv FileName /Clean [ /project projectnameorfile [/projectconfig name ] ]  
```  
  
## <a name="arguments"></a>Argomenti  
 `FileName`  
 Obbligatorio. Percorso completo e nome del file di soluzione o di progetto.  
  
 /project `ProjName`  
 Facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName` il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.  
  
 /projectconfig `ProjConfigName`  
 Facoltativo. Nome della configurazione della build di un progetto da usare durante la pulizia dell'elemento `/project` specificato.  
  
## <a name="remarks"></a>Note  
 Questa opzione esegue la stessa funzione del comando di menu **Pulisci soluzione** nell'ambiente di sviluppo integrato (IDE).  
  
 Racchiudere le stringhe che includono spazi tra virgolette doppie.  
  
 Le informazioni di riepilogo sulle operazioni di pulizia e compilazione, compresi gli errori, possono essere visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.  
  
## <a name="example"></a>Esempio  
 Nel primo esempio viene pulita la soluzione `MySolution` usando la configurazione predefinita specificata nel file di soluzione.  
  
 Nel secondo esempio viene pulito il progetto `CSharpConsoleApp` usando la configurazione della build del progetto `Debug` all'interno della configurazione della soluzione `Debug` di `MySolution`.  
  
```  
Devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean  
  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /Clean /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig "Debug"   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)



