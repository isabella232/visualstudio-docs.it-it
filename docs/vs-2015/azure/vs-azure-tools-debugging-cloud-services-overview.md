---
title: Opzioni per il debug di Azure dei servizi cloud | Microsoft Docs
description: Debug dei servizi cloud di Azure
author: mikejo5000
manager: douge
ms.assetid: 80755da7-8350-4f5c-97ce-2962beabb36d
ms.topic: conceptual
ms.workload: azure-vs
ms.date: 03/18/2017
ms.author: mikejo
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.openlocfilehash: bd2608371871b7adc925fc11927fe061b00a1ec6
ms.sourcegitcommit: e481d0055c0724d20003509000fd5f72fe9d1340
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "51002881"
---
# <a name="learn-the-various-ways-to-debug-an-azure-cloud-service"></a>Informazioni sui vari modi disponibili per eseguire il debug di un servizio cloud di Azure
Questo articolo vengono forniti collegamenti ai vari modi per eseguire il debug di un servizio cloud di Azure. 

## <a name="debugging-an-azure-cloud-service-in-visual-studio"></a>Debug di un servizio cloud di Azure in Visual Studio
È possibile risparmiare tempo e denaro usando Azure compute emulator per il debug del servizio cloud in un computer locale. Dal debug di un servizio in locale prima di distribuirla, è possibile migliorare affidabilità e prestazioni senza pagare per tempo di calcolo. Tuttavia, possono verificarsi alcuni errori solo quando si esegue un servizio cloud in Azure. Gli errori che si verificano solo quando si esegue un servizio cloud in Azure possono eseguire il debug abilitando il debug remoto quando si pubblica il servizio e quindi collegare il debugger a un'istanza del ruolo. Per altre informazioni, vedere [il Debug del servizio cloud nel computer locale](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-your-cloud-service-on-your-local-computer).

## <a name="using-intellitrace"></a>Utilizzo di IntelliTrace 
Se si usa Visual Studio Enterprise per scrivere ruoli destinati a .NET Framework 4.5, è possibile abilitare IntelliTrace nel momento in cui si distribuisce un servizio cloud di Azure da Visual Studio. IntelliTrace fornisce un log che è possibile utilizzare con Visual Studio per il debug dell'applicazione come se fosse in esecuzione in Azure. Per altre informazioni, vedere [debug di un servizio cloud pubblicato con IntelliTrace e Visual Studio](http://go.microsoft.com/fwlink/p/?LinkId=623016).

## <a name="remote-debugging"></a>Debug remoto 
È possibile abilitare il debug remoto nei servizi cloud al momento quando si distribuisce il servizio cloud da Visual Studio. Se si sceglie di abilitare il debug remoto per una distribuzione, servizi di debug remoto vengono installati nelle macchine virtuali che eseguono ogni istanza del ruolo. Questi servizi, ad esempio `msvsmon.exe` : non influiscono sulle prestazioni né producono costi aggiuntivi. Per altre informazioni, vedere [eseguire il Debug di un servizio cloud in Azure](vs-azure-tools-debug-cloud-services-virtual-machines.md#debug-a-cloud-service-in-azure).

## <a name="next-steps"></a>Passaggi successivi
- [Debug di un servizio cloud di Azure o una macchina virtuale in Visual Studio](./vs-azure-tools-debug-cloud-services-virtual-machines.md) -informazioni dettagliate su come eseguire il debug di servizi cloud di Azure.