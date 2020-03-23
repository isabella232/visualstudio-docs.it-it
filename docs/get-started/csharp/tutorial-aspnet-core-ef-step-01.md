---
title: App Web ASP.NET Core con Entity Framework e Visual Studio 2019
titleSuffix: ''
description: Come primo passaggio prima della creazione di un'app Web ASP.NET Core, scoprire come installare Visual Studio 2019 con questa esercitazione video e istruzioni dettagliate.
ms.custom: get-started
ms.date: 03/31/2019
ms.technology: vs-ide-general
ms.prod: visual-studio-windows
monikerRange: vs-2019
ms.topic: tutorial
ms.devlang: CSharp
author: ardalis
ms.author: ornella
manager: jillfra
dev_langs:
- CSharp
ms.workload:
- aspnet
- dotnetcore
ms.openlocfilehash: d900c0f51b14450f38caf06738739daef2549235
ms.sourcegitcommit: 2975d722a6d6e45f7887b05e9b526e91cffb0bcf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/20/2020
ms.locfileid: "77580097"
---
# <a name="tutorial-create-your-first-aspnet-core-app-using-entity-framework-with-visual-studio-2019"></a>Esercitazione: Creare la prima app di base ASP.NET usando Entity Framework con Visual Studio 2019Tutorial: Create your first ASP.NET Core App using Entity Framework with Visual Studio 2019

In questa esercitazione verrà creata un'app Web ASP.NET Core che usa i dati e l'app verrà distribuita in Azure. L'esercitazione è costituita dai passaggi seguenti:

- [Passaggio 1: Installare Visual Studio 2019Step 1: Install Visual Studio 2019](#step-1-install-visual-studio-2019)
- [Passaggio 2: Creare la prima app Web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md)
- [Passaggio 3: Usare i dati con Entity FrameworkStep 3: Work with data using Entity Framework](tutorial-aspnet-core-ef-step-03.md)
- [Passaggio 4: Esporre un'API Web dall'app ASP.NET CoreStep 4: Expose a web API from your ASP.NET Core app](tutorial-aspnet-core-ef-step-04.md)
- [Passaggio 5: Distribuire l'app ASP.NET Core in AzureStep 5: Deploy your ASP.NET Core app to Azure](tutorial-aspnet-core-ef-step-05.md)

## <a name="step-1-install-visual-studio-2019"></a>Passaggio 1: Installare Visual Studio 2019Step 1: Install Visual Studio 2019

Scoprire come installare Visual Studio 2019 con questa esercitazione video e le istruzioni dettagliate. Se Visual Studio è già stato installato, andare al [Passaggio 2: Creare la prima app Web ASP.NET Core](tutorial-aspnet-core-ef-step-02.md).

_Guardare questo video e seguire le indicazioni per installare Visual Studio e creare la prima app ASP.NET Core._

> [!VIDEO https://www.youtube.com/embed/Fz_HAqQGLtY]

## <a name="download-the-installer"></a>Scaricare il programma di installazione

Passare a [visualstudio.com](https://visualstudio.com) per trovare il programma di installazione. Individuare il collegamento di Visual Studio 2019 e fare clic su di esso per avviare il download. Per una versione gratuita di Visual Studio, scegliere Visual Studio Community.

## <a name="start-the-installer"></a>Avviare il programma di installazione

Al termine del download, fare clic su **Esegui** per avviare il programma di installazione.

![Programma di installazione di Visual Studio 2019](media/vs-2019/vs2019-installer.png)

## <a name="choose-workloads"></a>Scegliere i carichi di lavoro

È possibile usare Visual Studio per molti tipi diversi di attività di sviluppo e i carichi di lavoro rendono più semplice il download di tutti i componenti necessari per il tipo di app da creare. Per il momento scegliere i carichi di lavoro **Sviluppo ASP.NET e Web** e **Sviluppo multipiattaforma .NET Core**. È sempre possibile riavviare il programma di installazione in un secondo momento per installare altri carichi di lavoro e componenti.

![Visual Studio 2019 - Scegliere i carichi di lavoro](media/vs-2019/vs2019-choose-workloads.png)

## <a name="install"></a>Installazione

Fare clic su **Installa** e lasciare che il programma di installazione scarichi e installi Visual Studio.

## <a name="run-visual-studio-for-the-first-time"></a>Eseguire Visual Studio per la prima volta

Visual Studio verrà avviato automaticamente al termine del programma di installazione. Potrebbe essere richiesto di eseguire l'accesso, per usufruire di alcune funzionalità interessanti. Per il momento, tuttavia, scegliere di farlo in un secondo momento. È poi possibile scegliere il tema e le impostazioni per lo sviluppo. Dopo aver fatto queste scelte, si sarà pronti per iniziare il primo progetto. Fare clic su **Crea un nuovo progetto** e quindi scegliere **Applicazione Web ASP.NET Core**.

![Visual Studio 2019 - Creare un nuovo progetto per applicazione Web ASP.NET Core](media/vs-2019/vs2019-create-new-project.png)

## <a name="explore-aspnet-core-project-types"></a>Esplorare i tipi di progetto ASP.NET Core

È possibile scegliere il nome del progetto e il percorso, quindi scegliere **Crea**. A questo punto, scegliere il modello da usare per l'applicazione ASP.NET Core. È possibile scegliere tra le opzioni seguenti:

- Vuoto. Modello di progetto vuoto che consente di iniziare da zero.
- . Ideale per le API Web.
- Applicazione Web. Un'applicazione Web ASP.NET Core standard creata con Razor Pages.
- Applicazione Web (MVC). Un'applicazione Web ASP.NET Core standard creata con il modello MVC (Model-View-Controller).
- Angular.
- React.js.
- React.js / Redux.
- Libreria di classi Razor. Usata per condividere gli asset di Razor tra progetti.

Si noti che per la maggior parte dei modelli di progetto è anche possibile scegliere di abilitare il supporto di Docker selezionando una casella di controllo. Si può anche aggiungere il supporto per l'autenticazione facendo clic sul pulsante Modifica autenticazione. Da qui è possibile scegliere tra:

- Nessuna autenticazione.
- Account utente individuali. Questi vengono archiviati in un database locale o basato su Azure.
- Account aziendali o dell'istituto di istruzione. Questa opzione usa Active Directory, Azure AD o Office 365 per l'autenticazione.
- Autenticazione di Windows. Adatta per le applicazioni Intranet.

Selezionare il modello di applicazione Web standard senza autenticazione e fare clic su **Crea**.

![Visual Studio 2019 - Scegliere le opzioni per il progetto ASP.NET Core](media/vs-2019/vs2019-choose-aspnetcore-project.png)

## <a name="next-steps"></a>Passaggi successivi

Nel prossimo video verranno presentate ulteriori informazioni sul primo progetto ASP.NET Core.

[Esercitazione: Creazione della prima ASP.NET'app Web di base](tutorial-aspnet-core-ef-step-02.md)

## <a name="see-also"></a>Vedere anche

- [Esercitazione: Introduzione a C 'NET e ASP.NET CoreTutorial: Get Started with C'è and ASP.NET Core](tutorial-aspnet-core.md) Un'esercitazione più dettagliata senza una procedura dettagliata video
