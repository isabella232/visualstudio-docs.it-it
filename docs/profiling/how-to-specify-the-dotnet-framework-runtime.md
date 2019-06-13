---
title: 'Procedura: Specificare il runtime di .NET Framework | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: f0179be3aa5ca55eef0854cc68a7e1287ac284f1
ms.sourcegitcommit: 12f2851c8c9bd36a6ab00bf90a020c620b364076
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/06/2019
ms.locfileid: "66746428"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Procedura: Specificare il runtime di .NET Framework

Con la versione di .NET Framework 4, le applicazioni possono essere composte di moduli che sono stati compilati usando versioni diverse di run-time di .NET Framework. Per impostazione predefinita, gli strumenti di profilatura di Visual Studio profilano il primo runtime caricato dall'applicazione. È possibile specificare il runtime di cui eseguire la profilatura quando si avvia un'applicazione con il profiler e quando si connette il profiler a un'applicazione già in esecuzione.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Per specificare il runtime di .NET Framework da profilare quando si avvia un'applicazione con il profiler

1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni, scegliere **Proprietà** e quindi fare clic su **Avanzate**.

     Il **versione CLR di destinazione** finestra visualizzata nell'elenco **automatica** e le versioni di runtime di .NET Framework installate nel computer.

2. Effettuare uno dei passaggi indicati di seguito.

    - Fare clic sulla versione di CLR per la profilatura.

    - Fare clic su **Automatico** per eseguire la profilatura della prima versione caricata dall'applicazione.

## <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Per specificare il runtime di .NET Framework da profilare quando si connette il profiler a un'applicazione

1. Nel menu **Analizza** scegliere **Profiler** e fare clic su **Connetti/Disconnetti**.

2. Nella finestra di dialogo **Connettere profiler a processo** fare clic sul processo da profilare.

     Il **versione CLR di destinazione** casella di riepilogo s **automatica** e le versioni di runtime di .NET Framework installate nel computer.

3. Effettuare uno dei passaggi indicati di seguito.

    - Fare clic sulla versione di CLR per la profilatura.

    - Fare clic su **Automatico** per eseguire la profilatura della versione caricata quando il profiler viene connesso all'applicazione.