---
title: Comando Percorso simboli | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
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
manager: jillfra
ms.openlocfilehash: 27c4c8ac23e2524245107d9052642350e9db09d2
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670397"
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
  
## <a name="remarks"></a>Osservazioni  
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
