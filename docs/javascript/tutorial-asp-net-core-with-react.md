---
title: Creare un'app ASP.NET Core con React
description: In questa esercitazione si creerà un'app usando ASP.NET Core e React
ms.date: 07/19/2021
ms.topic: tutorial
ms.devlang: javascript
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-javascript
dev_langs:
- JavaScript
ms.workload:
- nodejs
monikerRange: '>= vs-2022'
ms.openlocfilehash: 4d6fefdda40e550a62616a82734a84037c0c10b0
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077920"
---
# <a name="tutorial-create-an-aspnet-core-app-with-react-in-visual-studio"></a>Esercitazione: Creare un'app ASP.NET Core con React in Visual Studio

In questo articolo si apprenderà come compilare un progetto di ASP.NET Core da fungere da back-end api e un progetto di React da fungere da interfaccia utente.

Attualmente, Visual Studio include ASP.NET Core di applicazione a pagina singola che supportano Angular e React. I modelli forniscono una cartella app client predefinita nei progetti ASP.NET Core che contiene i file e le cartelle di base di ogni framework.

A partire Visual Studio 2022 Preview 2, è possibile usare il metodo descritto in questo articolo per creare ASP.NET Core a pagina singola che:

- Inserire l'app client in un progetto separato, all'esterno ASP.NET Core progetto
- Creare il progetto client in base all'interfaccia della riga di comando del framework installata nel computer

## <a name="prerequisites"></a>Prerequisiti

Assicurarsi che siano installati gli elementi seguenti:

- Visual Studio 2022 Preview 2 o versione successiva con il carico di lavoro ASP.NET **e sviluppo** Web installato. Passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
  Se è necessario installare il carico di lavoro e si dispone già di Visual Studio, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web**, quindi scegliere **Cambia**.
- npm ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- npx ( [https://www.npmjs.com/package/npx](https://www.npmjs.com/package/npx) )

## <a name="create-the-frontend-app"></a>Creare l'app front-end

1. Nella finestra di dialogo Project nuovo progetto selezionare **Crea un nuovo progetto.** 

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Creare un nuovo progetto":::

1. Cercare React nella barra di ricerca nella parte superiore e quindi selezionare **Standalone JavaScript React Template**(Modello javascript autonomo). Il modello di React TypeScript autonomo non è attualmente supportato in questa esercitazione.

   :::image type="content" source="media/vs-2022/react-choose-template.png" alt-text="Scelta di un modello":::

1. Assegnare un nome al progetto e alla soluzione. Quando si arriva alla finestra **Informazioni aggiuntive,** assicurarsi di selezionare l'opzione Aggiungi integrazione per API Web ASP.NET Project **vuota.** Questa opzione aggiunge file al modello React in modo che possa essere associato in un secondo momento al ASP.NET Core progetto.

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-additional-info.png" alt-text="Informazioni aggiuntive":::

   Dopo aver creato il progetto, vengono visualizzati alcuni file nuovi e modificati:

   - aspnetcore-https.js
   - aspnetcore-react.js
   - setupProxy.js
   - App.js (modificato)
   - App.test.js (modificato)

## <a name="create-the-backend-app"></a>Creare l'app back-end

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nome della soluzione, passare il mouse su Aggiungi **e** quindi **scegliere Project**. 

   :::image type="content" source="media/vs-2022/asp-net-core-add-project.png" alt-text="Aggiungere un nuovo progetto":::

1. Cercare e selezionare il progetto ASP.NET Core'API Web.
 
   :::image type="content" source="media/vs-2022/asp-net-core-choose-web-api-template.png" alt-text="Scegliere il modello API Web":::

1. Assegnare un nome al progetto e alla soluzione. Quando si arriva alla **finestra Informazioni** aggiuntive, selezionare **.NET 6.0** come framework di destinazione.

   Dopo aver creato il progetto, Esplora soluzioni dovrebbe essere simile al seguente:

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-solution-explorer.png" alt-text="Diamo un'occhiata Esplora soluzioni":::

## <a name="set-the-project-properties"></a>Impostare le proprietà del progetto

1. Fare clic con il pulsante destro ASP.NET Core progetto e scegliere **Proprietà.**

   :::image type="content" source="media/vs-2022/asp-net-core-project-properties.png" alt-text="Aprire le proprietà del progetto"::: 
 
1. Passare al menu Debug e selezionare l'opzione **Open debug launch profiles UI (Apri profili di avvio debug dell'interfaccia** utente). Deselezionare **l'opzione Avvia** browser.

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-deselect-launch-browser.png" alt-text="Aprire l'interfaccia utente dei profili di avvio del debug"::: 

1. Fare quindi clic con il pulsante destro del React progetto, scegliere **Proprietà** e passare alla **sezione** Debug. Modificare debugger per avviare l'opzione **launch.jsattivata.**
 
   :::image type="content" source="media/vs-2022/asp-net-core-with-react-choose-debugger.png" alt-text="Scegliere il debugger (launch.jssì)":::

## <a name="set-the-startup-project"></a>Impostare il progetto di avvio

1. Fare clic con il pulsante destro del mouse sulla soluzione e **scegliere Imposta avvio Project**. Modificare il progetto di avvio da Progetto di avvio singolo a **Progetti di avvio multipli**. Selezionare **Avvia** per ogni azione del progetto.
  
1. Selezionare quindi il progetto back-end e spostarlo sopra il front-end, in modo che sia avviato per primo.

   :::image type="content" source="media/vs-2022/asp-net-core-with-react-startup-project.png" alt-text="Scegliere il progetto di avvio":::

## <a name="start-the-project"></a>Avviare il progetto

Premere **F5** o selezionare il **pulsante Avvia** nella parte superiore della finestra. Verranno visualizzati due prompt dei comandi:

- Progetto API ASP.NET Core in esecuzione
- npm che esegue il comando react-scripts start

Dovrebbe essere visualizzata una React app, popolata tramite l'API.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Può essere visualizzato l'errore seguente:

```
[HPM] Error occurred while trying to proxy request /weatherforecast from localhost:4200 to https://localhost:5001 (ECONNREFUSED) (https://nodejs.org/api/errors.html#errors_common_system_errors)
```

Se si verifica questo problema, molto probabilmente il front-end è stato avviato prima del back-end. Quando il prompt dei comandi back-end è in esecuzione, è sufficiente aggiornare l React app nel browser.
