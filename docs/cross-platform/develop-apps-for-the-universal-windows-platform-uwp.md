---
title: Sviluppare app per la piattaforma UWP (Universal Windows Platform)
description: Informazioni sulla creazione di app con Visual Studio e gli strumenti di sviluppo della Windows universali.
ms.custom: SEO-VS-2020
ms.date: 10/24/2017
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- uwp
ms.openlocfilehash: ae5da20dd7eb508745621f517abf77240d32f062c6df9f3e5e27c37ab3f7db44
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121420894"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Sviluppare app per la piattaforma UWP (Universal Windows Platform)

Con la piattaforma UWP (Universal Windows Platform) e uno dei nostri core Windows, è possibile eseguire la stessa app su qualsiasi dispositivo Windows 10, dai telefoni ai desktop. È possibile creare queste app di Windows universale usando Visual Studio e gli strumenti di sviluppo di app di Windows universale.

![Piattaforma UWP (Universal Windows Platform)](../cross-platform/media/uwp_coreextensions.png)

È possibile eseguire le app su telefoni Windows 10, computer desktop Windows 10 o Xbox. Il pacchetto di app non cambia. Con l'introduzione del singolo core unificato Windows 10, un unico pacchetto di app può essere eseguito su tutte le piattaforme. Diverse piattaforme hanno SDK di estensione che è possibile aggiungere all'app per sfruttare i comportamenti specifici di piattaforma. Ad esempio, un SDK di estensione per dispositivi mobili gestisce la pressione del pulsante Indietro su un telefono Windows. Se si fa riferimento a un SDK di estensione nel progetto, è sufficiente aggiungere i controlli di runtime per verificare se tale SDK sia disponibile nella piattaforma. In questo modo è possibile avere lo stesso pacchetto di app per ogni piattaforma.

**Che cos'è il core Windows?**

Per la prima volta, è stato eseguito il refactoring di Windows per avere a disposizione un core comune a tutte le piattaforme Windows 10. Esiste una sola origine comune, un unico kernel di Windows comune, un unico stack I/O di file e un solo modello di applicazione. Per l'interfaccia utente, esiste un unico framework dell'interfaccia utente XAML e un unico framework dell'interfaccia utente HTML. L'esecuzione delle app su diversi dispositivi Windows 10 è stata semplificata per consentire di concentrarsi sulla creazione di app eccezionali.

**Che cos'è esattamente la piattaforma UWP (Universal Windows Platform)?**

La piattaforma UWP (Universal Windows Platform) è semplicemente una raccolta di contratti e versioni che consente di scegliere la destinazione in cui eseguire l'app. La destinazione non è più un sistema operativo, ma una o più famiglie di dispositivi. Per altre informazioni, vedere [Introduzione alla piattaforma UWP (Universal Windows Platform)](/windows/uwp/get-started/universal-application-platform-guide).

## <a name="requirements"></a>Requisiti

Gli strumenti di sviluppo di UWP (Universal Windows Platform) sono dotati di emulatori che consentono di visualizzare l'aspetto dell'app in dispositivi diversi. Per usare gli emulatori, è necessario installare questo software in un computer fisico in cui sia in esecuzione Windows 8.1 (x64) Professional o versioni successive e dotato di un processore che supporti Client Hyper-V e Second Level Address Translation (SLAT). Non è possibile eseguire gli emulatori quando Visual Studio è installato in una macchina virtuale.

Elenco del software necessario:

::: moniker range="vs-2017"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2017 supporta lo sviluppo UWP solo in Windows 10. Per altre informazioni, vedere [Selezione della piattaforma](/visualstudio/productinfo/vs2017-compatibility-vs) e [Requisiti di sistema](/visualstudio/productinfo/vs2017-system-requirements-vs) di Visual Studio.

- [Visual Studio](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download). Sarà anche necessario il carico di lavoro di sviluppo della piattaforma UWP (Universal Windows Platform).

     ![Carico di lavoro UWP (Universal Windows Platform)](media/uwp_workload.png)

::: moniker-end

::: moniker range=">=vs-2019"

- [Windows 10](https://support.microsoft.com/help/17777/downloads-for-windows). Visual Studio 2019 supporta lo sviluppo UWP solo in Windows 10. Per altre informazioni, vedere [Selezione della piattaforma](/visualstudio/releases/2019/compatibility/) e [Requisiti di sistema](/visualstudio/releases/2019/system-requirements/) di Visual Studio.

- [Visual Studio](https://visualstudio.microsoft.com/downloads). Sarà anche necessario il carico di lavoro di sviluppo della piattaforma UWP (Universal Windows Platform).

     ![Carico di lavoro UWP (Universal Windows Platform)](media/uwp_workload.png)

::: moniker-end

Dopo aver installato il software, è necessario abilitare il dispositivo Windows 10 per lo sviluppo. Vedere [Abilitare il dispositivo per lo sviluppo](/windows/uwp/get-started/enable-your-device-for-development). Non è più necessaria una licenza per sviluppatori per ogni dispositivo Windows 10.

## <a name="universal-windows-apps"></a>App di Windows universale

Scegliere il linguaggio di sviluppo preferito tra C#, Visual Basic, C++ o JavaScript per creare un'app della piattaforma UWP per dispositivi Windows 10. Vedere [Creare la prima app](/windows/uwp/get-started/your-first-app) o guardare il video [Tools for Windows 10 Overview](https://channel9.msdn.com/Series/ConnectOn-Demand/229) (Panoramica degli strumenti per Windows 10).

Se si hanno app di Windows Store 8.1 o Windows Phone 8.1 oppure app di Windows universale create con Visual Studio 2015, sarà necessario trasferire tali app per usare la versione più recente della piattaforma UWP (Universal Windows Platform). Vedere [Passare da Windows Runtime 8.x a UWP](/windows/uwp/porting/w8x-to-uwp-root).

Dopo aver creato l'app di Windows universale, è necessario creare un pacchetto dell'app per installarla in un dispositivo Windows 10 o inviarla a Windows Store. Vedere [Creazione di pacchetti delle app](/windows/uwp/packaging/index).

## <a name="see-also"></a>Vedi anche

- [Sviluppo per dispositivi mobili multipiattaforma in Visual Studio](../cross-platform/cross-platform-mobile-development-in-visual-studio.md)
