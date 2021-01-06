---
title: Visualizzare e nascondere i gruppi di registri | Microsoft Docs
description: La finestra registri, disponibile se il debug a livello di indirizzo è abilitato, organizza i registri nei gruppi. Informazioni su come impostare i gruppi da visualizzare.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.registergroups
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- Registers window, displaying and hiding register groups
- register groups, displaying and hiding
ms.assetid: 6be5dfb4-4cfe-4daf-b538-60405640857d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c14d325d417606c6945d51d99461d34ccd9a4bc8
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903038"
---
# <a name="how-to-display-and-hide-register-groups-c-c-visual-basic-f"></a>Procedura: visualizzare e nascondere gruppi di registri (C#, C++, Visual Basic, F #)

La finestra **Registri** è disponibile solo se il debug a livello di indirizzo è stato attivato nel nodo **Debug** della categoria **Generale** nella finestra di dialogo **Opzioni**.

Per evitare confusione, nella finestra **Registri** i registri sono organizzati in gruppi. Facendo clic con il pulsante destro del mouse sulla finestra **Registri** verrà visualizzato un menu di scelta rapida contenente tali gruppi, che è possibile visualizzare o nascondere secondo necessità seguendo la procedura riportata di seguito.

> [!NOTE]
> È possibile che le finestre di dialogo e i comandi di menu visualizzati varino da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere **Importa/Esporta impostazioni** dal menu **Strumenti** . Per altre informazioni vedere [Reimpostare le impostazioni](../ide/environment-settings.md#reset-settings).

## <a name="display-or-hide-register-groups"></a>Visualizzare o nascondere i gruppi di registri

1. Fare clic con il pulsante destro del mouse sulla finestra **Registri**.

2. Scegliere i gruppi di registri da visualizzare o nascondere dal menu di scelta rapida.

     I gruppi di registri non supportati dall'hardware per il quale si sta eseguendo il debug sono disabilitati nel menu di scelta rapida e non possono essere selezionati.

## <a name="see-also"></a>Vedere anche

- [Procedura: utilizzare la finestra Registri](../debugger/how-to-use-the-registers-window.md)