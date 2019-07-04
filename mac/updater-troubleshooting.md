---
title: Errori durante il recupero di informazioni sugli aggiornamenti
description: Istruzioni su come risolvere il problema quando viene visualizzato l'errore 'Si è verificato un errore durante il recupero delle informazioni sugli aggiornamenti'. In Visual Studio 2019 per Mac
author: asb3993
ms.author: amburns
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 554633b2fc5d47d9cc4824ff9d8bf2febfbcd1f8
ms.sourcegitcommit: 16bcaca215de75479695738d3c2d703c78c3500e
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/21/2019
ms.locfileid: "67309634"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Risoluzione dei problemi: Errori durante il recupero di informazioni sugli aggiornamenti

In rare occasioni può essere visualizzato il messaggio di errore "Si è verificato un errore durante il recupero delle informazioni sugli aggiornamenti" quando si tenta di [aggiornare Visual Studio per Mac](update.md). In questo caso, provare i passaggi seguenti per risolvere il problema:

- Controllare la connessione Internet. Un'interruzione della connessione è la causa più comune di questo errore.
    - Se il download di un componente ha esito negativo, è possibile fare clic sul pulsante Riprova accanto al nome del componente per ritentare il download.
- Riavviare l'IDE.
- Se si continua a visualizzare questo messaggio di errore, è anche possibile provare a eseguire l'aggiornamento usando il programma di installazione, se il file con estensione **dmg** è ancora disponibile nel computer, oppure è possibile scaricarlo da [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/)
    - Il programma di installazione aggiornerà i componenti installati nel computer.
    - Eseguendo di nuovo il programma di installazione sarà anche possibile installare eventuali componenti mancanti, non installati in precedenza.
- È inoltre possibile provare a cancellare i download memorizzati nella cache eliminando il file che si trova in `~/Library/Caches/VisualStudio/7.0/TempDownload/index.xml`.