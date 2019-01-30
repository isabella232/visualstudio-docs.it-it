---
title: Installare framework di unit test di terze parti
ms.date: 06/07/2018
ms.prod: visual-studio-dev15
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 4cf2635cf46b1fa8b395cb8a7cab8769ae6ed6d3
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/25/2019
ms.locfileid: "54960114"
---
# <a name="install-unit-test-frameworks"></a>Installare framework di unit test

Esplora test di Visual Studio può eseguire qualsiasi framework di unit test che ha sviluppato un'interfaccia di adattatore per Esplora test. Il programma di installazione del framework installa i file binari e aggiunge modelli di progetto di Visual Studio per i linguaggi supportati. Quando si crea un progetto con il modello, il framework viene registrato con Esplora test. Una soluzione di Visual Studio può includere progetti unit test che usano diversi framework e fanno riferimento a diversi linguaggi. Esplora test li esegue tutti.

[MSTest](getting-started-with-unit-testing.md) è il framework di test offerto da Visual Studio che viene installato con Visual Studio per impostazione predefinita.

## <a name="acquire-frameworks"></a>Acquisire framework

È possibile scaricare e installare framework di unit test di terze parti usando Gestione estensioni di Visual Studio o da [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs). I framework sono disponibili per il download anche da altri siti, ad esempio il sito Web specifico del framework.

### <a name="install-from-visual-studio"></a>Installare da Visual Studio

1. Scegliere **Strumenti** nel menu standard e quindi **Estensioni e aggiornamenti**.

2. Espandere **Online** > **Visual Studio Marketplace** > **Strumenti**. Scegliere **Test**.

3. Cercare il framework nell'elenco.

4. Selezionare il framework e scegliere **Download**.

Per altre informazioni, vedere [Cercare e usare le estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

### <a name="install-from-the-web"></a>Installazione dal Web

Se si conosce il framework che si vuole usare:

1. Aprire [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. Digitare il nome del framework nella casella **Trova**.

3. Scegliere il framework dall'elenco di risultati per passare alla pagina di **Visual Studio Marketplace** per lo strumento.

Per sfogliare un elenco di framework e di altri strumenti di test:

1. Aprire [Visual Studio Marketplace](https://marketplace.visualstudio.com/vs).

2. In **Filtra per categoria/raccolta** scegliere **Visualizza tutto**.

3. Nell'elenco **Categoria** con etichetta **Visualizzazione di**, espandere il nodo **Strumenti** e scegliere **Test**.

4. Scegliere un framework dall'elenco di risultati per passare alla pagina di **Visual Studio Marketplace** per lo strumento.

## <a name="update-to-the-latest-test-adapters"></a>Eseguire l'aggiornamento agli adattatori di test più recenti

Eseguire l'aggiornamento all'adattatore di test stabile più recente per una migliore esperienza di individuazione ed esecuzione dei test. Per altre informazioni sugli aggiornamenti per gli adattatori di test MSTest, NUnit e xUnit, vedere il [blog di Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2017/11/16/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Per eseguire l'aggiornamento alla versione dell'adattatore di test stabile più recente

1. Aprire Gestione pacchetti NuGet per la soluzione passando a **Strumenti** > **Gestione pacchetti NuGet** > **Gestisci pacchetti NuGet per la soluzione**.

2. Fare clic sulla scheda **Aggiornamenti** e cercare gli adattatori di test MSTest, NUnit o xUnit installati.

3. Selezionare ogni adattatore di test e quindi selezionare la versione stabile più recente nel menu a discesa.

4. Scegliere il pulsante **Installa**.

   ![Aggiornare un adattatore di test](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Vedere anche

- [Eseguire unit test del codice](../test/unit-test-your-code.md)
