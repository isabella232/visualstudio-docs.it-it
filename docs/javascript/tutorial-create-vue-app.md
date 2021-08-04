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
dev_langs:
- JavaScript
ms.workload:
- nodejs
monikerRange: '>= vs-2022'
ms.openlocfilehash: 33e69c5e828120ab9449296c957ed7c00f71d7e1
ms.sourcegitcommit: 2430a38f23ac17b65dd8d3baa806e90433aba24f
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/04/2021
ms.locfileid: "115095043"
---
# <a name="create-a-vuejs-app"></a>Creare un'app Vue.js

In questa introduzione di 5-10 minuti all'ambiente di sviluppo integrato (IDE) di Visual Studio viene creata ed eseguita una semplice applicazione Web Vue.js front-end.

## <a name="prerequisites"></a>Prerequisiti

Assicurarsi di avere installato quanto segue:

- npm ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- Vue.js ([Installation | Vue.js (vuejs.org)](https://v3.vuejs.org/guide/installation.html#npm))
- Vue.js dell'interfaccia della riga di comando ([(| Vue.js (vuejs.org)](https://v3.vuejs.org/guide/installation.html#cli))

## <a name="create-your-app"></a>Creare l'app

1. Nella finestra di dialogo Project nuovo progetto selezionare **Crea un nuovo progetto**.

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Creare un nuovo progetto":::

1. Cercare Vue nella barra di ricerca nella parte superiore e quindi selezionare **Modello Vue JavaScript** autonomo o Modello **Vue TypeScript** autonomo, in base alle preferenze.

   :::image type="content" source="media/vs-2022/vue-choose-template.png" alt-text="Scelta di un modello":::

1. Assegnare un nome al progetto e alla soluzione. 

## <a name="set-the-project-properties"></a>Impostare le proprietà del progetto

1. In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto Vue.js, scegliere Proprietà **e** quindi passare alla **sezione** Debug.

1. Modificare debugger per avviare l'opzione **launch.jsattivata.**
 
   :::image type="content" source="media/vs-2022/vue-choose-debugger.png" alt-text="Scegliere il debugger (launch.jssu)":::

## <a name="build-your-project"></a>Creare il Project

Scegliere **Compila**  >  **soluzione per** compilare il progetto.

## <a name="start-your-project"></a>Avviare il Project

Premere **F5** o selezionare il **pulsante Avvia** nella parte superiore della finestra. Viene visualizzato un prompt dei comandi:

- npm che esegue il comando vue-cli-service start

Verrà quindi visualizzata l'app di base Vue.js app.