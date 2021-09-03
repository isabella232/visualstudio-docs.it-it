---
title: Distribuire in Azure con GitHub Actions
description: Informazioni su come distribuire l'applicazione in Azure usando i flussi GitHub actions creati da Visual Studio
ms.date: 08/31/2021
ms.topic: tutorial
helpviewer_keywords:
- deployment, GitHub Actions
- GitHub Actions, publish
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-deployment
monikerRange: '>= vs-2019'
ms.workload:
- multiple
ms.openlocfilehash: fa9a9a8d052a4003dc15b454df21b90cf956d069
ms.sourcegitcommit: 9a340611faaaa143946b3ede66ee84ec19108b09
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2021
ms.locfileid: "123423057"
---
# <a name="deploy-your-application-to-azure-using-github-actions-workflows-created-by-visual-studio"></a>Distribuire l'applicazione in Azure usando i flussi GitHub actions creati da Visual Studio
A partire Visual Studio 2019 versione 16.11, è possibile creare nuovi flussi di lavoro di GitHub Action per i progetti .NET ospitati in GitHub.com.

## <a name="how-does-it-work"></a>Come funziona?
In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto ospitato GitHub.com e scegliere **Pubblica**

![Fare clic con il pulsante destro del > pubblica](./media/solution-explorer-publish.png)

Nella schermata successiva selezionare **Azure e** **Avanti**

![Selezionare Azure](./media/wizard-azure.png)

A seconda del [tipo di progetto,](#which-project-types-are-supported) si ottiene un elenco diverso di servizi di Azure tra cui scegliere. Scegliere uno dei [servizi di Azure supportati](#which-azure-services-are-supported) in base alle proprie esigenze.

![Selezionare il servizio di Azure appropriato per il progetto](./media/wizard-pick-azure-service.png)

Nel passaggio finale della procedura guidata selezionare CI/CD usando i flussi di lavoro di GitHub Actions (genera il **file yml)** e quindi scegliere **Fine.**

![CI/CD con flussi GitHub Actions (genera il file yml)](./media/wizard-final-step.png)

Visual Studio genera un nuovo flusso di lavoro GitHub Actions e chiede di eseguirne il commit ed eseguirne il push in GitHub.com.

![commit e push](./media/summary-commit-and-push.png)

Se si completa questo passaggio usando [gli strumenti Git](../version-control/git-with-visual-studio.md#git-changes-window) predefiniti Visual Studio rileverà l'esecuzione del flusso di lavoro.

![flusso di lavoro in esecuzione](./media/summary-workflow-running.png)

## <a name="setting-the-github-secrets"></a>Impostazione dei GitHub segreti
Per la corretta distribuzione del flusso di lavoro generato in Azure, potrebbe essere necessario l'accesso a un [profilo di pubblicazione](/azure/app-service/deploy-github-actions?tabs=applevel#configure-the-github-secret) 

![un segreto GitHub](./media/summary-one-github-secret.png)

Una distribuzione corretta può anche richiedere l'accesso a [un'entità servizio](/azure/app-service/deploy-github-actions?tabs=userlevel#configure-the-github-secret)

![due segreti github](./media/summary-two-github-secrets.png)

In tutti i casi, Visual Studio tenta di impostare il GitHub segreto per conto dell'utente con il valore corretto. In caso di errore, verrà visualizzato un messaggio che offre la possibilità di riprovare.

![Segreto GitHub mancante](./media/summary-one-github-secret-missing.png)

Se non riesce a impostare nuovamente il segreto, Visual Studio offre la possibilità di ottenere l'accesso al segreto manualmente, in modo da poter completare il processo tramite la pagina del github.com.

![impostare il segreto GitHub mancante](./media/summary-set-github-secret.png)

## <a name="which-project-types-are-supported"></a>Quali tipi di progetto sono supportati?
 * ASP.NET Core
 * ASP.NET 5 e successive
 * Funzioni di Azure

## <a name="which-azure-services-are-supported"></a>Quali servizi di Azure sono supportati?
* App Web di Azure
* Funzioni di Azure
* Gestione API di Azure
