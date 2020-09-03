---
title: Sviluppare app per la piattaforma UWP (Universal Windows Platform) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b3f38f519444de7876046baf242f74a18b8c5a59
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/02/2020
ms.locfileid: "75844364"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Sviluppare app per la piattaforma UWP (Universal Windows Platform)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con la piattaforma UWP (Universal Windows Platform) e uno dei nostri core Windows, è possibile eseguire la stessa app su qualsiasi dispositivo Windows 10, dai telefoni ai desktop. È possibile creare queste app di Windows universale usando Visual Studio 2015 e gli strumenti di sviluppo di app di Windows universale.

 ![Piattaforma UWP (Universal Windows Platform)](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")

 È possibile eseguire le app su telefoni Windows 10, computer desktop Windows 10 o Xbox. Il pacchetto di app non cambia. Con l'introduzione del singolo core unificato Windows 10, un unico pacchetto di app può essere eseguito su tutte le piattaforme. Diverse piattaforme hanno SDK di estensione che è possibile aggiungere alla app per sfruttare i comportamenti specifici di piattaforma. Ad esempio, un SDK di estensione per dispositivi mobili gestisce la pressione del pulsante Indietro su un telefono Windows. Se si fa riferimento a un SDK di estensione nel progetto, è sufficiente aggiungere i controlli di runtime per verificare se tale SDK è disponibile nella piattaforma. In questo modo è possibile avere lo stesso pacchetto di app per ogni piattaforma.

 **Che cos'è il core Windows?**

 Per la prima volta, è stato eseguito il refactoring di Windows per avere a disposizione un core comune a tutte le piattaforme Windows 10. Esiste una sola origine comune, un unico kernel di Windows comune, un unico stack I/O di file e un solo modello di applicazione. Per l'interfaccia utente, esiste un unico framework dell'interfaccia utente XAML e un unico framework dell'interfaccia utente HTML. L'esecuzione delle app su diversi dispositivi Windows 10 è stata semplificata per permettere di concentrarsi sulla creazione di app eccezionali.

 **Che cos'è esattamente la piattaforma UWP (Universal Windows Platform)?**

 È semplicemente una raccolta di contratti e versioni che consente di scegliere la destinazione in cui eseguire l'app. La destinazione non è più un sistema operativo, bensì una o più famiglie di dispositivi. Altre informazioni sono disponibili nella [Guida della piattaforma](https://msdn.microsoft.com/library/windows/apps/dn894631.aspx).

## <a name="requirements"></a>Requisiti
 Gli strumenti di sviluppo di app di Windows universale sono dotati di emulatori che permettono di visualizzare l'aspetto della app in dispositivi diversi. Per usare gli emulatori, è necessario installare questo software in un computer fisico in cui sia in esecuzione Windows 8.1 (x64) Professional o versioni successive e dotato di un processore che supporti Client Hyper-V e Second Level Address Translation (SLAT). Non è possibile eseguire gli emulatori quando Visual Studio è installato in una macchina virtuale.

 Elenco del software necessario:

- [Windows 10](https://windows.microsoft.com/windows/downloads)

- [Visual Studio 2015](https://visualstudio.microsoft.com/downloads/). Assicurarsi che gli strumenti per lo sviluppo di app di Windows universale siano selezionati nell'elenco di funzionalità facoltative. Senza questi strumenti, non sarà possibile creare app universali.

  Dopo aver installato il software, è necessario [abilitare il dispositivo Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) per lo sviluppo (non è più necessaria una licenza per sviluppatori per ogni dispositivo Windows 10).

  **Supporto per Windows 8.1 e Windows 7**

  Per sviluppare app di Windows universale con Visual Studio 2015 su una piattaforma diversa da Windows 10, sono presenti alcune restrizioni:

- Windows 8.1: non è possibile eseguire l'app localmente (solo in un dispositivo Windows 10 remoto). È possibile usare gli emulatori in Visual Studio, ma non il simulatore.

- Windows 7: non è possibile eseguire l'app localmente (solo in un dispositivo Windows 10 remoto). Non è possibile usare gli emulatori né il simulatore di Visual Studio.

  È possibile usare la finestra di progettazione XAML solo se la piattaforma di sviluppo è Windows 10.

## <a name="universal-windows-apps"></a>App di Windows universale
 Scegliere il linguaggio di sviluppo preferito tra C#, Visual Basic, C++ o JavaScript per [creare un'app di Windows universale per dispositivi Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10). In alternativa, è possibile guardare [questo video introduttivo](https://channel9.msdn.com/Series/ConnectOn-Demand/229).

 Se si hanno app di Windows Store 8.1 o Windows Phone 8.1 oppure app di Windows universale create con Visual Studio 2015 RC, [trasferire le app esistenti](https://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) per usare la versione più recente della piattaforma UWP (Universal Windows Platform).

 Dopo aver creato l'app di Windows universale, è necessario [creare un pacchetto dell'app](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) per installarla in un dispositivo Windows 10 o inviarla al Windows Store.
