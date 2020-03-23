---
title: Errori durante il recupero di informazioni sugli aggiornamenti
description: Istruzioni su come risolvere il problema quando viene visualizzato l'errore 'Si è verificato un errore durante il recupero delle informazioni sugli aggiornamenti'. In Visual Studio 2017 per Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 8825BBAD-65C0-480F-9868-A01E64F28250
ms.openlocfilehash: 2ff0703171f5854baed2dd9be3767571a930bcb7
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "74983487"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Risoluzione dei problemi: Updater ha errori durante il recupero delle informazioni

In rare occasioni può essere visualizzato il messaggio di errore "Si è verificato un errore durante il recupero delle informazioni sugli aggiornamenti" quando si tenta di [aggiornare Visual Studio per Mac](update.md). In questo caso, provare i passaggi seguenti per risolvere il problema:

- Verificare la connessione Internet. Un'interruzione della connessione è la causa più comune di questo errore.
  - Se il download di un componente ha esito negativo, è possibile fare clic sul pulsante Riprova accanto al nome del componente per ritentare il download.
- Riavviare l'IDE.
- Se si continua a visualizzare questo messaggio di errore, è anche possibile provare a eseguire l'aggiornamento usando il programma di installazione di Visual Studio 2017 per Mac, se il file con estensione **dmg** è ancora disponibile nel computer, oppure è possibile scaricarlo da [my.visualstudio.com](https://my.visualstudio.com/Downloads?q=Visual%20Studio%20for%20Mac)
  - Il programma di installazione aggiornerà i componenti installati nel computer.
  - Eseguendo di nuovo il programma di installazione sarà anche possibile installare eventuali componenti mancanti, non installati in precedenza.
