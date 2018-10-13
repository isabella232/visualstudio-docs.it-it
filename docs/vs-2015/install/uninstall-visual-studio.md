---
title: Disinstallare Visual Studio | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 25fbfec12299cecf265437baa04a3dd86093f30b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259339"
---
# <a name="uninstall-visual-studio"></a>Disinstallare Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio 2017, vedere [disinstallare Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/uninstall-visual-studio).

Questa pagina descrive la procedura di disinstallazione di Visual Studio 2015, una versione precedente della famiglia integrata di strumenti di produttività per sviluppatori.  
  
##  <a name="uninstalling"></a>   
#### <a name="to-uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Per disinstallare Visual Studio usando il metodo di disinstallazione "standard"  
  
1.  Nelle **Pannello di controllo**via le **programmi e funzionalità** pagina, scegliere l'edizione del prodotto che vuoi disinstallare e quindi scegliere **modifica**.  
  
2.  Nell'installazione guidata, scegliere **disinstallazione**, scegliere **Yes**e quindi seguire le istruzioni rimanenti della procedura guidata.  
  
 Questo metodo standard, o predefinito lascerà alcuni elementi della versione di Visual Studio originariamente installata (ad esempio, di Microsoft .NET Framework, Microsoft Visual C++ Redistributable, Microsoft SQL Server, e così via).   È necessario lasciare questi due componenti in quanto molte altre applicazioni dipendono da essi. Tuttavia, se si desidera rimuovere anche questi elementi, seleziona la relativa voce in **programmi e funzionalità**e quindi eliminali singolarmente.  
  
#### <a name="to-uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Per disinstallare Visual Studio e tutti gli altri file correlati (vale a dire, disinstallare quasi tutto)  
  
1.  Individuare il file .exe Visual Studio (ad esempio, cercare "vs_enterprise.exe").  
  
    > [!NOTE]
    >  Il file deve trovarsi in una sottocartella di "%ProgramData%\Package Cache", ad esempio: Cache C:\ProgramData\Package\\\vs_enterprise.exe {37e19555-e88d-4aed-9d42-82d0784d2b79}  
  
2.  Eseguire il file .exe tramite il / disinstallare/forzare i parametri della riga di comando.  
  
     Ad esempio, eseguire ```vs_enterprise.exe /uninstall /force```, che verranno rimossi Visual Studio e la maggior parte dei componenti di base residui in una disinstallazione predefinita. Tuttavia, non verranno rimossi tutti i contenuti aggiuntivi che i componenti aggiuntivi di Visual Studio e le estensioni installabili (ad esempio, gli aggiornamenti di Visual Studio e altri componenti facoltativi).  
  
    > [!TIP]
    > In alternativa, è possibile usare la "**programma di disinstallazione totale**" strumento per rimuovere tutti gli elementi che Visual Studio o aggiornamenti di Visual Studio potrebbero essere installato. Vale a dire, qualsiasi versione di Visual Studio 2013 o versione successiva. Per altre informazioni, vedere la [dello strumento di disinstallazione di Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases) su GitHub.  
  
#### <a name="to-uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Per disinstallare Visual Studio in modalità invisibile all'utente o passiva (vale a dire, disinstallazione dall'origine)  
  
1.  Nel computer in cui è installato Visual Studio aprire il prompt dei comandi di Windows.  
  
2.  Immettere i seguenti parametri:  
  
     *DVDRoot* \\< File di installazione\> \<lightweightserver /quiet&#124;o passiva > [/norestart] /Uninstall  
  
#### <a name="to-roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Eseguire il rollback a una versione precedente o una versione di Visual Studio  
  
1.  Disinstalla Visual Studio usando uno dei metodi elencati in questo argomento.  
  
    > [!WARNING]
    >  Disinstallazione di una versione corrente di Visual Studio (o un aggiornamento di Visual Studio) e quindi installare una versione precedente potrebbero non funzionare come previsto.  
    >   
    >  Il risultato dipende da quale versione o rilascio di Visual Studio è installato, quali versioni dei relativi componenti vengono installate, quali prodotti sono installati con dipendenze sia la versione di Visual Studio o i relativi componenti, e infine su la versione di Visual Studio precedenti si intende installare o reinstallare.  A causa di tutte queste variabili, una disinstallazione standard saranno spesso non rimuoverà che alcuni componenti potrebbero non funzionare con versioni o versioni precedenti di Visual Studio.  
    >   
    >  Pertanto, per ottenere risultati ottimali, è consigliabile usare la [dello strumento di disinstallazione di Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases).  
  
2.  Installare o reinstallare la versione precedente di Visual Studio che si desidera utilizzare.  
  
 Anche se si installa una versione precedente di Visual Studio, il programma di installazione potrebbe comunque provare a usare una versione più recente o release se disponibile. Per informazioni più dettagliate, vedere la [procedura: installare una versione specifica di Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md) argomento.  
  
## <a name="see-also"></a>Vedere anche  
 [Installare Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)