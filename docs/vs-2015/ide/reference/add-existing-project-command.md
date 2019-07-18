---
title: Comando Aggiungi progetto esistente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- file.addexistingproject
helpviewer_keywords:
- Add Existing Project command
- File.AddExistingProject
ms.assetid: 71cf3e31-c76b-405b-ad6a-1b1bc654bd40
caps.latest.revision: 19
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4778efc4a50ceb63e72d4283644537345510e833
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "68194968"
---
# <a name="add-existing-project-command"></a>Comando Aggiungi progetto esistente
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Aggiunge un progetto esistente alla soluzione corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
File.AddExistingProject filename  
```  
  
## <a name="arguments"></a>Argomenti  
 `filename`  
 facoltativo. Percorso completo e nome del progetto comprensivo di estensione da aggiungere alla soluzione.  
  
 Se l'argomento `filename` include spazi, deve essere racchiuso tra virgolette.  
  
 Se non viene specificato un nome file, il comando aprirà la finestra di dialogo in cui l'utente potrà selezionare un progetto.  
  
## <a name="remarks"></a>Osservazioni  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)
