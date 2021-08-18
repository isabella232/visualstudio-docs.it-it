---
title: Visual Studio nei dispositivi con tecnologia ARM
description: Consigli per l'Visual Studio su dispositivi con processori basati su ARM.
ms.date: 09/10/2020
ms.topic: conceptual
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 034487e5af331d6724c26bfc09958b24be42ebcaf59cd654496097e5a2a15dee
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121356556"
---
# <a name="visual-studio-on-arm-powered-devices"></a>Visual Studio nei dispositivi basati su ARM

> [!IMPORTANT]
> Visual Studio è supportato solo nei dispositivi che usano un processore basato su x86 o AMD64/x64.

Visual Studio è progettato per i processori di destinazione basati sull'architettura x86 e non sono disponibili versioni di Visual Studio per i processori basati su ARM. Tuttavia, Windows [l'emulazione x86](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation)in ARM, che Visual Studio possibile eseguire. L'esecuzione di Visual Studio in un processore ARM tramite emulazione x86 comprova le prestazioni di Visual Studio e diverse funzionalità di Visual Studio non sono progettate per funzionare in questo scenario. Di conseguenza, non è consigliabile eseguire Visual Studio nei dispositivi che usano processori basati su ARM, ma è consigliabile usare dispositivi ARM destinati in remoto.

## <a name="remote-targeting-arm-devices"></a>Destinazione remota dei dispositivi ARM
Per un'esperienza ottimale, è consigliabile usare Visual Studio in un computer separato con tecnologia x86 e usare le funzionalità remote di distribuzione e debug in Visual Studio per il dispositivo basato su ARM. Per eseguire il debug Windows applicazioni universali già installate nel dispositivo, vedere la documentazione [relativa al debug del pacchetto dell'app](../debugger/debug-installed-app-package.md) installato. Per distribuire una nuova app, vedere [running a Windows Store app remotley](../debugger/run-windows-store-apps-on-a-remote-machine.md)(Esecuzione di un'app di Windows Store). Per tutti gli altri tipi di applicazioni, vedere la [documentazione sul debug](../debugger/remote-debugging.md) remoto.

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>Suggerimenti per l'esecuzione Visual Studio nei dispositivi ARM

### <a name="use-only-when-needed"></a>Usare solo quando necessario
Ottimizzare il tempo usando Visual Studio solo quando necessario per operazioni specifiche di ARM. Le prestazioni di qualsiasi dispositivo basato su ARM saranno scarse e probabilmente non saranno accettabili per l'uso normale.

### <a name="install-time"></a>Tempo dell'installazione
Pianificare l Visual Studio richiederà più tempo per l'installazione e si prevede che venga sospeso per periodi di tempo o che sia necessario il riavvio.
 
### <a name="remote-tools"></a>Strumenti remoti
Per eseguire il debug di un'app in esecuzione in un dispositivo remoto, è necessario [scaricare e installare gli strumenti remoti](../debugger/remote-debugging.md#download-and-install-the-remote-tools) per ARM.

### <a name="start-debugging-f5"></a>Avviare i debug (F5)
Non tutti i Visual Studio sono configurati per avviare i progetti in locale quando si avvia il debug (**F5**) da un dispositivo ARM. Potrebbe essere necessario configurare il Visual Studio per il debug remoto, anche se l'app è in esecuzione in locale. Per altre informazioni, vedere [Debug remoto.](../debugger/remote-debugging.md)

## <a name="we-need-your-help"></a>È necessario il supporto dell'utente.
Se si desidera che Visual Studio in modo nativo nei dispositivi ARM, è possibile conoscere gli scenari e il supporto necessario. È possibile contattarci pubblicando un post nella [community degli sviluppatori.](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html)
