---
title: Disinstallare Visual Studio 2015 | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-install
ms.topic: conceptual
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: ed9d33501644c6fa7252dffa758f92c0919653b1
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62546902"
---
# <a name="uninstall-visual-studio"></a>Disinstallare Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per la documentazione più recente di Visual Studio, vedere [Disinstallare Visual Studio](/visualstudio/install/uninstall-visual-studio).

In questa pagina viene descritta la procedura di disinstallazione di Visual Studio 2015, una versione precedente della suite integrata di strumenti di produttività per gli sviluppatori.

## <a name="uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Disinstallare Visual Studio usando il metodo di disinstallazione standard

1. Nella pagina **Programmi e funzionalità** del **Pannello di controllo** selezionare l'edizione del prodotto che si vuole disinstallare e fare clic su **Cambia**.

2. Nell'Installazione guidata scegliere **Disinstalla**, scegliere **Sì**, quindi seguire le istruzioni rimanenti.

   Questo metodo standard, o predefinito, lascerà sul sistema alcuni elementi della versione di Visual Studio installata in origine, ad esempio Microsoft .NET Framework, pacchetti ridistribuibili Microsoft Visual C++, Microsoft SQL Server e così via.   Questi elementi vengono lasciati installati perché molte altre applicazioni dipendono da essi. Tuttavia, se si preferisce rimuoverli, selezionare la relativa voce in **Programmi e funzionalità** e quindi disinstallarli singolarmente.

## <a name="uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Disinstallare Visual Studio e tutti gli altri file correlati (disinstallare quasi tutto)

1. Individuare il file eseguibile di Visual Studio (ad esempio, cercare "vs_enterprise.exe").

    > [!NOTE]
    > Il file dovrebbe trovarsi in una sottocartella di "%ProgramData%\Package Cache", ad esempio: C:\ProgramData\Package Cache\\{37e19555-e88d-4aed-9d42-82d0784d2b79}\vs_enterprise.exe

2. Eseguire il file EXE usando i parametri della riga di comando /uninstall /force.

     Ad esempio, eseguire ```vs_enterprise.exe /uninstall /force```, che rimuoverà Visual Studio e la maggior parte dei componenti di base che con una disinstallazione predefinita vengono conservati. Tuttavia, non verranno rimossi tutti i contenuti aggiuntivi che potrebbero essere installati da estensioni e componenti aggiuntivi di Visual Studio, ad esempio, gli aggiornamenti di Visual Studio e altri componenti facoltativi.

    > [!TIP]
    > In alternativa, è possibile usare lo strumento di disinstallazione completa "**Total Uninstaller**" per rimuovere ogni elemento installato da Visual Studio o dai relativi aggiornamenti, cioè qualsiasi versione di Visual Studio 2013 o successive. Per altre informazioni, vedere lo [strumento di disinstallazione di Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases) su GitHub.

## <a name="uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Disinstallare Visual Studio in modalità invisibile all'utente o passiva (disinstallazione dall'origine)

1. Nel computer in cui è installato Visual Studio aprire il prompt dei comandi di Windows.

2. Immettere i seguenti parametri:

     *DVDRoot* \\<File di installazione\> \</quiet&#124;/passive> [/norestart]/uninstall

## <a name="roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Eseguire il rollback a una versione precedente di Visual Studio

1. Disinstallare Visual Studio usando uno dei metodi elencati in questo argomento.

   > [!WARNING]
   > La disinstallazione di una versione corrente di Visual Studio o di un relativo aggiornamento seguita dall'installazione di una versione precedente potrebbe non offrire i risultati sperati.
   >
   > Il risultato dipende dalla versione di Visual Studio installata, da quali versioni dei relativi componenti sono state installate, da quali prodotti installati potrebbero avere dipendenze dalla versione di Visual Studio o dai suoi componenti e, infine, da quale versione precedente di Visual Studio si intende installare o reinstallare.  A causa di tutte queste variabili, una disinstallazione standard spesso non rimuoverà alcuni componenti che potrebbero non funzionare con versioni precedenti di Visual Studio.
   >
   > Di conseguenza, per risultati ottimali, è consigliabile usare lo [strumento di disinstallazione di Visual Studio](https://github.com/Microsoft/VisualStudioUninstaller/releases).

2. Installare o reinstallare la versione precedente di Visual Studio che si vuole usare.

   Anche se si installa una versione precedente di Visual Studio, il programma di installazione potrebbe comunque provare a usare una versione più recente, se disponibile. Per informazioni più dettagliate, vedere [Procedura: Installare una versione specifica di Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md).

## <a name="see-also"></a>Vedere anche

- [Installare Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)