---
title: Creare un ASP.NET Core app con Vue
description: In questa esercitazione si crea un'app usando ASP.NET Core e Vue
ms.date: 08/09/2021
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
ms.openlocfilehash: 50ee00867e6729c269753edeb0cdfa44f3215c3f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122027912"
---
# <a name="tutorial-create-an-aspnet-core-app-with-vue-in-visual-studio"></a>Esercitazione: Creare un'app ASP.NET Core con Vue in Visual Studio

Questo articolo illustra come compilare un progetto ASP.NET Core per fungere da back-end dell'API e come progetto Vue come interfaccia utente.

Attualmente, Visual Studio modelli ASP.NET Core applicazione a pagina singola che supportano Angular, React e Vue. I modelli forniscono una cartella predefinita dell'app client nei progetti ASP.NET Core che contiene i file e le cartelle di base di ogni framework.

A partire Visual Studio 2022 Preview 2, è possibile usare il metodo descritto in questo articolo per creare ASP.NET Core a pagina singola che:

- Inserire l'app client in un progetto separato, all'esterno del ASP.NET Core progetto
- Creare il progetto client in base all'interfaccia della riga di comando del framework installata nel computer

## <a name="prerequisites"></a>Prerequisiti

Assicurarsi di avere installato quanto segue:

- Visual Studio 2022 Preview 2 o versione successiva con il carico di **lavoro ASP.NET sviluppo** Web e web installato. Passare alla pagina [Visual Studio download per](https://visualstudio.microsoft.com/downloads/) installarlo gratuitamente.
  Se è necessario installare il carico di lavoro e si dispone già di Visual Studio, passare a Strumenti Ottieni strumenti e  >  **funzionalità...**, che apre il Programma di installazione di Visual Studio. Scegliere il carico di lavoro **Sviluppo ASP.NET e Web**, quindi scegliere **Cambia**.
- npm ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Interfaccia della riga di comando di Vue ( [https://cli.vuejs.org/](https://cli.vuejs.org/) )  

## <a name="create-the-frontend-app"></a>Creare l'app front-end

1. Nella finestra di dialogo Project nuovo progetto selezionare **Crea un nuovo progetto**. 

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Creare un nuovo progetto":::

1. Cercare Vue nella barra di ricerca nella parte superiore e quindi selezionare **Modello Vue JavaScript** autonomo o Modello **Vue TypeScript autonomo.**

   :::image type="content" source="media/vs-2022/vue-choose-template.png" alt-text="Scelta di un modello":::

1. Assegnare un nome al progetto e alla soluzione. Quando si arriva alla **finestra Informazioni** aggiuntive, assicurarsi di selezionare l'opzione Aggiungi integrazione **per** API Web ASP.NET Project vuota. Questa opzione aggiunge file al modello Vue in modo che possa essere collegato in un secondo momento con il ASP.NET Core progetto.

   :::image type="content" source="media/vs-2022/asp-net-core-vue-additional-info.png" alt-text="Informazioni aggiuntive":::

Dopo aver creato il progetto, vengono visualizzati alcuni file nuovi e modificati:

- aspnetcore-https.js
- vue.config.jssu (modificato)
- HelloWorld.vue (modificato)
- package.jssu (modificato)

## <a name="create-the-backend-app"></a>Creare l'app back-end

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul nome della soluzione, passare il mouse su Aggiungi **e** **quindi selezionare Nuovo Project**. 

   :::image type="content" source="media/vs-2022/asp-net-core-add-project.png" alt-text="Aggiungere un nuovo progetto":::

1. Cercare e selezionare il progetto ASP.NET Core'API Web.
 
   :::image type="content" source="media/vs-2022/asp-net-core-choose-web-api-template.png" alt-text="Scegliere il modello api Web":::

1. Assegnare un nome al progetto e alla soluzione. Quando si arriva alla **finestra Informazioni** aggiuntive, selezionare **.NET 6.0** come framework di destinazione.

   Dopo aver creato il progetto, Esplora soluzioni dovrebbe essere simile al seguente:

   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-solution-explorer.png" alt-text="Esaminare le Esplora soluzioni":::

## <a name="set-the-project-properties"></a>Impostare le proprietà del progetto

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul ASP.NET Core progetto e scegliere **Proprietà**.

   :::image type="content" source="media/vs-2022/asp-net-core-project-properties.png" alt-text="Aprire le proprietà del progetto"::: 
 
1. Passare al menu Debug e selezionare l'opzione **Apri profili di avvio debug dell'interfaccia** utente. Deselezionare **l'opzione Avvia browser.**

   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-deselect-launch-browser.png" alt-text="Aprire l'interfaccia utente dei profili di avvio di debug"::: 

1. Fare quindi clic con il pulsante destro del mouse sul progetto Vue e **scegliere** il menu Proprietà e passare alla **sezione** Debug. Modificare debugger per avviare l'opzione **launch.jsattivata.**
 
   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-choose-debugger.png" alt-text="Scegliere il debugger (launch.jssu)":::

## <a name="set-the-startup-project"></a>Impostare il progetto di avvio

1. Fare clic con il pulsante destro del mouse sulla soluzione e **scegliere Imposta avvio Project**. Modificare il progetto di avvio da Progetto di avvio singolo a **Progetti di avvio multipli**. Selezionare **Avvia** per ogni azione del progetto.
  
1. Selezionare quindi il progetto back-end e spostarlo sopra il front-end, in modo da avviarlo per primo.

   :::image type="content" source="media/vs-2022/asp-net-core-with-vue-set-first-project.png" alt-text="Scegliere il primo progetto di avvio":::

## <a name="start-the-project"></a>Avviare il progetto

Premere **F5** o selezionare il **pulsante Avvia** nella parte superiore della finestra. Verranno visualizzati due prompt dei comandi:

- Progetto api ASP.NET Core in esecuzione
- L'interfaccia della riga di comando di Vue che esegue il comando vue-cli-service serve

Verrà visualizzata un'app Vue popolata tramite l'API.

## <a name="troubleshooting"></a>Risoluzione dei problemi

Può essere visualizzato l'errore seguente:

```
[HPM] Error occurred while trying to proxy request /weatherforecast from localhost:4200 to https://localhost:5001 (ECONNREFUSED) (https://nodejs.org/api/errors.html#errors_common_system_errors)
```

Se si verifica questo problema, molto probabilmente il front-end è stato avviato prima del back-end. Dopo aver visualizzato il prompt dei comandi back-end in esecuzione, è sufficiente aggiornare l'app Vue nel browser.