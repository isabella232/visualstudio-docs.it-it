---
title: Visualizzare i valori dei registri nel debugger | Microsoft Docs
description: Visualizzare i valori dei registri nella finestra Registri in Visual Studio. Durante il debug, i valori di registrazione cambiano quando il codice viene eseguito nell'app.
ms.custom: SEO-VS-2020
ms.date: 11/19/2018
ms.topic: how-to
f1_keywords:
- vs.debug.registers
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- registers, debugging
- register contents
- flags, Registers window
- register groups
- debugging [Visual Studio], Registers window
- Registers window
ms.assetid: 2918ffa2-562f-40d6-9053-ef321bbeb767
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 94048bef497f21a77e3e94d583f26d65ceef53553725195ea1100ab5313b9887
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121453240"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Visualizzare i valori dei registri nella finestra Registri (C#, C++, Visual Basic, F#)

La **finestra Registri visualizza** il contenuto del registro durante Visual Studio debug. Per un'introduzione generale ai concetti alla base di registri e i **registra** finestra, vedere [nozioni fondamentali di debug: Finestra Registri](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Le informazioni di registrazione non sono disponibili per le app SQL script.

Durante il debug, i valori di registrazione cambiano quando il codice viene eseguito nell'app. I valori modificati di recente vengono visualizzati in rosso nella **finestra** Registri.

Per evitare confusione, nella finestra **Registri** i registri sono organizzati in gruppi che variano secondo la piattaforma e il tipo di processore. È possibile visualizzare o nascondere i gruppi di registri. Per altre informazioni, vedere [Procedura: Visualizzare e nascondere gruppi di registri](../debugger/how-to-display-and-hide-register-groups.md).

Per informazioni sui flag visualizzati nella finestra **Registri,** vedere [Informazioni sulla finestra Registri](../debugger/debugging-basics-registers-window.md)

È possibile modificare i valori dei registri. Per altre informazioni, vedere [Procedura: Modificare un valore di registro.](../debugger/how-to-edit-a-register-value.md)

**Per aprire la finestra Registri**

1. Abilitare il debug a livello di indirizzo selezionando Abilita debug a livello di indirizzo **in** Strumenti **(o** Debug **)**> **Opzioni**  >  **di debug**.

1. Durante l'esecuzione del debug o in corrispondenza di un punto di interruzione,  >  **selezionare Debug Windows**  >  **Registra** oppure premere **ALT** + **5.**

>[!NOTE]
>Le finestre di dialogo e i comandi di menu possono variare a seconda dell Visual Studio o delle impostazioni. Per modificare le impostazioni, scegliere **Importa/Esporta Impostazioni** dal **menu** Visual Studio Strumenti. Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Vedi anche

- [Nozioni di base sul debug: finestra Registri](../debugger/debugging-basics-registers-window.md)
- [Visualizzazione dei dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
