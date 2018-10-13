---
title: Comando Percorso simboli | Microsoft Docs
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
- debug.symbolpath
helpviewer_keywords:
- symbol path command
- Debug.SymbolPath command
- SymbolPath command
ms.assetid: b697ef2d-3f5d-40df-b113-7068a5bec0d4
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 343b45f4a8aef0fdeef5aef7653a5dbb1c7c5582
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49189163"
---
# <a name="symbol-path-command"></a>Comando Percorso simboli
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

  
Imposta l'elenco delle directory in cui il debugger deve eseguire la ricerca dei simboli.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.SymbolPath pathname1;pathname2;... pathnameN  
```  
  
## <a name="arguments"></a>Argomenti  
 `pathname`  
 Facoltativo. Elenco di percorsi delimitato da punti e virgola usato dal debugger per la ricerca dei simboli.  
  
## <a name="remarks"></a>Note  
 Se non viene specificato un `pathname`, il comando elenca i percorsi dei simboli correnti.  
  
## <a name="example"></a>Esempio  
 In questo esempio vengono aggiunti due percorsi all'elenco delle directory dei simboli.  
  
```  
Debug.SymbolPath C:\Symbol Path 1;C:\Symbol Path 2  
```  
  
## <a name="example"></a>Esempio  
 In questo esempio viene visualizzato un elenco delimitato da punti e virgola dei percorsi dei simboli correnti.  
  
```  
Debug.SymbolPath  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Comandi di Visual Studio](../../ide/reference/visual-studio-commands.md)



