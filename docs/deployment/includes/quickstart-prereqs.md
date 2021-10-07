---
ms.openlocfilehash: 4a6afc117b2457b9be9a3aeb3703695fe2e1a230
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2021
ms.locfileid: "129638226"
---
## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) installato con i carichi di lavoro appropriati per il linguaggio scelto:
  * ASP.NET: **Sviluppo ASP.NET e Web**
  * Python: **Sviluppo Python**
  * Node.js: **Sviluppo Node.js**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) installato con i carichi di lavoro appropriati per il linguaggio scelto:
  * ASP.NET: **Sviluppo ASP.NET e Web**
  * Python: **Sviluppo Python**
  * Node.js: **Sviluppo Node.js**
::: moniker-end

* Un progetto ASP.NET, ASP.NET Core, Python o Node.js. Se non è già presente un progetto, selezionare una delle opzioni seguenti:
  * ASP.NET Core: Seguire [Avvio rapido: Usare Visual Studio per](../../ide/quickstart-aspnet-core.md)creare la prima app Web ASP.NET Core oppure seguire questa procedura:
    ::: moniker range=">=vs-2019"
    In Visual Studio 2019 scegliere **Crea un nuovo progetto** nella finestra iniziale. Se la finestra iniziale non è aperta, scegliere **Finestra**  >  **iniziale file**. Digitare **app Web** nella casella di ricerca, scegliere **C#** come linguaggio, quindi scegliere applicazione Web ASP.NET Core **(Model-View-Controller)** e infine **scegliere Avanti.** Nella schermata successiva assegnare al progetto il **nome MyASPApp** e quindi scegliere **Avanti.**

    Scegliere il framework di destinazione consigliato o .NET 6 e quindi scegliere **Crea.**
    ::: moniker-end
    ::: moniker range="vs-2017"
    In Visual Studio 2017 scegliere **File** Nuovo Project , selezionare  >   **Visual C#**  >  **.NET Core,** quindi selezionare ASP.NET Core **Applicazione Web**. Quando richiesto, selezionare il modello **Applicazione Web (MVC)**, assicurarsi che sia selezionata **Nessuna autenticazione**, quindi selezionare **OK**.
    ::: moniker-end
  * Python: seguire [Guida introduttiva: creare la prima app Web Python con Visual Studio](../../ide/quickstart-python.md) oppure usare **File** > **Nuovo progetto**, selezionare **Python**, quindi selezionare **Progetto Flask Web**.
  * Node.js: seguire [Guida introduttiva: usare Visual Studio per creare la prima app Node.js](../../ide/quickstart-nodejs.md) oppure usare **File** > **Nuovo progetto**, selezionare **JavaScript**, quindi selezionare **Applicazione Web Node.js vuota**.

* Assicurarsi di compilare il progetto usando il comando di menu **Compila > Compila soluzione** prima di seguire i passaggi per la distribuzione.