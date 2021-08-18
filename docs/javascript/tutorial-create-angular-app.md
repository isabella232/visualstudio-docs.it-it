---
title: Creare un'app Angular app
description: Questa esercitazione illustra come creare un'applicazione Angular semplice in Visual Studio.
ms.date: 07/30/2021
ms.custom: vs-acquisition
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
ms.openlocfilehash: 1b40a03c63665be09ecea5c28fb8e82dcc69c7a7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122077751"
---
# <a name="create-an-angular-app"></a>Creare un'app Angular app

In questa introduzione di 5-10 minuti all'ambiente Visual Studio di sviluppo integrato (IDE) viene creata ed eseguita una semplice applicazione Web Angular front-end.

## <a name="prerequisites"></a>Prerequisiti

Assicurarsi di avere installato quanto segue:

- Visual Studio 2022 Preview 2 o versione successiva. Passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
- npm ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Angular Interfaccia della riga di comando ( [https://angular.io/cli](https://angular.io/cli) ) Può essere la versione scelta

## <a name="create-your-app"></a>Creare l'app

1. Nella finestra di dialogo Project nuovo progetto selezionare **Crea un nuovo progetto**.

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Creare un nuovo progetto":::

1. Cercare Angular nella barra di ricerca nella parte superiore e quindi selezionare **Modello Angular autonomo**.

   :::image type="content" source="media/vs-2022/angular-choose-template.png" alt-text="Scelta di un modello":::

1. Assegnare un nome al progetto e alla soluzione. 

   Quando si arriva alla finestra Informazioni aggiuntive assicurarsi DI NON selezionare l'opzione Aggiungi integrazione **per** API Web ASP.NET Project vuoto. Questa opzione aggiunge file al modello Angular in modo che possa essere collegato al progetto ASP.NET Core, se viene aggiunto un ASP.NET Core progetto.

   :::image type="content" source="media/vs-2022/angular-additional-info.png" alt-text="Informazioni aggiuntive":::

## <a name="set-the-project-properties"></a>Impostare le proprietà del progetto

1. In Esplora soluzioni fare clic con il pulsante destro del mouse Angular progetto, scegliere Proprietà **e** quindi passare alla **sezione** Debug.

1. Modificare debugger per avviare l'opzione **launch.jsattivata.**
 
   :::image type="content" source="media/vs-2022/angular-choose-debugger.png" alt-text="Scegliere il debugger (launch.jssu)":::

## <a name="build-your-project"></a>Creare il Project

Scegliere **Compila**  >  **soluzione per** compilare il progetto.

Si noti che la compilazione iniziale potrebbe richiedere del tempo, in quanto l'interfaccia della Angular comando eseguirà il comando npm install.

## <a name="start-your-project"></a>Avviare la Project

Premere **F5** o selezionare il **pulsante Avvia** nella parte superiore della finestra. Viene visualizzato un prompt dei comandi:

- Interfaccia Angular comando che esegue il comando ng start

Verrà quindi visualizzata l'app di base Angular app.