---
title: 'Procedura: Aggiornare i progetti Visual C++ a Visual Studio 2015 | Microsoft Docs'
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: mikeblome
ms.author: mblome
manager: jillfra
ms.openlocfilehash: b33b1b47ad4c32aabe09aae5a66fe3f02aeb1487
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74300385"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Procedura: Aggiornare i progetti Visual C++ a Visual Studio 2015
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente su Visual Studio 2017, vedere [Guida al porting e aggiornamento in Visual C++](https://docs.microsoft.com/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Quando si apre per la prima volta un progetto Visual C++ creato in una versione precedente di Visual Studio, è possibile che venga richiesto di aggiornare il progetto. Nel messaggio viene chiesto se si desidera eseguire l'aggiornamento alla versione più recente del compilatore e delle librerie di Visual C++. Le opzioni per l'aggiornamento dipendono dalla versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] usata per creare il progetto.

 È possibile usare [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] per aprire, modificare e compilare i progetti [!INCLUDE[win8](../includes/win8-md.md)] creati in [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], ma per creare un nuovo progetto [!INCLUDE[win8](../includes/win8-md.md)] , è necessario usare [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]. Per creare un progetto [!INCLUDE[win81](../includes/win81-md.md)] , è necessario usare [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)].

 Per creare un progetto Windows 10, è necessario usare [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)].

 Se non viene richiesto di aggiornare il progetto, è possibile che non sia necessario eseguire alcun aggiornamento.

- Se il progetto (con estensione VCPROJ) è stato creato in una versione di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] precedente a [!INCLUDE[vs2010](../includes/vs2010-md.md)], è necessario aggiornare il progetto.

- Se il progetto (con estensione VCXPROJ) è stato creato in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)],  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]o [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] , sono disponibili due opzioni:

  - È possibile ignorare l'aggiornamento. In [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] verrà caricato il progetto senza apportare alcuna modifica se è disponibile l'accesso agli strumenti di Visual C++ in [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] con SP1, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] o [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]. È possibile fornire questo accesso installando la versione di Visual Studio con cui il progetto è stato creato nello stesso computer in cui è presente [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]. Per altre informazioni, vedere [Installing Visual Studio Versions Side-by-Side](../install/install-visual-studio-versions-side-by-side.md).

  - È possibile aggiornare il progetto consentendo a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] di apportare le modifiche descritte più avanti in questo argomento. Se si dispone di più di un progetto Visual C++ nella soluzione, è necessario aggiornali tutti.

    > [!NOTE]
    > Se si rifiuta l'aggiornamento alla prima richiesta, è possibile aggiornare il progetto in un secondo momento scegliendo **Aggiorna progetto VC++** dal menu **Progetto** . Se il comando non viene visualizzato, non è necessario alcun aggiornamento.

## <a name="upgrading-a-visual-c-project"></a>Aggiornamento di un progetto Visual C++
 Se si consente a [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] di aggiornare automaticamente il progetto, vengono apportate queste modifiche:

- Il progetto viene modificato in modo da usare il compilatore e le librerie di [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] (PlatformToolset = VisualStudio v140).

- Per i progetti [!INCLUDE[cppcli](../includes/cppcli-md.md)] TargetFrameworkVersion viene impostato su .NET Framework 4.5.2.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Continuare a usare un set di strumenti della piattaforma personalizzato
 Se si desidera continuare a usare un set di strumenti della piattaforma personalizzato in [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)], il set di strumenti deve trovarsi in %Programmi%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ in un computer x86 o in %Programmi (x86)%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ in un computer x64. Per informazioni su come creare un set di strumenti della piattaforma personalizzato, vedere il post relativo al [multitargeting nativo per C++](https://go.microsoft.com/fwlink/?LinkId=248587) nel blog del team di Visual C++.

## <a name="see-also"></a>Vedere anche
 [Guida al porting e aggiornamento in Visual C++](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb) [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md)
