---
title: Creare un'app React predefinita
description: Questa esercitazione illustra come creare una semplice applicazione React in Visual Studio.
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
ms.openlocfilehash: 11d59ac05be469d19a10d68d1a0bc004460d2d385644687f0b58c49c9afd8d59
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/12/2021
ms.locfileid: "121411404"
---
# <a name="create-a-react-app"></a>Creare un'app React predefinita

In questa introduzione di 5-10 minuti all'ambiente Visual Studio di sviluppo integrato (IDE) viene creata ed eseguita una semplice applicazione Web React front-end.

## <a name="prerequisites"></a>Prerequisiti

Assicurarsi di avere installato quanto segue:

- Visual Studio 2022 Preview 2 o versione successiva. Passare alla pagina [Visual Studio download](https://visualstudio.microsoft.com/downloads/) per installarlo gratuitamente.
- npm ( [https://www.npmjs.com/](https://www.npmjs.com/) ) 
- npx ( [https://www.npmjs.com/package/npx](https://www.npmjs.com/package/npx) )

## <a name="create-your-app"></a>Creare l'app

1. Nella finestra di dialogo Project nuovo progetto selezionare **Crea un nuovo progetto**.

   :::image type="content" source="media/vs-2022/create-new-project.png" alt-text="Creare un nuovo progetto":::

1. Cercare React nella barra di ricerca nella parte superiore e quindi selezionare **Modello di React JavaScript** autonomo o Modello di React **TypeScript autonomo, in** base alle preferenze.

   :::image type="content" source="media/vs-2022/react-choose-template.png" alt-text="Scelta di un modello":::

1. Assegnare un nome al progetto e alla soluzione. 

   Se in precedenza è stato selezionato Modello React JavaScript autonomo, quando si arriva alla finestra Informazioni aggiuntive assicurarsi di non selezionare l'opzione Aggiungi integrazione per API Web ASP.NET Project **vuoto.** Questa opzione aggiunge file al modello React in modo che possa essere collegato al progetto ASP.NET Core, se viene aggiunto un ASP.NET Core progetto.

   :::image type="content" source="media/vs-2022/react-additional-info.png" alt-text="Informazioni aggiuntive":::

   Si noti che la creazione del progetto React richiede un momento perché il comando create-react-app in esecuzione in questo momento esegue anche il comando npm install

## <a name="set-the-project-properties"></a>Impostare le proprietà del progetto

1. In Esplora soluzioni fare clic con il pulsante destro del mouse React progetto, scegliere **Proprietà** e quindi passare alla **sezione** Debug.

1. Modificare debugger per avviare l'opzione **launch.jsattivata.**
 
   :::image type="content" source="media/vs-2022/react-choose-debugger.png" alt-text="Scegliere il debugger (launch.jssu)":::

## <a name="build-your-project"></a>Creare il Project

Scegliere **Compila**  >  **soluzione per** compilare il progetto.

## <a name="start-your-project"></a>Avviare la Project

Premere **F5** o selezionare il **pulsante Avvia** nella parte superiore della finestra. Viene visualizzato un prompt dei comandi:

- npm che esegue il comando react-scripts start

Verrà quindi visualizzata l'app di base React app.