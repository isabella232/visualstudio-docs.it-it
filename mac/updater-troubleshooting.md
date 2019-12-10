---
title: Errori durante il recupero di informazioni sugli aggiornamenti
description: Istruzioni su come risolvere il problema quando viene visualizzato l'errore 'Si è verificato un errore durante il recupero delle informazioni sugli aggiornamenti'. In Visual Studio 2019 per Mac
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: b25285ff3060734ee18085d7a9e89cd0d0c43439
ms.sourcegitcommit: 370cc7fd2e11ede6d8215c8d81963a8307614550
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/10/2019
ms.locfileid: "74984413"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Risoluzione dei problemi: l'aggiornamento contiene errori durante il recupero delle informazioni

In rare occasioni può essere visualizzato il messaggio di errore "Si è verificato un errore durante il recupero delle informazioni sugli aggiornamenti" quando si tenta di [aggiornare Visual Studio per Mac](update.md). In questo caso, provare i passaggi seguenti per risolvere il problema:

- Controllare la connessione Internet. Un'interruzione della connessione è la causa più comune di questo errore.
  - Se il download di un componente ha esito negativo, è possibile fare clic sul pulsante Riprova accanto al nome del componente per ritentare il download.
- Riavviare l'IDE.
- Se si continua a visualizzare questo messaggio di errore, è anche possibile provare a eseguire l'aggiornamento usando il programma di installazione, se il file con estensione **dmg** è ancora disponibile nel computer, oppure è possibile scaricarlo da [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/)
  - Il programma di installazione aggiornerà i componenti installati nel computer.
  - Eseguendo di nuovo il programma di installazione sarà anche possibile installare eventuali componenti mancanti, non installati in precedenza.
- È inoltre possibile provare a cancellare i download memorizzati nella cache eliminando il file che si trova in `~/Library/Caches/VisualStudio/7.0/TempDownload/index.xml`.
