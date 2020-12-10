---
title: Modificare il computer di riproduzione della diagnostica grafica
description: Riprodurre le informazioni grafiche da un log di grafica usando il computer locale o usando un computer o un dispositivo remoto che riproduce meglio il problema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8b6ae19fde7397b97ebe087557d71a52303605ec
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2020
ms.locfileid: "96995070"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Procedura: Modificare il computer di riproduzione della diagnostica della grafica
È possibile riprodurre le informazioni grafiche usando il computer locale o un computer o un dispositivo remoto.

## <a name="choosing-a-playback-machine"></a>Scelta di un computer di riproduzione
 Il computer di riproduzione è un computer o un dispositivo usato per riprodurre gli eventi di grafica da un log di grafica. In genere, il computer locale è l'opzione più semplice, ma un problema di rendering potrebbe non riprodursi in un computer con versioni hardware o driver diverse da quelle del computer in cui è stato acquisito. Quando si verifica questa situazione, è possibile scegliere un computer di riproduzione remoto che riproduca meglio il problema e continuare a usare il computer di sviluppo per diagnosticarlo.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Per utilizzare il computer locale per riprodurre le informazioni grafiche

1. Nella finestra del documento del log di grafica scegliere il collegamento **computer riproduzione** . Verrà visualizzata la finestra di dialogo **Connessioni debugger remoto** .

2. In **configurazione manuale**, nella proprietà **Indirizzo** , immettere `localhost` .

3. Impostare la proprietà **modalità di autenticazione** su **Nessuna**.

4. Scegliere il pulsante **Seleziona**.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Per utilizzare un computer remoto per riprodurre le informazioni grafiche

1. Nella finestra del documento del log di grafica scegliere il collegamento **computer riproduzione** . Verrà visualizzata la finestra di dialogo **Connessioni debugger remoto** .

2. In **configurazione manuale**, nella proprietà **Indirizzo** , immettere il nome di dominio Windows o l'indirizzo IP del computer o del dispositivo che si desidera utilizzare per riprodurre le informazioni grafiche.

3. Specificare il tipo di autorizzazione che si desidera utilizzare per proteggere la connessione al computer di riproduzione.

    - Per l'autenticazione di Windows, impostare la proprietà **modalità di autenticazione** su **Windows**.

    - Per nessuna autenticazione, impostare la proprietà **modalità di autenticazione** su **Nessuna**.

4. Scegliere il pulsante **Seleziona**.

> [!NOTE]
> Nella finestra di dialogo **Connessioni debugger remoto** è possibile che vengano visualizzate anche le destinazioni di debug remoto direttamente connesse al computer di sviluppo o che si trovano nella stessa subnet. È possibile usare una di queste destinazioni di debug remoto come Diagnostica della grafica computer di riproduzione senza configurarlo manualmente. Nella finestra di dialogo **Connessioni debugger remoto** selezionare la destinazione desiderata, quindi scegliere il pulsante **Seleziona** .

## <a name="see-also"></a>Vedere anche
- [Documento log grafica](graphics-log-document.md)