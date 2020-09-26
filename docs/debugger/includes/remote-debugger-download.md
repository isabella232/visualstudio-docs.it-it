---
title: Download del debugger remoto
description: Collegamenti per il download del debugger remoto
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 86bc2a1b73b492dc5f8d9977f05c3b2ba0dde6dc
ms.sourcegitcommit: 13cf7569f62c746708a6ced1187d8173eda7397c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/25/2020
ms.locfileid: "91377563"
---
Sul dispositivo remoto o sul server su cui si vuole eseguire il debug, anziché sul computer che esegue Visual Studio, scaricare e installare la versione corretta di Remote Tools dai collegamenti nella tabella seguente.

- Scaricare gli strumenti remoti più recenti per la versione di Visual Studio. La versione più recente di Remote Tools è compatibile con le versioni precedenti di Visual Studio, ma le versioni precedenti degli strumenti remoti non sono compatibili con le versioni successive di Visual Studio. (Ad esempio, se si usa Visual Studio 2017, scaricare l'aggiornamento più recente di Remote Tools per Visual Studio 2017. In questo scenario, non scaricare Remote Tools per Visual Studio 2019.
- Scaricare gli strumenti remoti con la stessa architettura del computer in cui vengono installati. Se ad esempio si vuole eseguire il debug di un'app a 32 bit in un computer remoto che esegue un sistema operativo a 64 bit, installare gli strumenti remoti a 64 bit.

::: moniker range=">=vs-2019"

|Versione|Collegamento|Note|
|-|-|-|
|Visual Studio 2019|[Strumenti remoti](https://visualstudio.microsoft.com/downloads#remote-tools-for-visual-studio-2019)|Compatibile con tutte le versioni di Visual Studio 2019. Scaricare la versione corrispondente al sistema operativo del dispositivo (x86, x64 o ARM64). In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging-unblock-file-download.md) per informazioni sul download di Remote Tools.|
|Visual Studio 2017|[Strumenti remoti](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Compatibile con tutte le versioni di Visual Studio 2017. Scaricare la versione corrispondente al sistema operativo del dispositivo (x86, x64 o ARM64). In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging-unblock-file-download.md) per informazioni sul download di Remote Tools.|
|Visual Studio 2015|[Strumenti remoti](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Remote Tools per Visual Studio 2015 è disponibile in My.VisualStudio.com. Se richiesto, partecipare al programma gratuito [Visual Studio dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) o accedere con l'ID sottoscrizione di Visual Studio. In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging-unblock-file-download.md) per informazioni sul download di Remote Tools.|
|Visual Studio 2013|[Strumenti remoti](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Pagina di download nella documentazione di Visual Studio 2013|
|Visual Studio 2012|[Strumenti remoti](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Pagina di download nella documentazione di Visual Studio 2012|

::: moniker-end

::: moniker range="vs-2017"

|Versione|Collegamento|Note|
|-|-|-|
|Visual Studio 2017|[Strumenti remoti](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Compatibile con tutte le versioni di Visual Studio 2017. Scaricare la versione corrispondente al sistema operativo del dispositivo (x86, x64 o ARM64). In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging-unblock-file-download.md) per informazioni sul download di Remote Tools. Per la versione più recente di Remote Tools, aprire il [documento di Visual Studio 2019](../../debugger/remote-debugging.md?view=vs-2019&preserve-view=true).|
|Visual Studio 2015|[Strumenti remoti](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Remote Tools per Visual Studio 2015 è disponibile in My.VisualStudio.com. Se richiesto, partecipare al programma gratuito [Visual Studio dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) o accedere con l'ID sottoscrizione di Visual Studio. In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging-unblock-file-download.md) per informazioni sul download di Remote Tools.|
|Visual Studio 2013|[Strumenti remoti](/previous-versions/visualstudio/visual-studio-2013/bt727f1t(v=vs.120)#installing-the-remote-tools)|Pagina di download nella documentazione di Visual Studio 2013|
|Visual Studio 2012|[Strumenti remoti](/previous-versions/visualstudio/visual-studio-2012/bt727f1t(v=vs.110)#installing-the-remote-tools)|Pagina di download nella documentazione di Visual Studio 2012|

::: moniker-end

È possibile eseguire il debugger remoto copiando *msvsmon.exe* nel computer remoto anziché installare Remote Tools. Tuttavia, la configurazione guidata del debugger remoto (*rdbgwiz.exe*) è disponibile solo quando si installa Remote Tools. Potrebbe essere necessario utilizzare la procedura guidata per la configurazione se si desidera eseguire il debugger remoto come servizio. Per ulteriori informazioni, vedere [(facoltativo) configurare il debugger remoto come servizio](../../debugger/remote-debugging.md#bkmk_configureService).

>[!NOTE]
>- Per eseguire il debug di app Windows 10 nei dispositivi ARM, usare ARM64, disponibile con la versione più recente di Remote Tools.
>- Per eseguire il debug di app Windows 10 nei dispositivi Windows RT, usare ARM, disponibile solo nel download di Visual Studio 2015 Remote Tools.
