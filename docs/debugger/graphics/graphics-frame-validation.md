---
title: Convalida dei Frame di grafica | Microsoft Docs
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
ms.openlocfilehash: ce283e5cbab30b612a02ec447113ad11e206a7f3
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/17/2019
ms.locfileid: "59655374"
---
# <a name="graphics-frame-validation"></a>Convalida Frame di grafica
<!-- VERSIONLESS -->
Visual Studio 2017 e il supporto maggiore di **convalida Frame** dello strumento.  Consente di visualizzare la finestra di convalida Frame errori e avvisi associati con l'elenco di eventi.  Per visualizzare questa finestra, selezionare la **Visualizza > convalida Frame** menu.

![Convalida frame](media/gfx_diag_frame_validation.png)

Scegliere il **Esegui convalida** pulsante nell'angolo superiore sinistro per avviare l'analisi.  Potrebbero occorrere alcuni minuti a seconda della complessità del frame.  I dati che viene visualizzata di seguito è una combinazione di due origini: i messaggi di tale D3D se stessa quando emette [livelli SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) è abilitata e i dati raccolti dallo stato interno dello strumento di rilevamento. Al termine dell'operazione, si noterà diverse colonne di dati:

| **Colonna** | **Descrizione** |
|------------| - |
| ID evento | ID che viene eseguito il mapping a una voce nella [elenco eventi](graphics-event-list.md) finestra. |
| Gravità | Danneggiamento, errore, avviso, informazioni o messaggio. |
| Category | Applicazione esterni, definita, l'inizializzazione, pulizia, compilazione, creazione stato, impostazione dello stato, recupero dello stato, l'esecuzione, modifica delle risorse, Shader, ridondanti e inutilizzate. |
| Messaggio | Il messaggio associato all'evento. |
| event | L'evento associato all'errore o avviso. |

## <a name="see-also"></a>Vedere anche
[Diagnostica della grafica (debug della grafica DirectX)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->