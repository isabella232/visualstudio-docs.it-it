---
title: Estrai classe di base
description: Questo refactoring estrae i membri da una classe selezionata in una nuova classe di base.
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
ms.openlocfilehash: 9d7a21bbd3e51ee6a6776ca728a545cbbb731cab
ms.sourcegitcommit: 8590cf6b3351e82827fd21159beefef0c02bf162
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/08/2021
ms.locfileid: "102466277"
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
