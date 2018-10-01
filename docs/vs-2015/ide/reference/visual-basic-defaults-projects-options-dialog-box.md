---
title: Impostazioni predefinite di Visual Basic, Progetti, finestra di dialogo Opzioni | Microsoft Docs
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
- VS.ToolsOptionsPages.Projects.VBDefaults
helpviewer_keywords:
- Option Explicit statement, setting in the IDE
- Option Compare statement, setting in the IDE
- Option Strict statement, setting in the IDE
ms.assetid: 2465cd9d-18b6-4c4a-b1ea-86dbab23fc79
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3370ecc8a80014f9d80152713140de7731bac058
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/22/2018
ms.locfileid: "47517811"
---
# <a name="visual-basic-defaults-projects-options-dialog-box"></a>Impostazioni predefinite di Visual Basic, Progetti, finestra di dialogo Opzioni
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versione più recente di questo argomento è reperibile in [Visual Basic per impostazione predefinita, i progetti, finestra di dialogo Opzioni](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box).  
  
  
Specifica le impostazioni predefinite per le opzioni dei progetti Visual Basic. Alla creazione di un nuovo progetto, le istruzioni specificate per le opzioni verranno aggiunte all'intestazione del progetto nell'editor di codice. Le opzioni si applicano a tutti i progetti Visual Basic.  
  
 Per accedere a questa finestra di dialogo, nel menu **Strumenti** fare clic su **Opzioni**, espandere la cartella **Progetti e soluzioni** e quindi fare clic su **Impostazioni predefinite di Visual Basic**.  
  
 **Option Explicit**  
 Imposta il valore predefinito del compilatore in modo da richiedere le dichiarazioni esplicite delle variabili. Per impostazione predefinita, **Option Explicit** è impostato su **On**. Per altre informazioni, vedere [/optionexplicit](http://msdn.microsoft.com/library/5d296ab3-bafe-4c4d-9887-78f162ed86c7).  
  
 **Option Strict**  
 Imposta il valore predefinito del compilatore in modo da richiedere le conversioni esplicite verso un tipo di dati più piccolo e da non consentire l'associazione tardiva. Per impostazione predefinita, **Option Strict** è impostato su **Off**. Per altre informazioni, vedere [/optionstrict](http://msdn.microsoft.com/library/c7b10086-0fa4-49db-b3c8-4ae0db5957da).  
  
 **Option Compare**  
 Imposta il valore predefinito del compilatore per il confronto di stringhe: binario (con distinzione tra maiuscole e minuscole) o basato sul testo (senza distinzione tra maiuscole e minuscole). Per impostazione predefinita, **Option Compare** è impostato su **Binary**. Per altre informazioni, vedere [/optioncompare](http://msdn.microsoft.com/library/7237b766-b44d-4cc5-9a3c-885348a7d9e4).  
  
 **Option Infer**  
 Imposta il valore predefinito del compilatore per l'inferenza del tipo di variabile locale. Per impostazione predefinita, **Option Infer** è impostato su **On** per i nuovi progetti e su **Off** per i progetti creati nelle versioni precedenti di Visual Basic dei quali è stata eseguita la migrazione. Per altre informazioni, vedere [/optioninfer](http://msdn.microsoft.com/library/f6c09db1-0553-464a-abe3-d4510c61d6ed).  
  
## <a name="see-also"></a>Vedere anche  
 [Solutions and Projects](../../ide/solutions-and-projects-in-visual-studio.md) (Soluzioni e progetti)



