---
title: Comando Controllo immediato | Microsoft Docs
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
- debug.quickwatch
helpviewer_keywords:
- Quick Watch command
- Debug.Quickwatch command
ms.assetid: 9670ac3a-8f2f-4874-974d-cb87d3b0cde1
caps.latest.revision: 18
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: afe27d567601e43b10323f9dcc3417bcf15e9298
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49269412"
---
# <a name="quick-watch-command"></a>Comando Controllo immediato
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
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
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md)



