---
title: Modificare la diagnostica grafica del computer di riproduzione
description: Riprodurre le informazioni grafiche da un log di grafica usando il computer locale o usando un computer remoto o un dispositivo che riproduce meglio il problema.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 1b9aa3ea-29a0-4e21-bc57-936f33537b5c
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 70ac7cbc1081e2c7a9a04c96393a5ac6af51cede
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133835"
---
# <a name="how-to-change-the-graphics-diagnostics-playback-machine"></a>Procedura: Modificare il computer di riproduzione della diagnostica della grafica
È possibile riprodurre le informazioni grafiche usando il computer locale o un computer o un dispositivo remoto.

## <a name="choosing-a-playback-machine"></a>Scelta di un computer di riproduzione
 Il computer di riproduzione è un computer o un dispositivo usato per riprodurre gli eventi grafici da un log di grafica. In genere, il computer locale è l'opzione più comoda, ma un problema di rendering potrebbe non essere riprodotto in un computer con versioni di hardware o driver diverse rispetto al computer in cui è stato acquisito. In questo caso, è possibile scegliere un computer di riproduzione remota che riproduce meglio il problema e usare comunque il computer di sviluppo per diagnosticarlo.

#### <a name="to-use-the-local-machine-to-play-back-graphics-information"></a>Per usare il computer locale per riprodurre le informazioni grafiche

1. Nella finestra del documento Log grafica scegliere il **collegamento Computer di** riproduzione. Verrà **visualizzata la finestra di** dialogo Connessioni debugger remoto .

2. In **Configurazione manuale** immettere nella proprietà **Indirizzo** `localhost` .

3. Impostare la **proprietà Modalità di** autenticazione su **Nessuno.**

4. Scegliere il pulsante **Seleziona**.

#### <a name="to-use-a-remote-machine-to-play-back-graphics-information"></a>Per usare un computer remoto per riprodurre le informazioni grafiche

1. Nella finestra del documento Log grafica scegliere il **collegamento Computer di** riproduzione. Verrà **visualizzata la finestra di** dialogo Connessioni debugger remoto .

2. In **Configurazione manuale,** nella proprietà **Indirizzo** immettere il Windows nome di dominio o l'indirizzo IP del computer o del dispositivo che si vuole usare per riprodurre le informazioni grafiche.

3. Specificare il tipo di autorizzazione da usare per proteggere la connessione al computer di riproduzione.

    - Per Windows authentication, impostare la **proprietà Authentication Mode** su **Windows**.

    - Per nessuna autenticazione, impostare la **proprietà Modalità** di autenticazione su **Nessuno.**

4. Scegliere il pulsante **Seleziona**.

> [!NOTE]
> La **finestra di dialogo Connessioni** debugger remoto potrebbe anche visualizzare destinazioni di debug remoto connesse direttamente al computer di sviluppo o che si trovano nella stessa subnet. È possibile usare una di queste destinazioni di debug remoto come Diagnostica della grafica di riproduzione senza configurarla manualmente. Nella finestra **di dialogo Connessioni debugger** remoto selezionare la destinazione desiderata e quindi scegliere il **pulsante** Seleziona.

## <a name="see-also"></a>Vedi anche
- [Documento log grafica](graphics-log-document.md)