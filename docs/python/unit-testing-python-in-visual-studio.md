---
title: Codice Python negli unit test
description: Configurazione di unit test per il codice Python in Visual Studio per usufruire delle funzionalità di Esplora test per l'individuazione, l'esecuzione e il debug dei test.
ms.date: 09/18/2019
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jmartens
ms.technology: vs-python
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: c35563a44bdcba5de9df820cb363def7818cb5ad
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 08/13/2021
ms.locfileid: "122156410"
---
# <a name="set-up-unit-testing-for-python-code"></a>Configurare gli unit test per il codice Python

Gli unit test sono parti di codice che testano altre unità di codice in un'applicazione, in genere funzioni isolate, classi e così via. Se un'applicazione supera tutti gli unit test, si può ritenere con una certa fiducia che almeno la funzionalità di basso livello sia corretta.

In Python gli unit test vengono usati frequentemente per convalidare gli scenari durante la progettazione di un programma. Il supporto di Python in Visual Studio include l'individuazione, l'esecuzione e il debug di unit test direttamente all'interno del contesto del processo di sviluppo, senza la necessità di eseguire i test separatamente.

Questo articolo illustra brevemente le funzionalità di testing unità in Visual Studio con Python. Per altre informazioni di carattere generale sull'esecuzione di unit test, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md).

::: moniker range="vs-2017"

[!include[Testing Python code](includes/vs-2017/unit-testing-python.md)]

::: moniker-end

::: moniker range=">= vs-2019"

[!include[Testing Python code](includes/vs-2019/unit-testing-python.md)]

::: moniker-end