---
title: -Upgrade (devenv.exe) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- /upgrade Devenv switch
- Devenv, /upgrade switch
- upgrade Devenv switch
ms.assetid: 3468045c-5cc9-4157-9a9d-622452145d27
caps.latest.revision: 22
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 79a00da92ac2da6eb37fa1eef90fa112598d23f3
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49264960"
---
# <a name="upgrade-devenvexe"></a>/Upgrade (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Aggiorna il file della soluzione e tutti i relativi file di progetto oppure il file di progetto specificato ai formati di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] correnti dei file.  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv SolutionFile | ProjectFile /upgrade  
```  
  
## <a name="arguments"></a>Argomenti  
 `SolutionFile`  
 Obbligatorio se si aggiorna un'intera soluzione e i relativi progetti. Il percorso e il nome di un file di soluzione. È possibile immettere solo il nome del file di soluzione oppure il percorso completo e il nome del file di soluzione. Se non esistono, la cartella o il nome file verranno creati.  
  
 `ProjectFile`  
 Obbligatorio se si esegue l'aggiornamento di un singolo progetto. Il percorso e il nome del file di progetto nella soluzione. È possibile immettere solo il nome del file di progetto oppure il percorso completo e il nome del file di progetto. Se non esistono, la cartella o il nome file verranno creati.  
  
## <a name="remarks"></a>Note  
 I backup vengono creati e copiati automaticamente in una directory denominata Backup creata nella directory corrente.  
  
 Per consentire l'aggiornamento di soluzioni o progetti inclusi nel controllo del codice sorgente è necessario estrarli.  
  
 Se si usa l'opzione `/upgrade`, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] non viene avviato. È possibile visualizzare i risultati dell'aggiornamento nel report di aggiornamento relativo al linguaggio di sviluppo della soluzione o del progetto. Non vengono restituiti messaggi di errore o informazioni sull'utilizzo. Per altre informazioni sull'aggiornamento di progetti in [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], vedere [procedura: risolvere i problemi di riuscita Visual Studio gli aggiornamenti di progetti](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md).  
  
## <a name="example"></a>Esempio  
 Questo esempio aggiorna un file di soluzione denominato "MyProject.sln" nella cartella predefinita per le soluzioni di [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
```  
devenv "MyProject.sln" /upgrade  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: risolvere i problemi di aggiornamento di progetti di Visual Studio con esito negativo](../../porting/how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades.md)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)



