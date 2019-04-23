---
title: 'Procedura: Specificare il runtime di .NET Framework | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- Profiling Tools, .NET Framework versions
- .NET Framework versions,profililng
ms.assetid: d39f3579-719a-4f47-a97d-5b4232fe4c64
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 2f631e8639c1004fa2cb005da3b6c8bcb27f1a9b
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2019
ms.locfileid: "60076506"
---
# <a name="how-to-specify-the-net-framework-runtime"></a>Procedura: Specificare il Runtime di .NET Framework
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con il rilascio di [!INCLUDE[net_v40_long](../includes/net-v40-long-md.md)], le applicazioni possono essere costituite da moduli compilati usando versioni diverse del runtime di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Per impostazione predefinita, gli strumenti di profilatura di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] profilano il primo runtime caricato dall'applicazione. È possibile specificare il runtime di cui eseguire la profilatura quando si avvia un'applicazione con il profiler e quando si connette il profiler a un'applicazione già in esecuzione.  
  
 **Requisiti**  
  
- [!INCLUDE[vsUltLong](../includes/vsultlong-md.md)], [!INCLUDE[vsPreLong](../includes/vsprelong-md.md)], [!INCLUDE[vsPro](../includes/vspro-md.md)]  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-starting-an-application-with-the-profiler"></a>Per specificare il runtime di .NET Framework da profilare quando si avvia un'applicazione con il profiler  
  
1. In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni, scegliere **Proprietà** e quindi fare clic su **Avanzate**.  
  
     Nella casella di riepilogo **Versione CLR di destinazione** viene visualizzato **Automatico** insieme alle versioni del runtime di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] installate nel computer.  
  
2. Effettuare uno dei passaggi indicati di seguito.  
  
    - Fare clic sulla versione di CLR per la profilatura.  
  
    - Fare clic su **Automatico** per eseguire la profilatura della prima versione caricata dall'applicazione.  
  
### <a name="to-specify-the-net-framework-run-time-to-profile-when-attaching-the-profiler-to-an-application"></a>Per specificare il runtime di .NET Framework da profilare quando si connette il profiler a un'applicazione  
  
1. Nel menu Analizza scegliere Profiler e quindi fare clic su Connetti/Disconnetti.  
  
2. Nella finestra di dialogo Connettere profiler a processo fare clic sul processo da profilare.  
  
     Nella casella di riepilogo **Versione CLR di destinazione** viene visualizzato **Automatico** insieme alle versioni del runtime di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] installate nel computer.  
  
3. Effettuare uno dei passaggi indicati di seguito.  
  
    - Fare clic sulla versione di CLR per la profilatura.  
  
    - Fare clic su **Automatico** per eseguire la profilatura della versione caricata quando il profiler viene connesso all'applicazione.
