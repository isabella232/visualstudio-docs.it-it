---
title: Applicazioni Server SDI | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- SDI server applications
- SDI server applications, debugging
ms.assetid: 09713718-1376-4753-b119-26f36639693e
caps.latest.revision: 18
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1296c0f43d0409df0081861095c5ec068932bbc1
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "58966657"
---
# <a name="sdi-server-applications"></a>Applicazioni server SDI
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se si esegue il debug di un'applicazione server SDI, è necessario specificare `/Embedding` o `/Automation` nella proprietà **Argomenti della riga di comando** disponibile nella finestra di dialogo Pagine delle proprietà di *Progetto* per i progetti C/C++, C# o Visual Basic.  
  
 Grazie a questi argomenti della riga di comando, il debugger è in grado di avviare l'applicazione server come se tale avvio venisse eseguito da un contenitore. In seguito all'avvio del contenitore da Program Manager o File Manager, il contenitore utilizzerà l'istanza del server già avviata dal debugger.  
  
## <a name="finding-the-command-line-arguments-property"></a>Ricerca della proprietà Argomenti della riga di comando  
 Per accedere alla finestra di dialogo Pagine delle proprietà di *Progetto*, fare clic con il pulsante destro del mouse sul progetto in Esplora soluzioni e scegliere Proprietà dal menu di scelta rapida. Per individuare la proprietà Argomenti della riga di comando, espandere la categoria Proprietà di configurazione e fare clic sulla pagina Debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Debug di COM e ActiveX](../debugger/com-and-activex-debugging.md)   
 [Procedura: Eseguire il debug di server COM](../debugger/how-to-debug-com-servers.md)
