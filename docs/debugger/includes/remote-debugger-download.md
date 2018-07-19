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
ms.openlocfilehash: 987193cb7f78947087c6d387e16261d83a20e7c2
ms.sourcegitcommit: c57ae28181ffe14a30731736661bf59c3eff1211
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/11/2018
ms.locfileid: "38809246"
---
1.  Nel dispositivo o server macchina che si desidera eseguire il debug (anziché il computer che esegue Visual Studio), installare la versione corretta di remote tools.

    |Versione|Collegamento|Note|
    |-|-|-|
    |Visual Studio 2017 (versione più recente)|[Remote tools](https://visualstudio.microsoft.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Scaricare sempre la versione corrispondente del sistema operativo del dispositivo (x x86, x64 o ARM64). In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging.md#unblock_msvsmon) per la Guida scaricare remote tools.|
    |Visual Studio 2017 (precedente)|[Remote tools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Remote tools per le versioni precedenti di Visual Studio 2017 sono disponibili da My.VisualStudio.com. ID se richiesto, join di gruppo di Visual Studio Dev Essentials gratuito oppure accedere con la sottoscrizione di Visual Studio. In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging.md#unblock_msvsmon) per la Guida scaricare remote tools.|
    |Visual Studio 2015 (precedente)|[Remote tools](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|ID se richiesto, join di gruppo di Visual Studio Dev Essentials gratuito oppure accedere con la sottoscrizione di Visual Studio. In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging.md#unblock_msvsmon) per la Guida scaricare remote tools.|
    |Visual Studio 2013|[Remote tools](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|2000A nella documentazione di Visual Studio 2013|
    |Visual Studio 2012|[Remote tools](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|2000A nella documentazione di Visual Studio 2012|

2.  Nella pagina di download, scegliere la versione degli strumenti che corrisponde al sistema operativo (x86, x64, ARM o ARM64) e scaricare remote tools.

    > [!IMPORTANT]
    >  Si consiglia di che installare la versione più recente di remote tools corrispondente alla versione di Visual Studio. Le versioni non corrispondenti non sono consigliate. Inoltre, è necessario installare gli strumenti remoti che hanno la stessa architettura del sistema operativo in cui si desidera installarlo. In altre parole, se si desidera eseguire il debug di un'applicazione a 32 bit in un computer remoto che esegue un sistema operativo a 64 bit, è necessario installare la versione a 64 bit di remote tools sul computer remoto.
    >
    >  Per eseguire il debug in Windows 10 nei dispositivi ARM, scegliere il download di ARM64 disponibile con la versione più recente di remote tools.  Per i dispositivi Windows RT, scegliere la versione ARM, che è solo disponibile nel download di Visual Studio 2015 RTW.

3.  Dopo aver scaricato il file eseguibile, passare alla sezione successiva e seguire le istruzioni di installazione.

Se si prova a copiare il debugger remoto (msvsmon.exe) al computer remoto ed eseguirlo, tenere presente che il **configurazione guidata del Debugger remoto** (**rdbgwiz.exe**) viene installato solo quando si scarica il strumenti. Si potrebbe essere necessario utilizzare la procedura guidata per la configurazione in un secondo momento, soprattutto se si desidera che il debugger remoto per l'esecuzione come servizio. Per altre informazioni, vedere [(facoltativo) configurare il debugger remoto come servizio](../../debugger/remote-debugging.md#bkmk_configureService).
