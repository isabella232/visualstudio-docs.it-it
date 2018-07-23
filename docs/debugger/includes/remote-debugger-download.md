---
title: Download di Remote debugger
description: I collegamenti di download per il debugger remoto
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 491b01d87e4f1a9980143e9ffcc501b3cda7c922
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/20/2018
ms.locfileid: "39189422"
---
1.  Nel dispositivo o server macchina che si desidera eseguire il debug (anziché il computer che esegue Visual Studio), installare la versione corretta di remote tools.

    |Versione|Collegamento|Note|
    |-|-|-|
    |Visual Studio 2017 (versione più recente)|[Remote tools](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|La versione più recente di remote tools è compatibile con tutte le versioni di Visual Studio 2017. Scaricare sempre la versione corrispondente del sistema operativo del dispositivo (x x86, x64 o ARM64). In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging-unblock-file-download.md) per la Guida scaricare remote tools.|
    |Visual Studio 2015|[Remote tools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Remote tools per Visual Studio 2015 sono disponibili da My.VisualStudio.com. Se richiesto, aggiungere il prodotto gratuito [Visual Studio Dev Essentials](https://visualstudio.microsoft.com/dev-essentials/) programma oppure accedere con l'ID sottoscrizione di Visual Studio. In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging-unblock-file-download.md) per la Guida scaricare remote tools.|
    |Visual Studio 2013|[Remote tools](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|2000A nella documentazione di Visual Studio 2013|
    |Visual Studio 2012|[Remote tools](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|2000A nella documentazione di Visual Studio 2012|

2.  Nella pagina di download, scegliere la versione degli strumenti che corrisponde al sistema operativo (x86, x64, ARM o ARM64) e scaricare remote tools.

    > [!IMPORTANT]
    >  È consigliabile installare la versione più recente di remote tools per il rilascio di Visual Studio. La versione più recente (ad esempio, 15.8) è compatibile con le versioni precedenti (ad esempio, 15.0); Tuttavia, le versioni precedenti non sono compatibili con versioni successive. Inoltre, è necessario installare gli strumenti remoti che hanno la stessa architettura del sistema operativo in cui si desidera installarlo. In altre parole, se si desidera eseguire il debug di un'applicazione a 32 bit in un computer remoto che esegue un sistema operativo a 64 bit, è necessario installare la versione a 64 bit di remote tools sul computer remoto.
    >
    >  Per eseguire il debug in Windows 10 nei dispositivi ARM, scegliere il download di ARM64 disponibile con la versione più recente di remote tools.  Per i dispositivi Windows RT, scegliere la versione ARM, che è solo disponibile nel download di Visual Studio 2015 RTW.

3.  Dopo aver scaricato il file eseguibile, passare alla sezione successiva e seguire le istruzioni di installazione.

Se si prova a copiare il debugger remoto (msvsmon.exe) al computer remoto ed eseguirlo, tenere presente che il **configurazione guidata del Debugger remoto** (**rdbgwiz.exe**) viene installato solo quando si scarica il strumenti. Si potrebbe essere necessario utilizzare la procedura guidata per la configurazione in un secondo momento, soprattutto se si desidera che il debugger remoto per l'esecuzione come servizio. Per altre informazioni, vedere [(facoltativo) configurare il debugger remoto come servizio](../../debugger/remote-debugging.md#bkmk_configureService).
