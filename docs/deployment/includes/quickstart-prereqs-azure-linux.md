---
ms.openlocfilehash: b2f9327da5e195c50bd074a468e1f9e57ece94ea
ms.sourcegitcommit: 5654b7a57a9af111a6f29239212d76086bc745c9
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/03/2021
ms.locfileid: "101749887"
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

* ASP.NET Core: seguire la [Guida introduttiva: usare Visual Studio per creare la prima app web ASP.NET Core](../../ide/quickstart-aspnet-core.md)o usare la procedura seguente:
  ::: moniker range=">=vs-2019"
  In Visual Studio 2019, scegliere **Crea un nuovo progetto** nella finestra Start. Se la finestra di avvio non è aperta, scegliere  >  **finestra di avvio** file. Digitare **app Web** nella casella di ricerca, scegliere **C#** come lingua, quindi scegliere **ASP.NET Core applicazione Web (Model-View-Controller)**, quindi scegliere **Avanti**. Nella schermata successiva denominare il progetto **MyASPApp**, quindi scegliere **Avanti**.

  Scegliere il Framework di destinazione consigliato (.NET Core 3,1) o .NET 5, quindi scegliere **Crea**.
  ::: moniker-end
  ::: moniker range="vs-2017"
  In Visual Studio 2017 scegliere **file**  >  **nuovo progetto**, selezionare **Visual C#**  >  **.NET Core**, quindi selezionare **ASP.NET Core applicazione Web**. Quando richiesto, selezionare il modello **Applicazione Web (MVC)**, assicurarsi che sia selezionata **Nessuna autenticazione**, quindi selezionare **OK**.
  ::: moniker-end

* Assicurarsi di compilare il progetto usando il comando di menu **Compila > Compila soluzione** prima di seguire i passaggi per la distribuzione.