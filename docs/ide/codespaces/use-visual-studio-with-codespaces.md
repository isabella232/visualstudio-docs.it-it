---
title: Visual Studio con una codespace (anteprima)
description: Informazioni sull'uso dell'IDE di Visual Studio con gli spazi dei valori di GitHub per lo sviluppo per Windows.
ms.topic: how-to
ms.date: 09/21/2020
author: gregvanl
ms.author: gregvanl
manager: jmartens
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.workload:
- multiple
monikerRange: vs-2019
ms.openlocfilehash: 95ed318c327735c85fda854d207b36874eeffca7
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99970985"
---
# <a name="how-to-use-visual-studio-with-a-codespace-preview"></a>Come usare Visual Studio con una codespace (anteprima)

Visual Studio offre un supporto eccezionale per lo sviluppo in codespaces GitHub. È possibile creare e connettersi a uno spazio dei comandi e avere tutta la potenza di Visual Studio per lavorare sui progetti in un ambiente host remoto. Anche se il codice sorgente e gli strumenti si trovano in uno spazio dei nomi e la compilazione e il debug si verificano nel cloud, l'esperienza di sviluppo si risulterà veloce e senza attrito, come se si lavorasse localmente. È possibile usare un codespace dall'interno di Visual Studio 2019 Preview ([iscriversi alla versione beta pubblica limitata](https://github.com/features/codespaces/signup-vs)).

> [!NOTE]
> Questo articolo descrive in modo specifico l'uso di Visual Studio per connettersi agli spazi di codebase di GitHub. È possibile ottenere informazioni sulla connessione a uno spazio dei tipi con altri client nella documentazione [Visual Studio Code](https://docs.github.com/github/developing-online-with-codespaces/connecting-to-your-codespace-from-visual-studio-code) o [GitHub](https://docs.github.com/github/developing-online-with-codespaces/developing-in-a-codespace) .

> [!NOTE]
> Se [Visual Studio 2019 Preview](https://aka.ms/vspreview) non è ancora installato, è possibile scaricarlo da [VisualStudio.Microsoft.com](https://aka.ms/vspreview).

## <a name="enable-connect-to-github-codespaces"></a>Abilitare la connessione a codespaces GitHub

La connessione a spazi dei caratteri di GitHub con Visual Studio 2019 Preview non è abilitata per impostazione predefinita, pertanto è necessario abilitare prima l'opzione funzionalità di anteprima.

1. In Visual Studio 2019 Preview usare la   >  voce di menu strumenti **Opzioni** per aprire la finestra di dialogo Opzioni.

2. In **Environment (ambiente**) selezionare **funzionalità di anteprima** e selezionare la funzionalità **Connect to GitHub codespaces** Preview.

   ![Controllare la funzionalità di anteprima della connessione alla codespaces di GitHub](media/connect-to-github-codespaces-preview-feature.png)

3. Per la disponibilità della funzionalità, sarà necessario riavviare Visual Studio.

## <a name="create-a-codespace"></a>Creare un codespace

Se non si dispone già di un codespace, è possibile crearne uno da Visual Studio.

1. Quando si avvia Visual Studio, nella finestra di avvio viene visualizzato un pulsante **Connetti a codespace** in "inizia".

   ![Finestra di avvio di Visual Studio con Connetti a uno spazio dei menu](media/visual-studio-start-window.png)

2. Selezionare **Connetti a un codespace** e verrà richiesto di accedere a github. Se non si dispone già di un account GitHub, è anche possibile crearne uno.

   ![Accesso a GitHub in Visual Studio](media/visual-studio-sign-in-to-github.png)

   Dopo aver selezionato **Accedi a GitHub**, seguire il flusso di lavoro di accesso a GitHub online.

3. Se non è mai stato creato un codespace, verrà richiesto di crearne uno.

   In "codespace Details" è necessario specificare un **URL del repository**. Gli spazi dei codespace di GitHub clonano il repository specificato nello spazio di codespace quando viene creato.

   È anche possibile modificare il **tipo di istanza** e **sospendere dopo** il timeout tramite i rispettivi elenchi a discesa. Dopo aver impostato i dettagli relativi allo spazio dei dati, selezionare il pulsante **Crea e Connetti** .

   ![Dettagli di Visual Studio codespace](media/visual-studio-codespace-details.png)

   Gli spazi dei codespace GitHub inizieranno a preparare lo spazio dei codespace e apriranno Visual Studio, una volta che lo spazio è pronto.

   Il nome codespace verrà visualizzato nell'indicatore remoto sulla barra dei menu.

   ![Visual Studio connesso al repository eShopOnWeb codespace](media/visual-studio-eshoponweb-codespace.png)

4. Iniziare a usare Visual Studio, come si farebbe in locale. Possibili soluzioni:

   * Esplorare il codice sorgente.
   * Selezionare un file di soluzione e compilare la soluzione (**CTRL + MAIUSC + B**).
   * Impostare un punto di interruzione in un file di origine e premere **F5** per avviare l'applicazione nel debugger.
   * Apportare modifiche ed eseguirne il commit nel repository.   

> [!NOTE]
> Attualmente, non è possibile creare spazi dei termini di GitHub per Visual Studio tramite il [portale codespaces](https://github.com/codespaces)di GitHub. È possibile crearli solo usando Visual Studio.

## <a name="connect-to-a-codespace"></a>Connettersi a un codespace

Dopo aver creato l'area di lavoro, è possibile aprire il codespace direttamente da Visual Studio.

1. Quando si avvia Visual Studio, nella finestra di avvio viene visualizzato un pulsante **Connetti a codespace** in "inizia".

   ![Finestra di avvio di Visual Studio con Connetti a uno spazio dei menu](media/visual-studio-start-window.png)

   Se si è già in Visual Studio, è possibile **usare la**  >  voce **di menu Connetti a una voce di** menu.

   ![File di Visual Studio connessione a una voce di menu codespace](media/visual-studio-file-connect-to-codespace.png)

2. Selezionare **Connetti a un codespace**. Verrà richiesto di accedere a GitHub, se non è già stato fatto.

3. Si vedranno quindi tutti gli spazi dei dati di GitHub, insieme ai relativi dettagli presentati nel pannello di destra.

   ![Visual Studio che Visualizza i dettagli e gli spazi dei dati GitHub disponibili](media/visual-studio-connect-codespace.png)

   Tutti gli spazi dei codici che clonano un repository di Azure DevOps saranno visibili solo in Visual Studio e non nella pagina codespaces di GitHub.

4. Scegliere un codespace e selezionare il pulsante **Connetti** . Se il codespace è stato sospeso, verrà riavviato e in Visual Studio verrà aperta la connessione a tale spazio.

   Il nome codespace verrà visualizzato nell'indicatore remoto sulla barra dei menu.

   ![Visual Studio connesso al repository eShopOnWeb codespace](media/visual-studio-eshoponweb-codespace.png)

5. Iniziare a usare Visual Studio, come si farebbe in locale. Possibili soluzioni:

   * Esplorare il codice sorgente.
   * Selezionare un file di soluzione e compilare la soluzione (**CTRL + MAIUSC + B**).
   * Impostare un punto di interruzione in un file di origine e premere **F5** per avviare l'applicazione nel debugger.
   * Apportare modifiche ed eseguirne il commit nel repository.

<!-- TBD ## Suspend a codespace -->

<!-- TBD ## Disconnect from a codespace -->

## <a name="see-also"></a>Vedi anche

* [Che cosa sono gli spazi di dati di GitHub?](codespaces-overview.md)
* [Come personalizzare uno spazio di codespace](customize-codespaces.md)
* [Funzionalità di Visual Studio supportate](supported-features-codespaces.md)
