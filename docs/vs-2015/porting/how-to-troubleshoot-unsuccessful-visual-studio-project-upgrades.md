---
title: 'Procedura: Risolvere i problemi di aggiornamento di progetti non riuscito | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: 6b50bbaaf7e5b018709f3cf0dece3c0ae38410f8
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/07/2018
ms.locfileid: "53064796"
---
# <a name="how-to-troubleshoot-unsuccessful-visual-studio-project-upgrades"></a>Procedura: Risolvere i problemi di aggiornamento di progetti di Visual Studio con esito negativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

In alcuni casi Visual Studio completamente non può convertire un progetto da una versione precedente di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Se i suggerimenti nelle sezioni seguenti non consentono di risolvere il problema riscontrato, potrebbe essere in grado di trovare altre informazioni su TechNet [Wiki: Portale di sviluppo](http://go.microsoft.com/fwlink/?LinkId=254808).

## <a name="the-project-does-not-run-because-files-are-not-found"></a>Il progetto non viene eseguita perché non vengono trovati file
 Un file di progetto contiene i percorsi di file hardcoded che [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Usa per eseguire il progetto quando si preme F5. Questi percorsi possono includere il percorso del devenv.exe e altri file necessari. In una versione aggiornata di [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], i percorsi di questi file sono stati modificati.

#### <a name="to-resolve-incorrect-file-paths"></a>Per risolvere i percorsi di file non corretto

1.  Aprire il file di progetto in un editor di testo.

2.  Analizzare i percorsi di file che non sia corretti, specialmente quelle che contengono un [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] numero di versione.

3.  Modificare i percorsi di file non corretto in modo che facciano riferimento alle destinazioni di nuovo.

## <a name="the-project-does-not-build-because-references-are-not-valid"></a>Il progetto non viene compilato perché i riferimenti non validi
 Quando esegue l'aggiornamento [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], si potrebbe anche essere aggiornando il [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versione. Se il progetto contiene i riferimenti che non sono più disponibili in più di recente [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versione, non vengano risolti correttamente. Ciò si verifica soprattutto per i riferimenti che includono numeri di versione, ad esempio, `Microsoft.VisualStudio.Shell.Interop.8.0`.

 Se il codice contiene molti riferimenti non validi, potrebbe essere la soluzione più semplice per usare la funzionalità di multitargeting [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] come destinazione una versione precedente del [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)].

#### <a name="to-resolve-incorrect-references"></a>Per risolvere i riferimenti non corretti

1. Aprire il file di progetto in un editor di testo.

2. Aprire le proprietà del progetto.

3. Selezionare i valori corretti **Framework di destinazione** valore. In alternativa, è possibile modificare il valore della `<TargetFrameworkVersion>` elemento direttamente nel file di progetto.

   Se si vuole che il progetto per l'esecuzione in aggiornati [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] versione, è necessario aggiornare i riferimenti del progetto e aggiornare anche eventuali `Imports` o `Using` istruzioni che chiama i riferimenti. Se il progetto viene caricato nell'IDE, è possibile aggiornare i riferimenti utilizzando **Esplora soluzioni** o nella **gestione riferimenti** nella finestra di dialogo.

## <a name="see-also"></a>Vedere anche
 [/ Aggiornamento (devenv.exe)](../ide/reference/upgrade-devenv-exe.md) [conversione in ASP.NET 4](http://msdn.microsoft.com/library/790147c6-36c1-41b5-a52d-30b9ccd2bd10)
