---
title: 'Procedura: risolvere i problemi relativi agli aggiornamenti di progetti non riusciti | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
f1_keywords:
- VisualStudio.SourceControl.CannotOpenFromSourceControlDSW
- vs.UpgradeProjectSolution.8.0
helpviewer_keywords:
- upgrading applications, Visual Studio
- upgrading projects [Visual Studio]
- projects [Visual Studio], upgrading
- Visual Studio Conversion Wizard
- Conversion wizard
ms.assetid: 842fe448-c044-4343-8eae-d81711cf48ba
caps.latest.revision: 31
author: kraigb
ms.author: kraigb
manager: jillfra
ms.openlocfilehash: 65059e285777e48633da5eb7e8723e3997f37dfa
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75844443"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Procedura: Risolvere i problemi relativi agli aggiornamenti di progetti Visual Studio con esito negativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In alcuni casi Visual Studio non è in grado di convertire completamente un progetto da una versione precedente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Se i suggerimenti nelle sezioni seguenti non consentono di risolvere il problema specifico, è possibile trovare ulteriori informazioni su TechNet [wiki: portale di sviluppo](https://social.technet.microsoft.com/wiki/contents/articles/706.wiki-development-portal.aspx#Visual_Studio).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Il progetto non viene eseguito perché i file non sono stati trovati
 Un file di progetto contiene percorsi di file hardcoded che [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] utilizza per eseguire il progetto quando si preme F5. Questi percorsi possono includere il percorso di devenv. exe e gli altri file necessari. In una versione aggiornata di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è possibile che i percorsi di questi file siano stati modificati.

#### <a name="to-resolve-incorrect-file-paths"></a>Per risolvere i percorsi di file non corretti

1. Aprire il file di progetto in un editor di testo.

2. Analizzare i percorsi di file che potrebbero non essere corretti, in particolare quelli che contengono un numero di versione [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

3. Modificare i percorsi di file non corretti in modo che puntino alle nuove destinazioni.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Il progetto non viene compilato perché i riferimenti non sono validi
 Quando si aggiorna [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], è anche possibile aggiornare la versione del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)]. Se il progetto contiene riferimenti che non sono più disponibili nella versione più recente di [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)], è possibile che non vengano risolti correttamente. Questo è particolarmente probabile per i riferimenti che includono i numeri di versione, ad esempio `Microsoft.VisualStudio.Shell.Interop.8.0`.

 Se il codice contiene molti riferimenti non validi, la soluzione più semplice potrebbe consistere nell'usare la funzionalità di multitargeting di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] per definire come destinazione una versione precedente del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="to-resolve-incorrect-references"></a>Per risolvere i riferimenti non corretti

1. Aprire il file di progetto in un editor di testo.

2. Aprire le proprietà del progetto.

3. Selezionare il valore del **Framework di destinazione** corretto. In alternativa, è possibile modificare il valore dell'elemento `<TargetFrameworkVersion>` direttamente nel file di progetto.

   Se si desidera che il progetto venga eseguito nella versione [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] aggiornata, è necessario aggiornare i riferimenti per il progetto e aggiornare anche eventuali istruzioni `Imports` o `Using` che chiamano i riferimenti. Se il progetto viene caricato nell'IDE, è possibile aggiornare i riferimenti usando **Esplora soluzioni** o la finestra di dialogo **Gestione riferimenti** .

## <a name="see-also"></a>Vedere anche
 [/Upgrade (devenv. exe)](../ide/reference/upgrade-devenv-exe.md) [conversione in ASP.NET 4](https://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
