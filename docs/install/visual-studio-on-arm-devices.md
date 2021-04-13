---
title: Visual Studio nei dispositivi dotati di ARM
description: Suggerimenti per l'uso di Visual Studio nei dispositivi con processori basati su ARM.
ms.date: 09/10/2020
ms.topic: conceptual
author: j-martens
ms.author: jmartens
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 31fb209a3f19c052c19e98691b8643bb098887ee
ms.sourcegitcommit: 6d88913a8b5a9e5eda01d3f95205b4d138f440f8
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/13/2021
ms.locfileid: "107295806"
---
# <a name="visual-studio-on-arm-powered-devices"></a>Visual Studio nei dispositivi basati su ARM

> [!IMPORTANT]
> Visual Studio è supportato solo nei dispositivi che usano un processore basato su x86 o AMD64/x64.

Visual Studio è progettato per i processori di destinazione in base all'architettura x86 e non sono disponibili versioni di Visual Studio per i processori basati su ARM. Tuttavia, Windows fornisce l' [emulazione x86 su ARM](https://www.docs.microsoft.com/windows/uwp/porting/apps-on-arm-x86-emulation), che può essere eseguito da Visual Studio. L'esecuzione di Visual Studio in un processore ARM tramite l'emulazione x86 comporta un grave danneggiamento delle prestazioni di Visual Studio e diverse funzionalità di Visual Studio non sono progettate per funzionare in questo scenario. Di conseguenza, non è consigliabile eseguire Visual Studio nei dispositivi che usano processori basati su ARM e consigliare invece i dispositivi ARM con destinazione remota.

## <a name="remote-targeting-arm-devices"></a>Dispositivi ARM di destinazione remota
Per un'esperienza ottimale, è consigliabile usare Visual Studio in un computer basato su x86 separato e usare le funzionalità di distribuzione e debug remote in Visual Studio per usare il dispositivo basato su ARM. Per eseguire il debug di applicazioni universali di Windows già installate nel dispositivo, vedere la documentazione relativa al [debug del pacchetto dell'app installato](../debugger/debug-installed-app-package.md) . Per distribuire una nuova app, vedere [esecuzione di un'app di Windows Store](../debugger/run-windows-store-apps-on-a-remote-machine.md). Per tutti gli altri tipi di applicazioni, vedere la documentazione relativa al [debug remoto](../debugger/remote-debugging.md) .

## <a name="tips-for-running-visual-studio-on-arm-devices"></a>Suggerimenti per l'esecuzione di Visual Studio nei dispositivi ARM

### <a name="use-only-when-needed"></a>Usare solo quando necessario
Ottimizza il tuo tempo usando Visual Studio solo quando necessario per il lavoro specifico di ARM. Le prestazioni di qualsiasi dispositivo alimentato da ARM non saranno sufficienti e probabilmente non saranno accettabili per l'uso normale.

### <a name="install-time"></a>Tempo dell'installazione
Pianificare l'installazione di Visual Studio in modo da richiedere più tempo e prevedere una pausa per periodi di tempo o richiedere il riavvio.
 
### <a name="remote-tools"></a>Strumenti remoti
Per eseguire il debug di un'app in esecuzione in un dispositivo remoto, è necessario [scaricare e installare Remote Tools](../debugger/remote-debugging.md#download-and-install-the-remote-tools) per ARM.

### <a name="start-debugging-f5"></a>Avviare i debug (F5)
Non tutti i progetti di Visual Studio sono configurati per avviare i progetti localmente quando si avvia il debug (**F5**) da un dispositivo ARM. Potrebbe essere necessario configurare Visual Studio per il debug remoto, anche se l'app è in esecuzione in locale. Per ulteriori informazioni, vedere [Remote Debugging](../debugger/remote-debugging.md).

## <a name="we-need-your-help"></a>È necessario un aiuto.
Se si vuole che Visual Studio venga eseguito in modalità nativa sui dispositivi ARM, è opportuno conoscere gli scenari e il supporto necessari. È possibile contattare Microsoft pubblicando la [community degli sviluppatori](https://developercommunity.visualstudio.com/idea/1161018/native-arm-support-for-visual-studio.html).
