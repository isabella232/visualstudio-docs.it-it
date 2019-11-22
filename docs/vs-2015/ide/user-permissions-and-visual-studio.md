---
title: Autorizzazioni utente | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
ms.assetid: 70485ed7-6342-41bf-8250-7a6826e21b98
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dc49a628cdf5695df7744295d2c1d990986bcfbe
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 11/21/2019
ms.locfileid: "74295628"
---
# <a name="user-permissions-and-visual-studio"></a>Autorizzazioni utente e Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Per motivi di sicurezza è necessario, quando possibile, eseguire Visual Studio come utente normale.

> [!WARNING]
> Accertarsi inoltre di non compilare, avviare o eseguire il debug di una soluzione di Visual Studio che non provenga da una persona o un percorso attendibile.

 È possibile usare quasi tutte le funzioni dell'IDE di Visual Studio come utente normale, tuttavia è necessario disporre delle autorizzazioni di amministratore per completare le seguenti attività:

|Area|Attività|Per altre informazioni|
|----------|----------|--------------------------|
|Installazione|Installazione di Visual Studio.|[Installazione di Visual Studio 2015](../install/install-visual-studio-2015.md)|
||Aggiornamento da una versione di valutazione di Visual Studio.|[Procedura: Eseguire l'aggiornamento da una versione di valutazione di Visual Studio](../install/how-to-upgrade-from-a-trial-edition-of-visual-studio.md)|
||Installazione, aggiornamento o rimozione del contenuto della Guida locale.|[Installare e gestire il contenuto locale](../ide/install-and-manage-local-content.md)|
|Tipi di applicazioni|Sviluppo di soluzioni per SharePoint 2010.|[Requisiti per lo sviluppo di soluzioni SharePoint](https://msdn.microsoft.com/library/ae8ff69d-4540-4380-ab0b-845f7108e89c)|
||Acquisizione di una licenza per sviluppatori per [!INCLUDE[win8_appstore_long](../includes/win8-appstore-long-md.md)].|[Ottenere una licenza per sviluppatori (app di Windows Store)](https://go.microsoft.com/fwlink/?LinkID=241313)|
|Casella degli strumenti|Aggiunta di controlli COM classici alla **Casella degli strumenti**.|[Uso della Casella degli strumenti](../ide/using-the-toolbox.md)|
|Componenti aggiuntivi|Installazione e utilizzo di componenti aggiuntivi scritti tramite COM classico nell'IDE.|[Creazione di componenti aggiuntivi e di procedure guidate](https://msdn.microsoft.com/library/c5a47c21-6668-4de3-898d-afa969317e73)|
|Compilazione|Utilizzo di eventi di post-compilazione che registrano un componente.|[Informazioni sulle istruzioni di compilazione personalizzate e sugli eventi di compilazione](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
||Aggiunta di un passaggio di registrazione durante la compilazione di progetti C++.|[Informazioni sulle istruzioni di compilazione personalizzate e sugli eventi di compilazione](https://msdn.microsoft.com/library/beb2f017-3e9f-4b2c-9b57-2572fd2628e4)|
|Debug|Debug di applicazioni eseguite con autorizzazioni elevate.|[Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)|
||Debug di applicazioni eseguite con un account utente diverso, come i siti Web ASP.NET.|[Debug di applicazioni ASP.NET e AJAX](../debugger/debugging-aspnet-and-ajax-applications.md)|
||Debug nell'area di sicurezza per applicazioni browser XAML (XBAP).|[Host WPF (PresentationHost.exe)](https://msdn.microsoft.com/library/3215bfa1-722c-4ac8-a7c5-bdd02d30afbd)|
||Utilizzo dell'emulatore per eseguire il debug di progetti di servizio cloud per Microsoft Azure.|[Debug di un servizio cloud in Visual Studio](https://go.microsoft.com/fwlink/?LinkId=266725)|
||Configurazione di un firewall per il debug remoto.|[Impostare Remote Tools sul dispositivo](https://msdn.microsoft.com/library/90f45630-0d26-4698-8c1f-63f85a12db9c)|
|Strumenti per le prestazioni|Profilatura di un'applicazione.|[Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md)|
|Distribuzione|Distribuzione di un'applicazione Web in Internet Information Services (IIS) su un computer locale.|[Deploying an ASP.NET Web Application to a Hosting Provider using Visual Studio or Visual Web Developer: Deploying to IIS as a Test Environment](https://go.microsoft.com/fwlink/?LinkId=266478) (Distribuzione di un'applicazione Web ASP.NET a un provider di hosting usando Visual Studio o Visual Web Developer: distribuzione a IIS come ambiente di test)|
|Invio di feedback a Microsoft|Modifica delle modalità di partecipazione al programma Analisi utilizzo software di Visual Studio.|[How to: Send Feedback](../misc/how-to-send-feedback-about-visual-studio.md) (Procedura: Inviare commenti e suggerimenti)|

## <a name="running-visual-studio-as-an-administrator"></a>Esecuzione di Visual Studio come amministratore
 È possibile avviare Visual Studio con autorizzazioni amministrative ogni volta che si avvia l'IDE oppure modificare il collegamento dell'applicazione in modo che venga eseguita sempre con autorizzazioni amministrative. Per altre informazioni, vedere la Guida di Windows.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin8includeswin8-mdmd-includewin81includeswin81-mdmd-includewinserver8includeswinserver8-mdmd-or-includewinblue_server_2includeswinblue-server-2-mdmd"></a>Per eseguire Visual Studio con autorizzazioni amministrative in [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[win81](../includes/win81-md.md)], [!INCLUDE[winserver8](../includes/winserver8-md.md)] o [!INCLUDE[winblue_server_2](../includes/winblue-server-2-md.md)]

1. Nella schermata **iniziale** digitare **Visual Studio**. Verrà visualizzata la versione o le versioni di Visual Studio installate.

2. Selezionare la versione di Visual Studio che si desidera avviare, quindi visualizzare il menu di scelta rapida (nella parte inferiore dello schermo). Scegliere **Esegui come amministratore**.

     All'avvio di Visual Studio, viene visualizzato **(Amministratore)** dopo il nome del prodotto nella barra del titolo.

#### <a name="to-run-visual-studio-with-administrative-permissions-on-includewin7includeswin7-mdmd-or-includewinsvr08_r2includeswinsvr08-r2-mdmd"></a>Per eseguire Visual Studio con autorizzazioni amministrative in [!INCLUDE[win7](../includes/win7-md.md)] o [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]

1. Dal menu **Start** scegliere **Tutti i programmi**.

2. Nella cartella **Microsoft Visual Studio** *Versione* selezionare **Visual Studio** *Versione*, aprire il menu di scelta rapida e quindi selezionare **Esegui come amministratore**.

     All'avvio di Visual Studio, viene visualizzato **(Amministratore)** dopo il nome del prodotto nella barra del titolo.

## <a name="see-also"></a>Vedere anche
 [Portabilità, migrazione e aggiornamento dei progetti di Visual Studio](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) [Installazione di Visual Studio 2015](../install/install-visual-studio-2015.md)
