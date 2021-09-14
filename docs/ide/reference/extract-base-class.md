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
ms.openlocfilehash: c3dec3fb8f00f763ea898b17e97c3714c75bfddb
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126710237"
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
