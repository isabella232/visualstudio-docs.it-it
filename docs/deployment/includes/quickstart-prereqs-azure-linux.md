---
ms.openlocfilehash: d73d994d4bab7aaf7ab4c596e133c83d79b28c06
ms.sourcegitcommit: aaa3146356421d921714c29ffd586083570ade3d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/07/2021
ms.locfileid: "129638779"
---
## <a name="prerequisites"></a>Prerequisiti

::: moniker range=">=vs-2019"

* [Visual Studio 2019](https://visualstudio.microsoft.com/downloads) installato con i carichi di lavoro appropriati per il linguaggio scelto:
  * ASP.NET: **Sviluppo ASP.NET e Web**
::: moniker-end
::: moniker range="vs-2017"
* [Visual Studio 2017](https://visualstudio.microsoft.com/vs/older-downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=vs+2017+download) installato con i carichi di lavoro appropriati per il linguaggio scelto:
  * ASP.NET: **Sviluppo ASP.NET e Web**
::: moniker-end

* Una sottoscrizione di Azure. Se non si dispone già di una sottoscrizione, [iscriversi gratuitamente](https://azure.microsoft.com/free/dotnet/) per ottenere un credito di $200 per 30 giorni e 12 mesi di accesso ai servizi gratuiti più diffusi.

* ASP.NET Core: Seguire [la guida introduttiva: usare Visual Studio per creare la](../../ide/quickstart-aspnet-core.md)prima app Web ASP.NET Core oppure seguire questa procedura:
  ::: moniker range=">=vs-2019"
  In Visual Studio 2019 scegliere **Crea un nuovo progetto** nella finestra iniziale. Se la finestra iniziale non è aperta, scegliere **Finestra**  >  **iniziale file**. Digitare **app** Web nella casella di ricerca, scegliere **C#** come linguaggio, quindi scegliere ASP.NET Core **Applicazione Web (Model-View-Controller)** e quindi **scegliere Avanti.** Nella schermata successiva assegnare al progetto il nome **MyASPApp** e quindi scegliere **Avanti.**

  Scegliere il framework di destinazione consigliato o .NET 6 e quindi scegliere **Crea**.
  ::: moniker-end
  ::: moniker range="vs-2017"
  In Visual Studio 2017 scegliere **File** nuovo Project , selezionare  >   **Visual C#**  >  **.NET Core,** quindi selezionare ASP.NET Core **Applicazione Web**. Quando richiesto, selezionare il modello **Applicazione Web (MVC)**, assicurarsi che sia selezionata **Nessuna autenticazione**, quindi selezionare **OK**.
  ::: moniker-end

* Assicurarsi di compilare il progetto usando il comando di menu **Compila > Compila soluzione** prima di seguire i passaggi per la distribuzione.