---
title: Errori durante il recupero di informazioni sugli aggiornamenti
description: Istruzioni su come risolvere il problema quando viene visualizzato l'errore 'Si è verificato un errore durante il recupero delle informazioni sugli aggiornamenti'. In Visual Studio 2019 per Mac
ms.topic: troubleshooting
author: heiligerdankgesang
ms.author: dominicn
ms.date: 04/13/2019
ms.technology: vs-ide-install
ms.assetid: 31AF914A-C66B-4CD3-9429-39695E0E94AE
ms.openlocfilehash: 2ccef07a2889f66df3e7f217ea292b61ffc0008f
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/09/2021
ms.locfileid: "123964264"
---
# <a name="troubleshooting-updater-has-errors-retrieving-information"></a>Risoluzione dei problemi: Errori durante il recupero di informazioni sugli aggiornamenti

In rare occasioni può essere visualizzato il messaggio di errore "Si è verificato un errore durante il recupero delle informazioni sugli aggiornamenti" quando si tenta di [aggiornare Visual Studio per Mac](update.md). In questo caso, provare i passaggi seguenti per risolvere il problema:

- Verificare la connessione Internet. Un'interruzione della connessione è la causa più comune di questo errore.
  - Se il download di un componente ha esito negativo, è possibile fare clic sul pulsante Riprova accanto al nome del componente per ritentare il download.
- Riavviare l'IDE.
- Se si continua a visualizzare questo messaggio di errore, è anche possibile provare a eseguire l'aggiornamento usando il programma di installazione, se il file con estensione **dmg** è ancora disponibile nel computer, oppure è possibile scaricarlo da [visualstudio.com](https://visualstudio.microsoft.com/vs/mac/)
  - Il programma di installazione aggiornerà i componenti installati nel computer.
  - Eseguendo di nuovo il programma di installazione sarà anche possibile installare eventuali componenti mancanti, non installati in precedenza.
- È inoltre possibile provare a cancellare i download memorizzati nella cache eliminando il file che si trova in `~/Library/Caches/VisualStudio/8.0/TempDownload/index.xml`.
- Se si lavora con una versione precedente di Visual Studio per Mac, è possibile che nella directory ci sono altri numeri di `VisualStudio` versione. Eliminare anche `index.xml` il file in questi percorsi.
