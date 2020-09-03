---
title: Convalida di fotogrammi grafici | Microsoft Docs
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 49248c6209f9e56e51551f6cd3d4af66ecac8b56
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "72735492"
---
# <a name="graphics-frame-validation"></a>Convalida di frame grafica
<!-- VERSIONLESS -->
Visual Studio 2017 e versioni successive supportano lo strumento di **convalida dei frame** .  La finestra di convalida dei frame Visualizza gli errori e gli avvisi associati all'elenco di eventi.  Per visualizzare questa finestra, selezionare il menu **visualizza > convalida frame** .

![Convalida frame](media/gfx_diag_frame_validation.png)

Fare clic sul pulsante **Esegui convalida** nell'angolo superiore sinistro per avviare l'analisi.  Il completamento dell'operazione potrebbe richiedere alcuni minuti, a seconda della complessità del frame.  I dati visualizzati qui sono una combinazione di due origini: i messaggi che D3D emette quando sono abilitati i [livelli SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) e i dati raccolti dal rilevamento dello stato interno dello strumento. Al termine, vengono visualizzate diverse colonne di dati:

| **Colonna** | **Descrizione** |
|------------| - |
| ID evento | ID che esegue il mapping a una voce nella finestra [elenco eventi](graphics-event-list.md) . |
| Gravità | Danneggiamento, errore, avviso, informazioni o messaggio. |
| Category | Applicazione definita, varie, inizializzazione, pulizia, compilazione, creazione dello stato, impostazione dello stato, recupero dello stato, esecuzione, manipolazione delle risorse, shader, ridondante e non usata. |
| Message | Messaggio associato all'evento. |
| Event | Evento associato all'errore o all'avviso. |

## <a name="see-also"></a>Vedere anche
[Diagnostica della grafica (Debug grafica DirectX)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->