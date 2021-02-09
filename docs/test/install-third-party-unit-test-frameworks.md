---
title: Installare framework di unit test di terze parti
description: Esplora test di Visual Studio può eseguire test da qualsiasi framework di unit test che ha sviluppato un'interfaccia di adattatore per Esplora test.
ms.custom: SEO-VS-2020
ms.date: 07/09/2020
ms.topic: how-to
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: c59a9d9055dd6a5788eec4d4904d9ec41262dae2
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/08/2021
ms.locfileid: "99879501"
---
# <a name="install-unit-test-frameworks"></a>Installare framework di unit test

Esplora test di Visual Studio può eseguire test da qualsiasi framework di unit test che ha sviluppato un'interfaccia di adattatore per Esplora test. L'installazione del framework copia i file binari e aggiunge modelli di progetto di Visual Studio per i linguaggi supportati. Quando si crea un progetto con il modello, il framework viene registrato con Esplora test.

Una soluzione di Visual Studio può includere progetti unit test che usano diversi framework e fanno riferimento a diversi linguaggi.

::: moniker range=">=vs-2019"
Per .NET, [MSTest, NUnit e xUnit](getting-started-with-unit-testing.md) sono i Framework di test forniti da Visual Studio installati per impostazione predefinita. Per C++, viene fornito un set di Framework di test diverso, ad esempio CTest.
::: moniker-end
::: moniker range="vs-2017"
[MSTest](getting-started-with-unit-testing.md) è il framework di test offerto da Visual Studio che viene installato per impostazione predefinita.
::: moniker-end

## <a name="acquire-frameworks"></a>Acquisire framework

Installare framework di unit test di terze parti usando **Gestione pacchetti NuGet**.

1. Fare clic con il pulsante destro del mouse sul progetto che conterrà il codice di test e selezionare **Gestisci pacchetti NuGet**.

2. In **Gestione pacchetti NuGet** cercare il framework di test da installare e quindi scegliere **Installa**.

   ![Gestione pacchetti NuGet in Visual Studio](media/vs-2019/nuget-package-manager.png)

## <a name="update-to-the-latest-test-adapters"></a>Eseguire l'aggiornamento agli adattatori di test più recenti

Eseguire l'aggiornamento all'adattatore di test stabile più recente per una migliore esperienza di individuazione ed esecuzione dei test. Per altre informazioni sugli aggiornamenti per gli adattatori di test MSTest, NUnit e xUnit, vedere il [blog di Visual Studio](https://devblogs.microsoft.com/visualstudio/test-experience-improvements/).

### <a name="to-update-to-the-latest-stable-test-adapter-version"></a>Per eseguire l'aggiornamento alla versione dell'adattatore di test stabile più recente

1. Aprire Gestione pacchetti NuGet per la soluzione passando a **strumenti** gestione  >  **pacchetti NuGet**  >  **Gestisci pacchetti NuGet per la soluzione**.

2. Fare clic sulla scheda **Aggiornamenti** e cercare gli adattatori di test MSTest, NUnit o xUnit installati.

3. Selezionare ogni adattatore di test e quindi selezionare la versione stabile più recente nel menu a discesa.

4. Scegliere il pulsante **Installa**.

   ![Aggiornare un adattatore di test](media/install-adapter-upgrade.png)

## <a name="see-also"></a>Vedi anche

- [Eseguire unit test del codice](../test/unit-test-your-code.md)
