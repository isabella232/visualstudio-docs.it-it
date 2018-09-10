---
title: Non aggiornate di finestra di dialogo Avviso di codice | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.ENC.stalecode
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- Stale Code Warning dialog box
- code, stale code warning
- warnings, Stale Code Warning dialog box
- Edit and Continue, stale code
ms.assetid: 594b894c-e652-4e13-a980-9909473d5712
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: f1e212602b317127cfd14adcd246a23cdd92ed86
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44281793"
---
# <a name="stale-code-warning-dialog-box"></a>Avviso di codice non aggiornato (finestra di dialogo)
Questa finestra di dialogo viene visualizzata quando sono state apportate modifiche al codice nativo che **modifica e continuazione** non può applicare immediatamente. Di conseguenza, il codice nativo nello stack frame corrente non sarà più aggiornato. Per altre informazioni, vedere [procedura: utilizzare codice non aggiornato](/visualstudio/debugger/edit-and-continue-visual-cpp#bkmk_how_to_work_with_stale_code).  
  
 **Non visualizzare più questa finestra di dialogo**  
 Se si seleziona questa casella di controllo, la modalità Modifica e continuazione applicherà le modifiche al codice senza chiedere l'autorizzazione. È possibile attivare questo avviso anche in questo caso passando al **opzioni** finestra di dialogo, aprire il **debug** cartella, fare clic sui **modifica e continuazione** , quindi selezionare **Avvisa in codice non aggiornato**.  
  
## <a name="see-also"></a>Vedere anche  
 [Modifiche al codice supportate (C++)](../debugger/supported-code-changes-cpp.md)   
 [Modifica e continuazione, Debug, finestra di dialogo Opzioni](/visualstudio/debugger/edit-and-continue)