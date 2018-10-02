---
title: -ResetAddin (devenv.exe) | Microsoft Docs
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
- disable addin
- addin state
- reset addin
ms.assetid: 9e339c8d-d768-4d86-8f45-2f479fc8255b
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: f306e6952b5cf0d41901b85e554cfc3f444dbb00
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47519450"
---
# <a name="resetaddin-devenvexe"></a>/ResetAddin (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [- /resetaddin (devenv.exe)](https://docs.microsoft.com/visualstudio/ide/reference/resetaddin-devenv-exe).  
  
  
Rimuove i comandi e l'interfaccia utente dei comandi associata al componente aggiuntivo specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Devenv /ResetAddin AddIn  
```  
  
## <a name="arguments"></a>Argomenti  
 `AddIn`  
 Facoltativo. Nome del comando del componente aggiuntivo.  
  
## <a name="remarks"></a>Note  
 Per impostazione predefinita, il nome del comando del componente aggiuntivo è uguale a *\<NomeSoluzioneComponenteAggiuntivo>*.Connect *.\<NomeSoluzioneComponenteAggiuntivo>* e viene visualizzato in Connect.cs come parametro `commandName` del metodo `Exec`. È anche possibile verificare il nome del comando digitando l'inizio del nome del componente aggiuntivo nella finestra dei comandi in Visual Studio e usando Intellisense per completarlo.  
  
## <a name="example"></a>Esempio  
 L'esempio seguente avvia Visual Studio e impedisce l'esecuzione all'avvio del componente aggiuntivo `MyAddin`.  
  
```  
Devenv.exe /ResetAddin MyAddin.Connect.MyAddin  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Personalizzazione delle impostazioni di sviluppo in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)   
 [Opzioni della riga di comando devenv](../../ide/reference/devenv-command-line-switches.md)



