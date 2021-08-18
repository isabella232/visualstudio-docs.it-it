---
title: Convalida dei frame di grafica | Microsoft Docs
description: Informazioni sullo strumento di convalida dei frame per la grafica in Visual Studio. Questo strumento visualizza gli errori e gli avvisi associati all'elenco di eventi.
ms.custom: SEO-VS-2020
ms.date: 03/02/2017
ms.topic: conceptual
f1_keywords:
- vs.graphics.FrameValidation
ms.assetid: 1e639182-1301-4e28-9c1e-b5df732f3f1b
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 1573b19318e86f5c7cdff796756b476728ce42ba
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122058597"
---
# <a name="graphics-frame-validation"></a>Convalida dei frame di grafica
<!-- VERSIONLESS -->
Visual Studio 2017 e versione successiva supportano lo **strumento di convalida dei** frame.  Nella finestra Convalida frame vengono visualizzati gli errori e gli avvisi associati all'elenco di eventi.  Per visualizzare questa finestra, selezionare il menu **Visualizza > Convalida frame.**

![Convalida frame](media/gfx_diag_frame_validation.png)

Fare clic **sul pulsante Esegui** convalida nell'angolo superiore sinistro per avviare l'analisi.  Il completamento può richiedere alcuni minuti a seconda della complessità del frame.  I dati visualizzati qui sono una combinazione di due origini: i messaggi generati da D3D quando sono abilitati i livelli [SDK](/windows/desktop/direct3d11/overviews-direct3d-11-devices-layers) e i dati raccolti dal rilevamento dello stato interno dello strumento. Al termine, verranno visualizzate diverse colonne di dati:

| **Colonna** | **Descrizione** |
|------------| - |
| ID evento | ID che esegue il mapping a una voce nella [finestra Elenco](graphics-event-list.md) eventi. |
| Gravità | Danneggiamento, Errore, Avviso, Informazioni o Messaggio. |
| Category | Definito dall'applicazione, Varie, Inizializzazione, Pulizia, Compilazione, Creazione stato, Impostazione stato, Recupero stato, Esecuzione, Manipolazione delle risorse, Shader, Ridondante e Inutilizzato. |
| Message | Messaggio associato all'evento. |
| Event | Evento associato all'errore o all'avviso. |

## <a name="see-also"></a>Vedi anche
[Diagnostica della grafica (Debug grafica DirectX)](visual-studio-graphics-diagnostics.md)
<!-- /VERSIONLESS -->