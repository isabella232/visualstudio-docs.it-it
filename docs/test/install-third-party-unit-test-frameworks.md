---
title: Installare framework di unit test di terze parti
ms.date: 04/01/2019
ms.topic: conceptual
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 9f61b52f72474a8ecd8fac4c30265dcd7cf36a5e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62978667"
---
# <a name="install-unit-test-frameworks"></a>Installare framework di unit test

Esplora test di Visual Studio può eseguire test da qualsiasi framework di unit test che ha sviluppato un'interfaccia di adattatore per Esplora test. L'installazione del framework copia i file binari e aggiunge modelli di progetto di Visual Studio per i linguaggi supportati. Quando si crea un progetto con il modello, il framework viene registrato con Esplora test.

Una soluzione di Visual Studio può includere progetti unit test che usano diversi framework e fanno riferimento a diversi linguaggi.

[MSTest](getting-started-with-unit-testing.md) è il framework di test offerto da Visual Studio che viene installato per impostazione predefinita.

## <a name="acquire-frameworks"></a>Acquisire framework

Installare framework di unit test di terze parti usando **Gestione pacchetti NuGet**.

1. Fare clic con il pulsante destro del mouse sul progetto che conterrà il codice di test e selezionare **Gestisci pacchetti NuGet**.

2. In **Gestione pacchetti NuGet** cercare il framework di test da installare e quindi scegliere **Installa**.

   ![Gestione pacchetti NuGet in Visual Studio](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>Eseguire l'aggiornamento agli adattatori di test più recenti

Eseguire l'aggiornamento all'adattatore di test stabile più recente per una migliore esperienza di individuazione ed esecuzione dei test. Per altre informazioni sugli aggiornamenti per gli adattatori di test MSTest, NUnit e xUnit, vedere il [blog di Visual Studio](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Per eseguire l'aggiornamento alla versione dell'adattatore di test stabile più recente

1. Aprire Gestione pacchetti NuGet per la soluzione passando a **Strumenti** > **Gestione pacchetti NuGet** > **Gestisci pacchetti NuGet per la soluzione**.

2. Fare clic sulla scheda **Aggiornamenti** e cercare gli adattatori di test MSTest, NUnit o xUnit installati.

3. Selezionare ogni adattatore di test e quindi selezionare la versione stabile più recente nel menu a discesa.

4. Scegliere il pulsante **Installa**.

   ![Aggiornare un adattatore di test](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Vedere anche

- [Eseguire unit test del codice](../test/unit-test-your-code.md)
