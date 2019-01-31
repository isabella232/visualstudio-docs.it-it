---
title: -LCID (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- language default
- locale IDs, setting for IDE
- Devenv, /LCID switch
- locale IDs
- /l Devenv switch
- LCID devenv switch
- /lcid Devenv switch
ms.assetid: 3a3f4e70-ea66-4351-9d62-acb1dec30e8e
caps.latest.revision: 15
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: def8ce2a40e068c602b0182b4580f5e3b524d222
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54782223"
---
# <a name="lcid-devenvexe"></a>/LCID (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Imposta la lingua predefinita usata per il testo, la valuta e altri valori all'interno dell'ambiente di sviluppo integrato (IDE).  
  
## <a name="syntax"></a>Sintassi  
  
```  
devenv {/LCID|/l} LocaleID  
```  
  
## <a name="arguments"></a>Argomenti  
 `LocaleID`  
 Obbligatorio. LCID (ID impostazioni locali) della lingua specificata.  
  
## <a name="remarks"></a>Note  
 Carica l'IDE e imposta la lingua naturale predefinita per l'ambiente. Questa modifica è persistente tra le sessioni e viene riportata nel riquadro **Impostazioni internazionali** delle opzioni **Ambiente** nella finestra di dialogo **Opzioni** nell'IDE.  
  
 Se la lingua specificata non è disponibile nel sistema dell'utente, l'opzione /LCID viene ignorata.  
  
 Nella tabella seguente vengono elencati gli LCID delle lingue supportate da [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
|Linguaggio|LCID|  
|--------------|----------|  
|Cinese (semplificato)|2052|  
|Cinese (tradizionale)|1028|  
|Inglese|1040|  
|Francese|1036|  
|Tedesco|1031|  
|Italiano|1040|  
|Giapponese|1041|  
|Coreano|1042|  
|Spagnolo|3082|  
  
## <a name="example"></a>Esempio  
 In questo esempio viene caricato l'IDE con le stringhe delle risorse in lingua inglese.  
  
```  
devenv /LCID 1033  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Devenv Command Line Switches](../../ide/reference/devenv-command-line-switches.md)  (Opzioni della riga di comando di Devenv)  
 [Impostazioni internazionali, Ambiente, finestra di dialogo Opzioni](../../ide/reference/international-settings-environment-options-dialog-box.md)   
 [Personalizzazione del layout delle finestre](../../ide/customizing-window-layouts-in-visual-studio.md)
