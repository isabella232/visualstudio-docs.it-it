---
title: Visualizzare i valori di registro nel debugger | Microsoft Docs
description: Visualizzare i valori di registrazione nella finestra registri in Visual Studio. Durante il debug, i valori di registrazione cambiano in base all'esecuzione del codice nell'app.
ms.custom: SEO-VS-2020, seodec18
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8422738b5c46b5482ac65cd24ccc903acdb4506e
ms.sourcegitcommit: 957da60a881469d9001df1f4ba3ef01388109c86
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/13/2021
ms.locfileid: "98148039"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Visualizzare i valori di registrazione nella finestra registri (C#, C++, Visual Basic, F #)

La finestra **registri** Visualizza il contenuto del registro durante il debug di Visual Studio. Per un'introduzione generale ai concetti alla base di registri e i **registra** finestra, vedere [nozioni fondamentali di debug: Finestra Registri](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Le informazioni di registrazione non sono disponibili per le app script o SQL.

Durante il debug, i valori di registrazione cambiano in base all'esecuzione del codice nell'app. I valori che sono stati modificati di recente vengono visualizzati in rosso nella finestra **registri** .

Per evitare confusione, nella finestra **Registri** i registri sono organizzati in gruppi che variano secondo la piattaforma e il tipo di processore. È possibile visualizzare o nascondere i gruppi di registri. Per altre informazioni, vedere [Procedura: Visualizzare e nascondere gruppi di registri](../debugger/how-to-display-and-hide-register-groups.md).

Per informazioni sui flag visualizzati nella finestra **registri** , vedere [informazioni sulla finestra registri](../debugger/debugging-basics-registers-window.md)

È possibile modificare i valori dei registri. Per altre informazioni, vedere [procedura: modificare un valore di registro](../debugger/how-to-edit-a-register-value.md).

**Per aprire la finestra registri**

1. Abilitare il debug a livello di indirizzo selezionando **Abilita debug a livello di indirizzo** in **strumenti** (o **debug**) > **Opzioni**  >  **debug**.

1. Durante il debug è in esecuzione o in un punto di interruzione, selezionare **Esegui il debug** di  >    >  **registri** di Windows oppure premere **ALT** + **5**.

>[!NOTE]
>Le finestre di dialogo e i comandi di menu potrebbero variare a seconda dell'edizione o delle impostazioni di Visual Studio. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **strumenti** di Visual Studio. Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Vedere anche

- [Nozioni fondamentali di debug: finestra registri](../debugger/debugging-basics-registers-window.md)
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
