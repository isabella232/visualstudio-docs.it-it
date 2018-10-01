---
title: Comando Controllo immediato | Microsoft Docs
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
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9d340f88b83e5dce3054a264a2815fa96707a19f
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47529253"
---
# <a name="quick-watch-command"></a>Comando Controllo immediato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Quick Watch comando](https://docs.microsoft.com/visualstudio/ide/reference/quick-watch-command).  
  
  
Visualizza il testo selezionato o specificato nel campo espressione della finestra di [finestra di dialogo Controllo immediato](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867). È possibile usare questa finestra di dialogo per calcolare il valore corrente di una variabile o di un'espressione riconosciuta dal debugger o i contenuti di un registro. È anche possibile modificare il valore di una variabile non costante o i contenuti di un registro.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.QuickWatchq [text]  
```  
  
## <a name="arguments"></a>Argomenti  
 `text`  
 Facoltativo. Il testo da aggiungere alla finestra di dialogo **Controllo immediato**.  
  
## <a name="remarks"></a>Note  
 Se `text` è omesso, il testo o la parola selezionata in corrispondenza del cursore viene aggiunta alla finestra Espressioni di controllo.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.QuickWatch  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: usare la finestra di dialogo Controllo immediato](http://msdn.microsoft.com/library/ffaee1dd-e5ce-4ef2-9401-d28329398867)   
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Alias di comandi di Visual Studio](../../ide/reference/visual-studio-command-aliases.md)



