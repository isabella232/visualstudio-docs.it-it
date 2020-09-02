---
title: 'Procedura: uscire da codice gestito quando nella finestra stack di chiamate mancano frame nativi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- SQL
- VB
- CSharp
- C++
helpviewer_keywords:
- Call Stack window, missing native frames
- code, managed code
- native frames
- stepping, out of managed code
- managed code, stepping out of
ms.assetid: 97cdd2a8-02a9-4a06-a5b1-c92b1e431979
caps.latest.revision: 24
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 63bd55fd254dd263540a9161e8579ea6600e97f1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "65690095"
---
# <a name="how-to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-window"></a>Procedura: uscire da codice gestito quando nella finestra Stack di chiamate non sono visualizzati frame nativi
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Se il codice contiene frame nativi non visibili nella finestra **Stack di chiamate**, l'uscita dal codice gestito può produrre risultati imprevisti. Una soluzione possibile consiste nell'utilizzare un punto di interruzione invece del comando **Esci da istruzione/routine**.  
  
> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni, vedere [personalizzazione delle impostazioni di sviluppo in Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-step-out-of-managed-code-when-native-frames-are-missing-from-the-call-stack-display"></a>Per uscire da codice gestito quando nella visualizzazione dello stack di chiamate non sono visualizzati frame nativi  
  
1. Nel codice nativo impostare un punto di interruzione di posizione dopo la chiamata a codice gestito.  
  
2. Scegliere **Continua** dal menu **Debug**.  
  
     Una volta completata la chiamata gestita, l'esecuzione si interromperà in corrispondenza del punto di interruzione nel codice nativo.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: utilizzare la finestra Stack di chiamate](../debugger/how-to-use-the-call-stack-window.md)
