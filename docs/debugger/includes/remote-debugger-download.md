---
title: Download di Remote debugger
description: Collegamenti di download per il debugger remoto
services: ''
author: mikejo5000
ms.service: ''
ms.topic: include
ms.date: 05/23/2018
ms.author: mikejo
ms.custom: include file
ms.openlocfilehash: 358dc0b457381bb56532e6cae1156aac9ea2dba2
ms.sourcegitcommit: d1824ab926ebbc4a8057163e0edeaf35cec57433
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/24/2018
---
1.  Nel dispositivo o server computer che si desidera eseguire il debug (anziché il computer che esegue Visual Studio), ottenere la versione corretta di remote tools.

    |Versione|Collegamento|Note|
    |-|-|-|
    |Visual Studio 2017 (versione più recente)|[Strumenti remoti](https://www.visualstudio.com/downloads/?q=remote+tools#remote-tools-for-visual-studio-2017)|Scaricare sempre la versione corrispondente di sistema operativo del dispositivo (x86 o x64). In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging.md#unblock_msvsmon) per la Guida scaricare gli strumenti remoti.|
    |Visual Studio 2017, (precedente)|[Strumenti remoti](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202017)|Sono disponibili da My.VisualStudio.com strumenti remoti per le versioni precedenti di Visual Studio 2017. Se richiesto, il gruppo di Visual Studio Dev Essentials libero join o accedere con la sottoscrizione di Visual Studio ID. In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging.md#unblock_msvsmon) per la Guida scaricare gli strumenti remoti.|
    |Visual Studio 2015 (precedente)|[Strumenti remoti](https://my.visualstudio.com/Downloads?q=remote%20tools%20visual%20studio%202015)|Se richiesto, il gruppo di Visual Studio Dev Essentials libero join o accedere con la sottoscrizione di Visual Studio ID. In Windows Server, vedere [sbloccare il download del file](../../debugger/remote-debugging.md#unblock_msvsmon) per la Guida scaricare gli strumenti remoti.|
    |Visual Studio 2013|[Strumenti remoti](https://msdn.microsoft.com/library/bt727f1t(v=vs.120).aspx#BKMK_Installing_the_Remote_Tools)|Scaricare una pagina nella documentazione di Visual Studio 2013|
    |Visual Studio 2012|[Strumenti remoti](https://msdn.microsoft.com/library/bt727f1t(v=vs.110).aspx#BKMK_Installing_the_Remote_Tools)|Scaricare una pagina nella documentazione di Visual Studio 2012|
  
2.  Nella pagina di download, scegliere la versione degli strumenti che corrisponde al sistema operativo (x x86, x64 o ARM) e scaricare gli strumenti remoti.
  
    > [!IMPORTANT]
    >  Si consiglia di che installare la versione più recente di remote tools corrispondente alla versione di Visual Studio. Le versioni non corrispondenti non sono consigliate. Inoltre, è necessario installare gli strumenti remoti che hanno la stessa architettura del sistema operativo in cui si desidera installarlo. In altre parole, se si desidera eseguire il debug di un'applicazione a 32 bit in un computer remoto che esegue un sistema operativo a 64 bit, è necessario installare la versione a 64 bit di remote tools sul computer remoto. 
    >   
    >  Superficie 3 passati da ARM su x64 architettura. Una versione ARM di remote tools non è disponibile per Visual Studio 2017. Per Visual Studio 2015, trovare la versione ARM nel download di Visual Studio 2015 RTW.
  
3.  Dopo aver scaricato il file eseguibile, passare alla sezione successiva e seguire le istruzioni di installazione.

Se si tenta di copiare il debugger remoto (msvsmon.exe) nel computer remoto ed eseguirlo, tenere presente che il **configurazione guidata Debugger remoto** (**rdbgwiz.exe**) viene installato solo quando si scarica il strumenti. Si potrebbe essere necessario utilizzare la procedura guidata per la configurazione in un secondo momento, soprattutto se si desidera che il debugger remoto venga eseguito come servizio. Per ulteriori informazioni, vedere [(facoltativo) configurare il debugger remoto come servizio](../../debugger/remote-debugging.md#bkmk_configureService).
