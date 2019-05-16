---
title: 'Procedura: Abilitare e disabilitare Modifica e continuazione | Microsoft Docs'
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
- /INCREMENTAL linker option
- Apply Code Changes command
- Edit and Continue, disabling
- code changes, applying in break mode
- INCREMENTAL linker option
- Edit and Continue, enabling
- break mode, applying code changes
- Edit and Continue, applying code changes
- Step command
- Go command
ms.assetid: fd961a1c-76fa-420d-ad8f-c1a6c003b0db
caps.latest.revision: 29
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 70914da9be4046589a0ca3b8e5fd4ae13210ca51
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/15/2019
ms.locfileid: "65689268"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Procedura: Abilitare e disabilitare Modifica e continuazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile disabilitare o abilitare Modifica e continuazione nella **opzioni** finestra di dialogo in fase di progettazione. Non è possibile modificare questa impostazione durante il debug.  
  
 La funzionalità Modifica e continuazione può essere utilizzata solo nelle build di debug. Per il codice C++ nativo, la funzionalità Modifica e continuazione richiede l'utilizzo dell'opzione /INCREMENTAL.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Per abilitare o disabilitare Modifica e continuazione  
  
1. Apri pagina delle opzioni di debug (**Strumenti / opzioni / debug**).  
  
2. Scorrere verso il basso **modifica e continuazione** categoria.  
  
3. Per abilitare, selezionare la **Abilita modifica e continuazione** casella di controllo. Per disabilitarla, deselezionare la casella di controllo.  
  
   > [!NOTE]
   > Se IntelliTrace è abilitato e si raccolgono sia eventi IntelliTrace sia informazioni sulle chiamate, la funzionalità Modifica e continuazione viene disabilitata. Per altre informazioni, vedere [configurare IntelliTrace](https://msdn.microsoft.com/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4. Fare clic su **OK**.  
  
   Per altre informazioni su queste opzioni, vedere [generale, debug, finestra di dialogo Opzioni](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica e continuazione](../debugger/edit-and-continue.md)
