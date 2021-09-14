---
title: Creare un'app Vue.js
description: Questa esercitazione illustra come creare una semplice applicazione Vue.js in Visual Studio.
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
ms.openlocfilehash: 926051ad98d43715a15a20091eb6a17c20f96758
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/13/2021
ms.locfileid: "126635891"
---
# <a name="create-a-vuejs-app"></a>Creare un'app Vue.js

In questa introduzione di 5-10 minuti all'ambiente Visual Studio di sviluppo integrato (IDE, Integrated Development Environment) si crea ed esegue una semplice Vue.js'applicazione Web front-end.

## <a name="prerequisites"></a>Prerequisiti

Assicurarsi che siano installati gli elementi seguenti:

- Visual Studio 2022 Preview 2 o versione successiva. Passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
- npm ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Vue.js ([Installation | Vue.js (vuejs.org) )](https://v3.vuejs.org/guide/installation.html#npm)
- Vue.js cli ([(Installation | Vue.js (vuejs.org)](https://v3.vuejs.org/guide/installation.html#cli))

## <a name="create-your-app"></a>Creare l'app

1. Nella finestra di dialogo Project nuovo progetto selezionare **Crea un nuovo progetto.**

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Creare un nuovo progetto":::

1. Cercare Vue nella barra di ricerca nella parte superiore e quindi selezionare **Standalone JavaScript Vue Template** (Modello JavaScript Vue autonomo) o **Standalone TypeScript Vue Template**(Modello Vue TypeScript autonomo), in base alle proprie preferenze.

   :::image type="content" source="media/vs-2022/vue-choose-template.png" alt-text="Scelta di un modello":::

1. Assegnare un nome al progetto e alla soluzione. 

## <a name="set-the-project-properties"></a>Impostare le proprietà del progetto

1. In Esplora soluzioni fare clic con il pulsante destro del mouse Vue.js progetto, scegliere **Proprietà** e quindi passare alla **sezione** Debug.

1. Modificare debugger per l'avvio con **l'opzione launch.json.**
 
   :::image type="content" source="media/vs-2022/vue-choose-debugger.png" alt-text="Scegliere il debugger (launch.json)":::

## <a name="build-your-project"></a>Creare il Project

Scegliere **Compila**  >  **compila soluzione** per compilare il progetto.

## <a name="start-your-project"></a>Avviare il Project

Premere **F5** o selezionare il **pulsante Avvia** nella parte superiore della finestra. Viene visualizzato un prompt dei comandi:

- npm che esegue il comando vue-cli-service start

Verrà quindi visualizzata l'app di base Vue.js app.