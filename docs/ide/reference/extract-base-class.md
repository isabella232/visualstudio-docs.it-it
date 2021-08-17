---
title: Estrai classe di base
description: Questo refactoring estrae i membri da una classe selezionata a una nuova classe di base.
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
ms.technology: vs-ide-general
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 15f6516b5114e7624babca567a65e7f041e4b56abe1090b4b98c1eb7d4d943d3
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121429530"
---
# <a name="extract-base-class"></a>Estrai classe di base

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Estrarre la classe di base.

**Quando:** Si desidera estrarre i membri da una classe selezionata in una nuova classe di base.

**Perché:** Il pull manuale dei membri può richiedere molto tempo e uscire dal flusso di lavoro. 

## <a name="how-to"></a>Procedure

1. Posizionare il punto di selezione sul nome della classe o su un membro evidenziato.

2. Premere  + **CTRL+ .** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare **Esegui pull dei membri fino alla nuova classe di base**.

    ![Finestra di dialogo Estrai classe di base](media/extract-base-class.png)

Verrà visualizzata la nuova finestra di dialogo **Estrai classe di base** in cui è possibile specificare il nome della classe di base e il percorso in cui deve essere inserita. È possibile selezionare i membri da trasferire alla nuova classe di base e scegliere di rendere astratti i membri selezionando la casella di controllo nella colonna Crea astratto.

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
