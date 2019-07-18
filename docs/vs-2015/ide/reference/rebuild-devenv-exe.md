---
title: -Rebuild (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /rebuild switch
- rebuild Devenv switch (/rebuild)
- projects [Visual Studio], rebuilding
- /rebuild Devenv switch
- applications [Visual Studio], rebuilding
ms.assetid: c5a8a4bf-0e2b-46eb-a44a-8aeb29b92c32
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 72818a3bdb4f983326c95b10cfe4e6af4445cc2f
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68200830"
---
# <a name="rebuild-devenvexe"></a>/Rebuild (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Pulisce e quindi compila la configurazione della soluzione specificata.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv SolutionName /rebuild SolnConfigName [/project ProjName] [/projectconfig ProjConfigName]  
```  
  
## <a name="arguments"></a>Argomenti  
 `SolnConfigName`  
 Obbligatorio. Nome della configurazione della soluzione da usare per ricompilare la soluzione indicata in `SolutionName`.  
  
 `SolutionName`  
 Obbligatorio. Il percorso completo e il nome del file della soluzione.  
  
 /project `ProjName`  
 facoltativo. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere il percorso relativo del file di progetto dalla cartella `SolutionName` il nome visualizzato del progetto o il percorso completo e il nome del file di progetto.  
  
 /projectconfig `ProjConfigName`  
 facoltativo. Nome della configurazione di compilazione del progetto da usare per la ricompilazione dell'elemento `/project` denominato.  
  
## <a name="remarks"></a>Osservazioni  
  
- Questa opzione esegue la stessa funzione del comando di menu **Ricompila soluzione** nell'ambiente di sviluppo integrato (IDE).  
  
- Racchiudere le stringhe che includono spazi tra virgolette doppie.  
  
- Le informazioni di riepilogo sulle operazioni di pulizia e compilazione, compresi gli errori, possono essere visualizzate nella finestra di **comando** o in qualsiasi file di log specificato con l'opzione `/out`.  
  
## <a name="example"></a>Esempio  
 Questo esempio pulisce e ricompila il progetto `CSharpWinApp` usando la configurazione di compilazione del progetto `Debug` all'interno della configurazione della soluzione `Debug` di `MySolution`.  
  
```  
devenv "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln" /rebuild Debug /project "CSharpWinApp\CSharpWinApp.csproj" /projectconfig Debug   
```  
  
## <a name="see-also"></a>Vedere anche  
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)   
 [/Clean (devenv.exe)](../../ide/reference/clean-devenv-exe.md)   
 [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)
