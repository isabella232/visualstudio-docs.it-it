---
title: Comando Aggiungi progetto esistente | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 048ba8e43b66ac5ad4bbc1d0c09adb75a2d61e1d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47518160"
---
# <a name="add-existing-project-command"></a>Comando Aggiungi progetto esistente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [aggiunta di comando di progetto esistenti](https://docs.microsoft.com/visualstudio/ide/reference/add-existing-project-command).  
  
  
Aggiunge un progetto esistente alla soluzione corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>Argomenti  
 `filename`  
 Facoltativo. Percorso completo e nome del progetto comprensivo di estensione da aggiungere alla soluzione.  
  
 Se l'argomento `filename` include spazi, deve essere racchiuso tra virgolette.  
  
 Se non viene specificato un nome file, il comando aprirà la finestra di dialogo in cui l'utente potrà selezionare un progetto.  
  
## <a name="remarks"></a>Note  
 Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene aggiunto il progetto [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] TestProject1 alla soluzione corrente.  
  
```  
>File.AddExistingProject "c:\visual studio projects\TestProject1.vbproj"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



