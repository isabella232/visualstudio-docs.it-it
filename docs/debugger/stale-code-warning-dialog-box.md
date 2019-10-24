---
title: Finestra di dialogo avviso di codice non aggiornato | Microsoft Docs
ms.date: 11/04/2016
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dba38e5b5d9f7a2be710cad58d6f2297dd03a412
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/22/2019
ms.locfileid: "72729538"
---
# <a name="stale-code-warning-dialog-box"></a>Avviso di codice non aggiornato (finestra di dialogo)

Questa finestra di dialogo viene visualizzata quando vengono apportate modifiche al codice nativo che la modalità **Modifica e continuazione** non può applicare immediatamente. Di conseguenza, il codice nativo nello stack frame corrente non sarà più aggiornato. Per altre informazioni, vedere [Modifica e continuazione (C++)](edit-and-continue-visual-cpp.md).

**Non visualizzare più questo messaggio**

Se si seleziona questa casella di controllo, la modalità Modifica e continuazione applicherà le modifiche al codice senza chiedere l'autorizzazione. Per riattivare questo messaggio di avviso, accedere alla finestra di dialogo **Opzioni**, aprire la cartella **Debug**, fare clic sulla pagina **Modifica e continuazione** e selezionare **Avvisa in caso di codice non aggiornato**.

## <a name="see-also"></a>Vedere anche

- [Modifiche al codice supportate (C++)](supported-code-changes-cpp.md)
- [Modifica e continuazione, Debug, finestra di dialogo Opzioni](edit-and-continue.md)