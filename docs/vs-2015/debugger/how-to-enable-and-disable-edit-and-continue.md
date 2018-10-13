---
title: 'Procedura: abilitare e disabilitare Modifica e continuazione | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2700076fa0cc08aa137377b9a99c1179d9b8fc12
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49212829"
---
# <a name="how-to-enable-and-disable-edit-and-continue"></a>Procedura: abilitare e disabilitare Modifica e continuazione
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È possibile disabilitare o abilitare Modifica e continuazione nella **opzioni** finestra di dialogo in fase di progettazione. Non è possibile modificare questa impostazione durante il debug.  
  
 La funzionalità Modifica e continuazione può essere utilizzata solo nelle build di debug. Per il codice C++ nativo, la funzionalità Modifica e continuazione richiede l'utilizzo dell'opzione /INCREMENTAL.  
  
## <a name="procedures"></a>Procedure  
  
#### <a name="to-enabledisable-edit-and-continue"></a>Per abilitare o disabilitare Modifica e continuazione  
  
1.  Apri pagina delle opzioni di debug (**Strumenti / opzioni / debug**).  
  
2.  Scorrere verso il basso **modifica e continuazione** categoria.  
  
3.  Per abilitare, selezionare la **Abilita modifica e continuazione** casella di controllo. Per disabilitarla, deselezionare la casella di controllo.  
  
    > [!NOTE]
    >  Se IntelliTrace è abilitato e si raccolgono sia eventi IntelliTrace sia informazioni sulle chiamate, la funzionalità Modifica e continuazione viene disabilitata. Per altre informazioni, vedere [configurare IntelliTrace](http://msdn.microsoft.com/en-us/7657ecab-e07e-4b1b-872d-f05d966be37e).  
  
4.  Fare clic su **OK**.  
  
 Per altre informazioni su queste opzioni, vedere [generale, debug, finestra di dialogo Opzioni](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Modifica e continuazione](../debugger/edit-and-continue.md)



