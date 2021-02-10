---
title: Estrai classe di base
ms.date: 11/03/2020
ms.topic: reference
author: mikadumont
ms.author: midumont
manager: jmartens
dev_langs:
- CSharp
- VB
ms.workload:
- dotnet
ms.openlocfilehash: 8c389ac6285b3f20dcdf05833f1ff3202d155c4f
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962808"
---
# <a name="extract-base-class"></a>Estrai classe di base

Questo refactoring si applica a:

- C#

- Visual Basic

**Cosa:** Estrae la classe di base.

**Quando:** Si desidera estrarre i membri da una classe selezionata in una nuova classe di base.

**Motivo:** Il pull manuale dei membri può richiedere molto tempo e uscire dal flusso di lavoro. 

## <a name="how-to"></a>Procedure

1. Posizionare il punto di inserimento sul nome della classe o su un membro evidenziato.

2. Premere **CTRL** + **.** per attivare il menu **Azioni rapide e refactoring**.

3. Selezionare **Esegui pull dei membri fino alla nuova classe di base**.

    ![Estrai finestra di dialogo classe di base](media/extract-base-class.png)

Verrà visualizzata la nuova finestra di dialogo **Estrai classe di base** in cui è possibile specificare il nome della classe di base e il percorso in cui deve essere inserita. È possibile selezionare i membri che si desidera trasferire alla nuova classe di base e scegliere di rendere i membri astratti selezionando la casella di controllo nella colonna crea abstract.

## <a name="see-also"></a>Vedi anche

- [Refactoring](../refactoring-in-visual-studio.md)
