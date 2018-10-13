---
title: Comando Apri progetto | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- file.openproject
helpviewer_keywords:
- op command
- File.OpenProject command
- Open Project command
ms.assetid: baa85f86-041b-49f4-9ced-0c397dc180e1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: b25ee0e6ba4dfa5c29d5a009087afb55509d0c08
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49263920"
---
# <a name="open-project-command"></a>Comando Apri progetto
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Apre un progetto esistente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
File.OpenProject filename  
```  
  
## <a name="arguments"></a>Argomenti  
 `filename`  
 Obbligatorio. Percorso completo e nome del file di progetto da aprire.  
  
 La sintassi per l'argomento `filename` richiede che i percorsi contenenti spazi usino le virgolette.  
  
## <a name="remarks"></a>Note  
 Il completamento automatico tenta di individuare il percorso e il nome file corretti durante la digitazione.  
  
 Questo comando non è disponibile durante il debug.  
  
## <a name="example"></a>Esempio  
 In questo esempio viene aperto il progetto [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] Test1.  
  
```  
>File.OpenProject "C:\My Projects\Test1\Test1.vbproj"  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



