---
title: Visualizza i valori del registro nel debugger | Microsoft Docs
ms.custom: seodec18
ms.date: 11/19/2018
ms.topic: conceptual
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
ms.openlocfilehash: afcada407060af2072e3cf1c30e86153762890b5
ms.sourcegitcommit: 847d192013eb8225776243045c9b5a53d1ba4a59
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/15/2019
ms.locfileid: "59584389"
---
# <a name="view-register-values-in-the-registers-window-c-c-visual-basic-f"></a>Visualizza i valori del registro nella finestra di registri (C#, C++, Visual Basic, F#)

Il **registra** finestra consente di visualizzare il contenuto del registro durante il debug di Visual Studio. Per un'introduzione generale ai concetti alla base di registri e i **registra** finestra, vedere [nozioni fondamentali di debug: Finestra Registri](../debugger/debugging-basics-registers-window.md).

> [!NOTE]
> Informazioni di registro non sono disponibile per App SQL o script.

Durante il debug, registrare valori modifica durante l'esecuzione di codice nell'app. I valori che sono stati modificati di recente vengono visualizzati in rosso nel **registra** finestra.

Per evitare confusione, nella finestra **Registri** i registri sono organizzati in gruppi che variano secondo la piattaforma e il tipo di processore. È possibile visualizzare o nascondere i gruppi di registri. Per altre informazioni, vedere [Procedura: Visualizzare e nascondere gruppi di registri](../debugger/how-to-display-and-hide-register-groups.md).

Per informazioni sui flag presenti il **registra** finestra, vedere [finestra di registri](../debugger/debugging-basics-registers-window.md)

È possibile modificare i valori dei registri. Per altre informazioni, vedere [Procedura: Modificare un valore di registro](../debugger/how-to-edit-a-register-value.md).

**Per aprire la finestra registri**

1. Abilita debug a livello di indirizzo, selezionando **abilitare il debug a livello di indirizzo** in **Tools** (o **Debug**) > **opzioni**  >  **Debug**.

1. Durante il debug è in esecuzione o in un punto di interruzione, selezionare **Debug** > **Windows** > **registra**, o premere **Alt** + **5**.

>[!NOTE]
>Finestre di dialogo e comandi di menu potrebbe essere diverso a seconda dell'edizione di Visual Studio o le impostazioni. Per modificare le impostazioni, selezionare **Importa / Esporta impostazioni** in Visual Studio **Tools** menu. Per altre informazioni, vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

### <a name="see-also"></a>Vedere anche

- [Informazioni di base sul debug: Finestra Registri](../debugger/debugging-basics-registers-window.md)
- [Visualizzazione di dati nel debugger](../debugger/viewing-data-in-the-debugger.md)
