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
ms.openlocfilehash: 3a2f7f1817b562b555a8ac026e165712bb81f912
ms.sourcegitcommit: 935e341a02dba1c2aa3b6e89469388aa6e626f7f
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/20/2018
ms.locfileid: "53684730"
---
# <a name="stale-code-warning-dialog-box"></a>Avviso di codice non aggiornato (finestra di dialogo)

Questa finestra di dialogo viene visualizzata quando vengono apportate modifiche al codice nativo che la modalità **Modifica e continuazione** non può applicare immediatamente. Di conseguenza, il codice nativo nello stack frame corrente non sarà più aggiornato. Per altre informazioni, vedere [Modifica e continuazione (C++)](edit-and-continue-visual-cpp.md).

**Non visualizzare più questo messaggio**

Se si seleziona questa casella di controllo, la modalità Modifica e continuazione applicherà le modifiche al codice senza chiedere l'autorizzazione. Per riattivare questo messaggio di avviso, accedere alla finestra di dialogo **Opzioni**, aprire la cartella **Debug**, fare clic sulla pagina **Modifica e continuazione** e selezionare **Avvisa in caso di codice non aggiornato**.

## <a name="see-also"></a>Vedere anche

- [Modifiche al codice supportate (C++)](supported-code-changes-cpp.md)
- [Modifica e continuazione, Debug, finestra di dialogo Opzioni](edit-and-continue.md)